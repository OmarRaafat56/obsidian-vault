[[Logs]]

write script to lower brightness when battery drops bellow certain percentage

Since you're on Hyprland, the clean way to do this is:

Monitor battery %

If below threshold → reduce brightness

If above → optionally restore it

This works best with brightnessctl.

✅ 1️⃣ Install brightnessctl (if not installed)

Arch:

sudo pacman -S brightnessctl


Debian/Ubuntu:

sudo apt install brightnessctl


Make sure your user can control brightness:

sudo usermod -aG video $USER


Then log out and back in.

✅ 2️⃣ Create the Script

Create:

nano ~/.local/bin/auto-dim.sh


Paste this:

#!/usr/bin/env bash

THRESHOLD=25        # Battery percentage to trigger dimming
DIM_LEVEL=30        # Brightness percentage when low battery
NORMAL_LEVEL=80     # Brightness when battery is OK
CHECK_INTERVAL=60   # Seconds between checks

while true; do
    BATTERY=$(cat /sys/class/power_supply/BAT*/capacity)
    STATUS=$(cat /sys/class/power_supply/BAT*/status)

    # Only dim when discharging
    if [[ "$STATUS" == "Discharging" ]]; then
        if (( BATTERY <= THRESHOLD )); then
            brightnessctl set ${DIM_LEVEL}%
        else
            brightnessctl set ${NORMAL_LEVEL}%
        fi
    fi

    sleep $CHECK_INTERVAL
done


Make it executable:

chmod +x ~/.local/bin/auto-dim.sh

✅ 3️⃣ Start It With Hyprland

Add to hyprland.conf:

exec-once = ~/.local/bin/auto-dim.sh


Reload:

hyprctl reload

🔥 Smarter Version (Prevents Constant Re-setting)

If you want a cleaner version that only changes brightness once instead of every minute, use this instead:

#!/usr/bin/env bash

THRESHOLD=25
DIM_LEVEL=30
NORMAL_LEVEL=80
CHECK_INTERVAL=60

DIMMED=0

while true; do
    BATTERY=$(cat /sys/class/power_supply/BAT*/capacity)
    STATUS=$(cat /sys/class/power_supply/BAT*/status)

    if [[ "$STATUS" == "Discharging" && $BATTERY -le $THRESHOLD && $DIMMED -eq 0 ]]; then
        brightnessctl set ${DIM_LEVEL}%
        DIMMED=1
    fi

    if [[ "$STATUS" == "Charging" || $BATTERY -gt $THRESHOLD ]] && [[ $DIMMED -eq 1 ]]; then
        brightnessctl set ${NORMAL_LEVEL}%
        DIMMED=0
    fi

    sleep $CHECK_INTERVAL
done

⚡ Optional Improvements

If you want it more advanced, I can help you:

Smooth fade instead of instant jump

Send a notification when dimming

Integrate with Waybar battery module

Use systemd user service instead of while loop (cleaner)

Tell me how advanced you want it 😄

yes

Perfect — using a systemd user service is much cleaner than a background while-loop in Hyprland 👍
It starts automatically, restarts if it crashes, and doesn’t depend on Hyprland config.

We’ll do this properly.

✅ Overview

We will:

Create a smart brightness script (no infinite loop abuse)

Create a systemd user service

Enable it permanently

1️⃣ Create the Script

Create:

mkdir -p ~/.local/bin
nano ~/.local/bin/auto-dim.sh


Paste this improved version:

#!/usr/bin/env bash

THRESHOLD=25
DIM_LEVEL=30
NORMAL_LEVEL=80

BAT_PATH="/sys/class/power_supply/BAT0"

get_battery() {
    cat "$BAT_PATH/capacity"
}

get_status() {
    cat "$BAT_PATH/status"
}

CURRENT_STATE="normal"

while true; do
    BATTERY=$(get_battery)
    STATUS=$(get_status)

    if [[ "$STATUS" == "Discharging" && "$BATTERY" -le "$THRESHOLD" && "$CURRENT_STATE" != "dim" ]]; then
        brightnessctl set ${DIM_LEVEL}% >/dev/null
        notify-send "Battery Low" "Brightness reduced to ${DIM_LEVEL}%"
        CURRENT_STATE="dim"
    fi

    if [[ ("$STATUS" == "Charging" || "$BATTERY" -gt "$THRESHOLD") && "$CURRENT_STATE" != "normal" ]]; then
        brightnessctl set ${NORMAL_LEVEL}% >/dev/null
        CURRENT_STATE="normal"
    fi

    sleep 60
done


Make executable:

chmod +x ~/.local/bin/auto-dim.sh

2️⃣ Create systemd User Service

Create:

mkdir -p ~/.config/systemd/user
nano ~/.config/systemd/user/auto-dim.service


Paste:

[Unit]
Description=Auto Dim Screen on Low Battery
After=graphical-session.target

[Service]
ExecStart=%h/.local/bin/auto-dim.sh
Restart=always
RestartSec=5

[Install]
WantedBy=default.target

3️⃣ Enable It

Reload systemd user services:

systemctl --user daemon-reload


Enable it permanently:

systemctl --user enable auto-dim.service


Start it now:

systemctl --user start auto-dim.service

✅ Check Status
systemctl --user status auto-dim.service

🎯 Why This Is Better

Runs independently of Hyprland

Auto restarts if it crashes

Clean process management

Shows up in systemctl --user

🚀 Even More Advanced (Optional)

If you want it truly professional:

Instead of polling every 60s, we can make it event-driven using:

udev

acpi_listen

or upower --monitor

That way it reacts instantly to battery changes and uses zero CPU while idle.

If you want the fully optimized version, say the word.