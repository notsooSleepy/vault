---
tags:
  - child
aliases:
---
2025-11-23 13:30
# raspbian kiosk
* run_kiosk.sh
```bash
sleep 3
/bin/chromium-browser --kiosk --start-maximized --start-fullscreen --noerrdialogs --disable-infobars https://gblonaspmfgap06.emrsn.org/Form?id=20186/ &
```
* wayfire.ini
```bash
[autostart]
screensaver = false
dpms = false
kiosk = /home/raspberrypi/run_kiosk.sh
```
# Links
# References