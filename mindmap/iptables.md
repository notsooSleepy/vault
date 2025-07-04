---
tags:
  - baby
aliases:
---
2025-05-03 15:58
# iptables
- View current rules:
```bash
sudo iptables -L -v -n
```
- Flush all rules:
```bash
sudo iptables -F
```
- Set default policies:
```bash
sudo iptables -P INPUT DROP
sudo iptables -P FORWARD DROP
sudo iptables -p OUTPUT ACCEPT
```
- Allow "established/related" connections
```bash
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

# References