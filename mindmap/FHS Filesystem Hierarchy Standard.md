---
tags:
  - topic
aliases:
---
2025-01-12 10:14
# FHS Filesystem Hierarchy Standard
## / 
## /bin
- Contains essential binary executables that are needed during the boot process or in single-user mode.
- Generally accessible to all users.
## /sbin
- Contains binary executables primarily used for system administration.
- Usually require root privileges to execute, since they involve system-level changes.
- [[fdisk]]: partitions hard disks
- [[fsck]]: checks and repairs file systems
- [[init]]: initializes the system
## [[/etc]]
- Houses configuration files for many system services and apps.
- "Control Center".
- Content of /etc can vary depending on the Linux distro and installed software.

## /home
- Your  personal space
### Worth notice
- ==Backup Regularly==: It's crucial to back up your home directory to protect your data.
- ==File Permissions==: Be mindful of file and directory permissions to ensure proper access.
- Storage Limits: Some systems may have storage limits for home directories.
- Organization: Keep your home directory organized to improve productivity.
## [[/var]]
Variable data
- Stores variable data that changes frequently.
- System Logs, Temporary Files, Mail Spools, etc.
## /usr
## /opt
## /dev
## /tmp
# References
