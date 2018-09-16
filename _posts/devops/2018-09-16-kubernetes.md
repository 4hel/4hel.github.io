---
layout: post
title:  "kubernetes"
date:   2018-09-16 10:00:00
categories: devops
---

## 4. kubectl

The `kubectl` command-line utility is used to interact with the kubernetes API

### Namespaces and (client) Contexts

```bash
kubectl config set-context my-context --namespace=mystuff
```

creates a new context

```bash
kubectl config use-context my-context
```

### API Objects

are represented as RESTful Resource like `https://my-k8s.com/api/v1/namespaces/default/pods/my-pod`

#### get

wide / json / yaml

```bash
kubectl get pods my-pod -o jsonpath --template={.status.podIP}
```

### apply / delete

are done via yaml or json file `-f obj.yaml`


