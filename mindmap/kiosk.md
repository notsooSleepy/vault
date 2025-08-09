---
tags:
  - child
aliases:
---
2025-08-05 10:53
# kiosk
```bash
chromium --kiosk --start-fullscreen --incognito --noerrdialogs --disable-translate --disable-infobars --window-position=0,0 --window-size=1920,1080 --hide-scrollbars https://webdriveruniversity.com/index.html &
```
skrypt
```bash
#!/bin/bash
# Orange Pi One kiosk scrypt
# Uwaga 1 --> odpalaj w home / nie zawiera ścieżek absolutnych
# Uwaga 2 --> odpalaj na docelowym userze / nie root zaraz po instalacji system
# Uwaga 3 --> pamietaj o chmod +x tenskrypt

set -e

sudo apt update
sudo apt upgrade
sudo apt install --no-install-recommends xserver-xorg x11-xserver-utils xinit openbox chromium kitty vim xdotool
# skrypt dla bookworm na ubuntu chromium nazywa się chromium-browser

cat <<EOF > ~/.xinitrc
#!/bin/sh
xset s off        # Disable screensaver
xset -dpms        # Disable DPMS power saving
xset s noblank    # Never blank the screen

# Start Chromium in kiosk mode
chromium --kiosk --start-fullscreen --incognito --noerrdialogs --disable-translate --disable-infobars --window-position=0,0 --window-size=1920,1080 --hide-scrollbars https://webdriveruniversity.com/index.html https://demoqa.com/ https://www.ministryoftesting.com/learn

~/rotate-tabs.sh
EOF

chmod +x ~/.xinitrc

# dodaje skrypt do rotowania tabów
cat <<EOF > ~/rotate-tabs.sh
#!/bin/bash

# Wait for X server to be ready
sleep 5

while true; do
    sleep 60
    xdotool key F5
    sleep 1
    xdotool key ctrl+Tab
done
EOF

chmod +x ~/rotate-tabs.sh

# dodaje auto login na tty1
sudo mkdir -p /etc/systemd/system/getty@tty1.service.d
sudo tee /etc/systemd/system/getty@tty1.service.d/override.conf > /dev/null <<EOF
[Service]
ExecStart=
ExecStart=-/sbin/agetty --autologin $USER --noclear %I \$TERM
EOF

# autostart xserver z .bash_profile 
if ! grep -q "startx" ~/.bash_profile 2>/dev/null; then
    echo 'if [[ -z $DISPLAY ]] && [[ $(tty) == /dev/tty1 ]]; then' >> ~/.bash_profile
    echo '  startx' >> ~/.bash_profile
    echo 'fi' >> ~/.bash_profile
fi
echo "Koniec"
```
# References