[[Aircrack-ng]]
#cybercrime #cybersecurity #hacking #aircrack-ng #recovery #WiFi 

What happened

When you used aircrack‑ng tools (usually airmon-ng), the tool:

1. Put your Wi‑Fi card into monitor mode

Monitor mode lets the adapter capture raw wireless packets.

In this mode, the card cannot connect to networks or be managed by NetworkManager.

Result: nmtui shows no Wi‑Fi networks.



2. Stopped NetworkManager temporarily

airmon-ng start wlan0 often runs:

airmon-ng check kill

This kills NetworkManager and wpa_supplicant, so normal Wi‑Fi control disappears.




So nothing was broken—your system was just left in penetration‑testing state instead of normal networking state.


---

Proper way to return to normal Wi‑Fi

After finishing with aircrack‑ng, always run:

sudo airmon-ng stop wlan0mon
sudo systemctl restart NetworkManager

That:

Disables monitor mode

Restores managed mode

Restarts normal Wi‑Fi services



---

If things still look broken

Run this recovery sequence:

sudo ip link set wlan0 down
sudo iw dev wlan0 set type managed
sudo ip link set wlan0 up
sudo systemctl restart NetworkManager

This fully resets the adapter.


---

Best practice for next time

Workflow when using aircrack‑ng:

1. Start monitor mode:

sudo airmon-ng start wlan0


2. Do capture/testing.


3. Always clean up:

sudo airmon-ng stop wlan0mon
sudo systemctl restart NetworkManager



If you skip step 3, Wi‑Fi appears “missing”.


---

If you want, a short one‑command reset script can be provided to fix this instantly in the future.