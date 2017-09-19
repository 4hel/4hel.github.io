---
layout: post
title:  "Queue Size and Slow Query Log"
date:   2017-09-19 22:00:00
categories: wisdom
---

Watch the size of your **message queue**!

Additionally watch the **slow query log**!

In order to make sure that updates are processed very fast, make sure that long running select only go a slave, so that the slow query log on the master for critical queries is always clean.




