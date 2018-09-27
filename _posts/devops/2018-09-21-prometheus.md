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

## Architecture

A Source of metrics that is scraped is called an **endpoint**. To scrape an endpoint a configuration called **target** is needed. A group of targets is called a **job** e.g. a cluster of apache servers.

## Data Model

### Labels

A time series is identified by its name and labels. But the name is also a label called `__name__`

There are **instrumentation labels** which are added at the source before scraping and **target labels** which are added by Prometheus during and after the scrape.

There are two types of target relabeling: `relabel_configs` happens **before** the scrape and `metric_relabel_configs` happens **after** the scrape.

### Samples

A value in a time series is called a **sample**. It consists of:

* A float64 value
* A millisecond-precision timestamp


## PromQL

CPU utilization percent

`100 - avg(irate(node_cpu_seconds_total{job="node",mode="idle"}[5m])) by (instance) * 100`

Is load 2 times greater than number of cpus ?

`node_load1 > on (instance) 2 * count by (instance) (node_cpu_seconds_total{mode="idle"})`

Memory percent used

`(node_memory_MemTotal_bytes - (node_memory_MemFree_bytes + node_memory_Cached_bytes + node_memory_Buffers_bytes)) / node_memory_MemTotal_bytes * 100`

Rate of paging in and out of memory

`1024 * sum by (instance) ( rate(node_vmstat_pgpgin[1m]) + rate(node_vmstat_pgpgout[1m]))`

Disk usage percent

`(node_filesystem_size_bytes{mountpoint="/"} - node_filesystem_free_bytes{mountpoint="/"} ) / node_filesystem_size_bytes{mountpoint="/"} * 100`

Predict linear

`predict_linear(node_filesystem_free_bytes{mountpoint="/"}[1h], 4*3600)`

Vector match

`node_systemd_unit_state{name="docker.service"} == 1 and on (instance, job) metadata{datacenter="NJ"}`
