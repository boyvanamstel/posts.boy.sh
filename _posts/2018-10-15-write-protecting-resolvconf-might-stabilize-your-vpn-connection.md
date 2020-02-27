---
title: Write protecting resolv.conf might stabilize your VPN connection
layout: post
tags:
- linux
date: '2018-10-15 15:30:00'
apps: [carbonize]
---

Setting up your headless Linux machine to connect through a VPN is straightforward. Install OpenVPN and download the configuration provided by your VPN service. That's usually all there is to it.

Making sure it stayed connected took a little more effort on my Raspberry Pi, unfortunately. It would connect quickly, but after an hour or two the connection would drop with the following error in my `syslog`:

```bash
ovpn-nl[23140]: TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
ovpn-nl[23140]: TLS Error: TLS handshake faile
```

Nothing I changed in the configuration fixed the issue.

I did remember how switching the VPN connection off and on would change the contents of `/etc/resolv.conf`. It would apply the name servers belonging to either my router or my VPN service. Instead of replacing the ones already there, it would just add them to the list. This is incorrect and seems to be the source of the problem I experienced.

After setting my prefered name servers and then write-protecting `/etc/resolv.conf` my connection has been stable. The command to prevent changes being made to `resolv.conf` is this:

`$ sudo chattr +i /etc/resolv.conf`
