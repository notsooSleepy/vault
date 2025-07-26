---
tags: 
aliases:
---
2025-07-10 18:34
# windows image
install opengl from windows store
``` yaml
services:
  windows:
    image: dockurr/windows
    container_name: windows
    environment:
      VERSION: "10"
    devices:
      - /dev/kvm
      - /dev/net/tun
    cap_add:
      - NET_ADMIN
    ports:
      - 8006:8006
      - 3389:3389/tcp
      - 3389:3389/udp
    volumes:
      - ./windows:/storage
    restart: always
    stop_grace_period: 2m
```

*when connecting through RDP use only localhost* without port number
# References
https://github.com/dockur/windows