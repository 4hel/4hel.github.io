---
layout: post
title:  "prometheus"
date:   2018-09-21 16:30:00
categories: devops
---

* TOC
{:toc}


## Fundamentals

### Health of a Service

The health of a Service can be characterized in the same way as the human needs by Maslow:

![pyramid](/img/devops/prometheus/pyramid.png)

### Metrics

#### Gauges

Gauges are numbers that go up or down like CPU utilization or number of customers

#### Counters

Counters are numbers that increase over time and never decrease like number ob bytes sent by a network device or the number of logins.

#### Histograms

A Historgram is a (graphical) frequency distribution (Häufigkeitsverteilung) of a dataset. The first step is to bucket the range of values and then count observations. The result are multiple metrics: one for each bucket.


## Methodologies

### The USE Method

This is for **host-level monitoring** For every resource check

* **Utilization** percentage the resource is busy

* **Saturation** how much work is queued

* **Errors** the count of error events

### The Google Four Golden Signals

This is for **application monitoring** (From the SRE Book)

* **Latency** The time taken for a request

* **Traffic** requests or transactions per second

* **Errors** the rate that requests fail, like HTTP 500

* **Saturation** the "fullness" of the applications resources like memory or IO.
