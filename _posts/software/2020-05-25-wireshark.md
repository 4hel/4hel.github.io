---
layout: post
title:  "wireshark"
date:   2020-05-25 10:10:00
categories: software
---

# remote analysis

start tcpdump via ssh on a remote server and pipe the pcap data to wireshark running on your machine:

```bash
ssh user@server.domain "tcpdump -U -w - ‘port 80’" | wireshark -i - -k
```

wireshark can decode many binary protocols
