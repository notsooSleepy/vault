---
tags:
  - baby
aliases:
---
2026-05-04 22:32
# rclone proton
Run:
```shell
rclone config
```
# Method 1 – Mount Proton Drive as a Folder
Create a local folder:
Mount the drive:
```shell
rclone mount protondrive: ~/ProtonDrive \
  --vfs-cache-mode full \
  --vfs-cache-max-age 1m \
  --dir-cache-time 30s \
  --poll-interval 15s \
  --daemon
```
You can now access Proton Drive directly in your file manager at ~/ProtonDrive.
To unmount:
```shell
fusermount -u ~/ProtonDrive
```
# Method 2 – Dropbox-Style Sync (bisync)
If you’d rather work in a local folder and keep everything synced with the cloud, rclone bisync is the way to go.
Create local folder
Initial sync
```shell
rclone bisync ~/ProtonDropbox protondrive: --resync --verbose
```
Normal sync (manual)
```shell
rclone bisync ~/ProtonDropbox protondrive: --verbose
```
Automating the Sync
You can use cron to run it every 5 minutes:
```shell
crontab -e
```
Add this line:
```shell
*/5 * * * * rclone bisync ~/ProtonDropbox protondrive: --verbose >> ~/rclone-bisync.log 2>&1
```
Or, for a more robust setup, use systemd to run it automatically in the background.

Systemd service
File ~/.config/systemd/user/proton-bisync.service:
```
[Unit]
Description=Rclone bisync ProtonDrive
After=network-online.target

[Service]
Type=oneshot
ExecStart=/usr/bin/rclone bisync /home/%u/ProtonDropbox protondrive: --verbose
Systemd timer
File ~/.config/systemd/user/proton-bisync.timer:

[Unit]
Description=Run ProtonDrive bisync every 5 minutes

[Timer]
OnBootSec=2m
OnUnitActiveSec=5m
Unit=proton-bisync.service

[Install]
WantedBy=timers.target
```
Enable:
```shell
systemctl --user daemon-reload
systemctl --user enable --now proton-bisync.timer
```
# Links
# References