---
layout: post
title:  "elasticsearch"
date:   2019-06-19 16:00:00
categories: software
---

## API

Write a Document to the Index twitter

```bash
curl -k -X POST -H 'Content-Type: application/json' -d '{"user": "kimchy"}' https://localhost:8081/twitter/_doc/
```

List Indices

```bash
curl -k -X GET -H "Accept: application/json" https://localhost:8081/_cat/indices
```

Get Index Info

```bash
curl -k -X GET -H "Accept: application/json" https://localhost:8081/twitter
```

Delete Index

```bash
curl -k -X DELETE https://localhost:8081/twitter
```
