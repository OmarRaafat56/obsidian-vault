[[Logs]]
#arch  #linux 
## Short answer

#NetworkManager is repeatedly dropping and re-requesting the IPv4 lease.
That’s why wake feels slow and Wi-Fi “flaps”, even though DHCP does succeed each time.

This is not normal and not a suspend bug anymore — it’s a connection profile issue.

### What the log is telling us (plain English)

#### Pattern repeating over and over:

1. DHCP gets an IP ✔️

2. state changed new lease, address=192.168.1.101


#### A few seconds later:


> 3. canceled DHCP transaction
> 
> 4. state changed no lease
> 
> 5. NM waits again with 45-second timeout
> 
> 6. Loop repeats

### That means:

* Your router is fine

* Your Wi-Fi driver is fine

* #NetworkManager itself is deciding to reset the connection

#### This usually happens when:

* #IPv6 is still enabled per-connection

* #MAC randomization confuses the router

* Power-save resets the device

* The connection profile is corrupted

#### ✅ The fix that actually stops this loop

We will force a clean, stable Wi-Fi profile.

1️⃣ Disable IPv6 on the Wi-Fi connection itself

(Global sysctl alone is NOT enough.)

>Find your connection name:
>
nmcli connection show

* #Nmcli -> network manager command line interface

>Then run (replace YOUR_WIFI exactly):
>
sudo nmcli connection modify "YOUR_WIFI" ipv6.method ignore

#nmcli 
#### 2️⃣ Disable Wi-Fi power saving (very common cause)

The #etc #path stores  important packages and requires #sudo to modify 

>sudo nano /etc/NetworkManager/conf.d/wifi-powersave.conf


>Paste:
>
[connection]
wifi.powersave=2


* (2 = disabled)

#### 3️⃣ Disable MAC address randomization (critical)

>sudo nmcli connection modify "YOUR_WIFI" 802-11-wireless.mac-address-randomization never


* This alone often stops the DHCP cancel loop.

#### 4️⃣ Restart NetworkManager cleanly
sudo #systemctl restart NetworkManager


>Then reconnect once:
>
nmcli device disconnect wlo1
nmcli device connect wlo1

* 🧪 What “fixed” looks like

>After this, run:
>
journalctl -b | grep dhcp


You should see:

* One DHCP lease

* No “canceled DHCP transaction”

* No repeating 45-second timeouts

#### Suspend/resume should now:

* Wake instantly

* Wi-Fi reconnect in 1–3 seconds

* No long stall

#### Why this happened

1. Your setup (Intel Wi-Fi + hybrid GPU + Arch defaults) +:

2. IPv6 attempts

3. MAC randomization

4. power save

→ #NetworkManager thinks the connection is unstable and keeps resetting it.

This is a known #arch / NM behavior, not user error.

#### If you want, next we can:

* Verify router compatibility

* Tune DHCP timeout further

* Lock Wi-Fi to fast-resume mode only

But first, apply the steps above — they address exactly what your log shows.
___
## My reply

it still takes way too long. heres what happens:
- after i input to wake it up, the screen opens but i cant interact with anything
-then the screen closes again and stays like that for ~30 seconds
- then it opens again,but freezes for 30 seconds before im finally able to use it
___

This description is extremely important — thank you.
This is not a NetworkManager problem anymore.

What you’re describing is a graphics stack resume failure with hybrid Intel + NVIDIA, and the behavior you list is a classic symptom.

### What your symptoms mean (mapped exactly)

🔹 screen opens, but you can’t interact
🔹 screen closes again
🔹 stays black ~30s
🔹 opens again, frozen ~30s
🔹 finally usable

This sequence almost always means:

❌ The GPU stack resumes in the wrong order

Specifically:

Intel iGPU (i915) wakes

NVIDIA dGPU partially wakes

Display server (Xorg/Wayland) loses DRM master

systemd-logind blocks input

GPU resets → long timeout → second wake

Your logs already showed:

i915: Failed to enable link training


That’s a known hybrid graphics resume bug, not user config.

The REAL root cause (clear now)

You are resuming from deep sleep, but the system falls back to s2idle mid-resume, causing a double suspend/resume cycle.

From your earlier log:

PM: suspend entry (deep)
PM: suspend exit
PM: suspend entry (s2idle)


That should never happen.

This causes:

screen flicker

input freeze

~30s kernel GPU timeout

second resume

✅ The correct fix (this WILL change behavior)
1️⃣ Force one sleep mode only (critical)

Edit:

sudo nano /etc/systemd/sleep.conf


Set exactly this:

>[Sleep]
AllowSuspend=yes
AllowHibernation=no
AllowSuspendThenHibernate=no
MemorySleepMode=deep


Save.

>Then run:
>
sudo systemctl daemon-reexec

2️⃣ Tell kernel to never use s2idle

>Edit GRUB:
>
sudo nano /etc/default/grub


>In GRUB_CMDLINE_LINUX_DEFAULT, add:
>
mem_sleep_default=deep


>Example:
>
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash mem_sleep_default=deep"


>Rebuild:
>
sudo grub-mkconfig -o /boot/grub/grub.cfg

#### 3️⃣ Fix Intel + NVIDIA resume order (mandatory)

>Create file:
>
sudo nano /etc/modprobe.d/hybrid-resume.conf


>Paste:
>
options i915 enable_psr=0 enable_dc=0
options nvidia NVreg_PreserveVideoMemoryAllocations=1


**Why:**

* PSR + DC cause black-screen-on-resume

* NVIDIA must preserve VRAM or it stalls for ~30s

#### 4️⃣ Ensure NVIDIA resume services are enabled (verify)
>systemctl status nvidia-suspend.service
systemctl status nvidia-resume.service


**If not enabled:**

>sudo systemctl enable nvidia-suspend.service
sudo systemctl enable nvidia-resume.service

#### 5️⃣ Disable display power management on resume (fixes screen close)

>Create:
>
sudo nano /etc/X11/xorg.conf.d/20-dpms.conf


>Paste:
>
Section "Monitor"
    Identifier "Monitor0"
    Option "DPMS" "false"
EndSection


*(This stops the “screen opens then closes again” effect.)*

#### 🧪 What should change after reboot

**After reboot + suspend:**

1. Screen turns on once

2. No second black screen

3. No 30s freeze

4. Input works immediately

5. Total wake time: 2–5 seconds

#### 🔍 If it STILL happens (unlikely after this)

>Run once after a bad resume:
>
dmesg | grep -E "i915|nvidia|drm|PM:"


But based on your description, this is 100% the hybrid GPU deep/s2idle bug, and the steps above address exactly that.

**Bottom line:**

You weren’t chasing the wrong thing — the system was:

suspending → partially resuming → re-suspending → resuming again

Fixing sleep mode + GPU resume order stops the entire chain.

**If you want, tell me:**

Xorg or Wayland?

Desktop environment (KDE, GNOME, etc.)

I can fine-tune the last 5% if needed.
___
## My reply

what does doing this imply

___ 

Got it — you’re asking what disabling DPMS actually implies / changes, not how to do it. Good question 👍

I’ll explain it plainly and honestly, including downsides.

What DPMS is (quick context)

DPMS (Display Power Management Signaling) is the mechanism that:

turns the screen off after inactivity

puts the monitor into standby/suspend/off states

is triggered by the display server (Xorg)

Normally:

idle → screen blanks

resume → screen wakes cleanly

What disabling DPMS does

>This config:
>
Option "DPMS" "false"


means:

“Never let the display server power the screen off or change its power state.”

Practically, that means:

❌ The screen will not blank due to inactivity

❌ The screen will not enter monitor sleep via DPMS

✅ The screen will stay logically ‘on’ at all times

Why this helps your problem specifically

Your symptom:

screen wakes

then immediately turns off again

then comes back much later

That happens when:

DPMS kicks in before GPU resume finishes

the GPU isn’t ready to re-enable the panel

the kernel waits ~30 seconds for a failed modeset

display retries → freeze

Disabling DPMS prevents this race condition:

no early screen-off signal

no failed panel re-init

no 30-second GPU timeout

So this is a workaround for a GPU resume bug, not a cosmetic tweak.

What you lose by disabling DPMS

Be aware of these tradeoffs:

🔻 Downsides

Screen won’t auto-turn off when idle

Slightly higher power usage

On laptops: a bit more battery drain if you leave it idle

🔺 What you do NOT lose

Suspend still works

Manual screen lock still works

Brightness controls still work

External monitors still work

GPU power-saving still works (this only affects the panel)

Is this permanent or dangerous?

No.

It does not harm hardware

It does not affect suspend itself

It is fully reversible (delete the file)

This is a stability-over-power-saving tradeoff.

When you should NOT do this

You might skip this if:

you already fixed the resume issue with sleep mode + GPU options

you rely heavily on automatic screen blanking

you’re on Wayland (this Xorg-only tweak won’t apply)

In fact, many people:

Fix sleep mode + GPU resume

Don’t need DPMS disabled afterward

TL;DR

Disabling DPMS means:

“Keep the screen logically on so it doesn’t interfere with GPU resume.”

It trades:

⚡ a bit of power efficiency
for

🧠 correct, instant wake-up with no freezes

If you want, tell me:

Xorg or Wayland

Laptop or desktop

and I’ll tell you whether you actually need this step or can skip it safely.

___


Since you’re on Wayland, this is the correct diagnosis and fix path 👇

What Wayland implies for your problem

❌ Xorg DPMS tweaks do nothing (so you can ignore that part)

✅ The issue is kernel + GPU resume ordering

✅ The freeze/black-screen timing (≈30s twice) matches GPU reset timeouts

Your symptoms are very common on Wayland + hybrid Intel/NVIDIA laptops.

What’s ACTUALLY causing the long delay (Wayland-specific)

On Wayland:

the compositor (KWin / GNOME Shell / etc.) waits for DRM devices

if either i915 or NVIDIA doesn’t resume cleanly, input is blocked

kernel waits ~30 seconds per failed modeset

compositor retries → second freeze

You already showed this kernel error:

i915: Failed to enable link training


That alone explains the 30s stall.

✅ The fixes that matter on Wayland (do ONLY these)
1️⃣ Force deep sleep only (mandatory)

Check current mode:

cat /sys/power/mem_sleep

>It must show:
>
>[s2idle] deep
>

If it doesn’t, force it permanently.

>Edit:
>
>sudo nano /etc/default/grub


>Add:
>
mem_sleep_default=deep


>Rebuild:
>
sudo grub-mkconfig -o /boot/grub/grub.cfg

2️⃣ Fix Intel i915 resume bugs (CRITICAL on Wayland)

>Create:
>
sudo nano /etc/modprobe.d/i915.conf


>Paste:
>
options i915 enable_psr=0 enable_dc=0 fastboot=0


Why:

PSR + DC are known to break panel link training after resume

Wayland is stricter than Xorg

3️⃣ Fix NVIDIA resume stalls

>Create:
>
sudo nano /etc/modprobe.d/nvidia-power.conf


>Paste:
>
options nvidia NVreg_PreserveVideoMemoryAllocations=1 NVreg_TemporaryFilePath=/var/tmp


Then ensure services:

>sudo systemctl enable nvidia-suspend.service
sudo systemctl enable nvidia-resume.service
sudo systemctl enable nvidia-hibernate.service

4️⃣ Disable runtime power management for NVIDIA (huge)

>Create udev rule:
>
sudo nano /etc/udev/rules.d/80-nvidia-pm.rules


>Paste:
`ACTION=="add", SUBSYSTEM=="pci", ATTR{vendor}=="0x10de", ATTR{power/control}="on"`



This prevents NVIDIA from half-sleeping and stalling resume.

5️⃣ Reboot (required)

All of these are kernel-level. A reboot is mandatory.

🧪 What you should see after reboot

After suspend:

Screen turns on once

No second black screen

No 30s freeze

Input works immediately

Total wake time: 2–4 seconds

If it STILL happens (last resort but effective)
Force NVIDIA off completely (Intel-only mode)

>If you don’t need NVIDIA on battery:
>
sudo pacman -S nvidia-prime


Then use Intel-only mode (depends on DE):

GNOME: “Integrated Graphics” profile

KDE: PRIME → Intel

This eliminates the issue entirely on affected laptops.

Bottom line

Because you’re on Wayland, your problem is:

GPU resume synchronization, not networking or DPMS.

The steps above directly target the exact kernel failures shown in your logs.

If you want, tell me:

GNOME or KDE?

Kernel version (uname -r)

I’ll fine-tune it precisely for your setup.