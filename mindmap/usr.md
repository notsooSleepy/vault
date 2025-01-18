---
tags:
  - baby
aliases:
---
2025-01-18 07:26
# usr
## Key directories
- /usr/bin: Contains commonly used binaries accessible to all users.
- /usr/sbin: Contains system administration binaries, usually requiring root privileges.
- /usr/lib: Stores shared libraries used by programs.
- /usr/local: Used for locally installed software, often outside of the package manager.
- /usr/share: Contains shared data files, such as documentation,. icons, and configuration files.
- /usr/src: Contains source code for various system utilities.
## Why is it important
- Program Execution: The binaries in /usr/bin and /usr/sbin are essential for running programs.
- Library Sharing: Shared libraries in /usr/lib are used by multiple programs to reduce disk space and improve performance.
- Software Installation: Many software packages install their files in various sub-directories of /usr.
- System Documentation: The /usr/ share/doc directory often contains documentation for system utilities and installed software.

## Key points:
- **Read-Only**: In many Linux distributions, the /usr directory is mounted as read-only to prevent accidental modifications.
- Package Management: Package managers like APT and RPM manage the installation and removal of software packages, often modifying files withing.
- User Access: While some file in /usr are accessible to all user, others may require root privileges to modify . 
# References