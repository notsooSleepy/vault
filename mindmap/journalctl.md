---
tags:
  - baby
  - command
aliases:
---
2025-04-29 20:23
# journalctl
```bash
journalctl -b
journalctl -p 4..4
journalctl -p "warn".."crit"

```
### 🔢 `journalctl` Priority Levels

| Value | Level     | Description                   |
| ----- | --------- | ----------------------------- |
| 0     | `emerg`   | System is unusable            |
| 1     | `alert`   | Immediate action required     |
| 2     | `crit`    | Critical conditions           |
| 3     | `err`     | Error conditions              |
| 4     | `warning` | Warning conditions            |
| 5     | `notice`  | Normal but significant events |
| 6     | `info`    | Informational messages        |
| 7     | `debug`   | Debug-level messages          |
# References