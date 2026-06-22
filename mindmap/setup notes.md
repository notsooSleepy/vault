---
tags:
  - topic
aliases:
---
2026-06-22 19:18
# setup notes
Day 1
# OPNsense
## Kea dhcp setup
### DHCPv4
LAN + lifetime 86400
HA (high availablity) disabled works with second server
#### Subnets
![[Pasted image 20260622192306.png]]
#### Reservations
I reserved wifi access point on 192.168.1.2
## Unbound DNS
![[Pasted image 20260622192731.png]]
### Blocklists
## Static hostnames
## Block DNS
Next I’d lock in the DNS blocking so clients can’t bypass it by using Google/Cloudflare DNS directly. This is still a LAN-side change and easy to undo.
Great — next step: **force LAN devices to use OPNsense DNS**, so your blocklists actually apply.

Right now, a device could ignore OPNsense and use:

```
8.8.8.8
1.1.1.1
9.9.9.9
```

OPNsense docs recommend blocking outbound DNS on port `53` when you want a validated DNS environment; they also mention NAT redirect as an option, but we’ll start with the simpler block method.

## Step 1 — Create a DNS allow rule

Go to:

```
Firewall → Rules → LAN
```

Add a new rule near the **top**:

```
Action: Pass
Interface: LAN
Protocol: TCP/UDP
Source: LAN net
Destination: This Firewall
Destination port: 53 
DNSDescription: Allow LAN DNS to OPNsense
```

Save.

## Step 2 — Block external DNS

Add another rule **directly below** the first one:

```
Action: Block
Interface: LAN
Protocol: TCP/UDP
Source: LAN net
Destination: any
Destination port: 53 
DNSDescription: Block LAN external DNS
```

Save.

## Step 3 — Rule order should look like this

Your LAN rules should be ordered like this:

```
1. Allow LAN DNS to OPNsense2. 
   Block LAN external DNS3. Allow LAN to any
```

Order matters because OPNsense firewall rules are normally **first match wins**. So the allow-to-OPNsense DNS rule must be above the block rule.

## Step 4 — Apply changes

Click:

```
Apply changes
```

Then test from a laptop/phone.

## Step 5 — Test normal DNS

From a computer, try browsing:

```
opnsense.org
google.com
youtube.com
```

Then test DNS manually.

### Windows

```
nslookup google.com 192.168.1.1nslookup google.com 8.8.8.8
```

### macOS/Linux

```
dig google.com @192.168.1.1
dig google.com @8.8.8.8
```

Expected result:

```
DNS through 192.168.1.1 worksDNS directly to 8.8.8.8 fails or times out
```

That means clients are forced to use OPNsense DNS.

## Important note

This blocks normal DNS on port `53`. It does **not** fully block encrypted DNS like:

```
DNS over HTTPS: TCP 443
DNS over TLS:   TCP 853
```

We can handle that later. For now, this is the right next safe step.
# Links
# References