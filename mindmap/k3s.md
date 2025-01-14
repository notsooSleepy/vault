---
tags:
  - baby
aliases:
---
2025-01-12 11:17
# k3s
https://k3s.io/
https://docs.k3s.io/
```bash
sudo k3s server &
# Kubeconfig is written to /etc/rancher/k3s/k3s.yaml
sudo k3s kubectl get node

# On a different node run the below command. 
# NODE_TOKEN comes from /var/lib/rancher/k3s/server/node-token on your server
sudo k3s agent --server https://myserver:6443 --token ${NODE_TOKEN}
```
# References