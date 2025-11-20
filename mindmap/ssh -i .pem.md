---
tags:
  - command
aliases:
---


2025-04-28 19:37
# ssh -i .pem
-i switch is for adding identity file which has .pem extension 
```bash
ssh -i privateKey.pem user@ip
```

*remember about adding chmod 600 to that file to permit only you to read and edit it or else ssh will ignore it*

```bash
chmod 600 ~./ssh/id_rsa
```

# References
