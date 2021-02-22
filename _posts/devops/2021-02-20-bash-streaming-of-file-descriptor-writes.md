---
layout: post
title:  "bash streaming of file descriptor writes"
date:   2021-02-20 18:00:00
categories: devops
---

intercept stdout/stderr of another process ($PID):

```shell
sudo strace -ff -e write=1,2 -s 1024 -p $PID 2>&1  | grep "^ |" | cut -c11-60 | sed -e 's/ //g' | xxd -r -p
```