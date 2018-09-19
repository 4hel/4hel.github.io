---
layout: post
title:  "kubernetes"
date:   2018-09-16 10:00:00
categories: devops
---

* TOC
{:toc}


## 4. kubectl

The `kubectl` command-line utility is used to interact with the kubernetes API

### Namespaces and (client) Contexts

`kubectl config set-context my-context --namespace=mystuff`

creates a new context

`kubectl config use-context my-context`

### API Objects

are a RESTful Resource like `https://my-k8s.com/api/v1/namespaces/default/pods/my-pod`

#### get

wide / json / yaml

`kubectl get pods my-pod -o jsonpath --template={.status.podIP}`


#### describe

`kubectl describe pods kuard`

#### apply / delete

are done via yaml or json file `-f obj.yaml`

### Debugging

logging

`kubectl logs <pod-name>` optionally following `-f`

execution

`kubectl exec kuard date`

`kubectl exec -it kuard ash`

copy

`kubectl cp <pod-name>:/path/to/remote/file /path/to/local/file`

port forwarding

`kubectl port-forward kuard 8080:8080`

### Help

`kubectl help`

or 

`kubectl help <command-name>`

## 5. Services

Create a Deployment:

`kubectl run alpaca-prod --image=gcr.io/kuar-demo/kuard-amd64:1 --replicas=3 --port=8080 --labels="ver=1,app=alpaca,env=prod"`

Create a Service with ClusterIP from the deployment:

`kubectl expose deployment alpaca-prod` optionally `--type=` **NodePort** or **LoadBalancer**

This ClusterIP can be resolved via **DNS** :

```
;; opcode: QUERY, status: NOERROR, id: 30123
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;alpaca-prod.default.svc.cluster.local.	IN	 A

;; ANSWER SECTION:
alpaca-prod.default.svc.cluster.local.	30	IN	A	10.100.196.205
```

## 11. ConfigMaps and Secrets

ConfigMap

`kubectl create configmap my-config --from-file=my-config.txt --from-literal=extra-param=extra-value --from-literal=another-param=another-value`

Secret

`kubectl create secret generic kuard-tls --from-file=kuard.crt --from-file=kuard.key`

Also useful **imagePullSecrets**

Also useful **--dry-run -o yaml**

`kubectl create secret generic kuard-tls --from-file=kuard.crt --from-file=kuard.key --dry-run -o yaml  | kubectl replace -f -`

## 12. Deployments

create:

`kubectl run nginx --image=nginx:1.7.12`i

Relationship to the ReplicaSet is defined by label

`kubectl get replicasets --selector=run=nginx`

Exporting the yaml

`kubectl get deployment nginx --export  -o yaml > nginx-deployment.yaml`

### Updating a Container Image

Updating Image

```
      containers:
      - image: nginx:1.9.10
        imagePullPolicy: IfNotPresent
```

Putting an Annotation for Change Cause

```
  template:
    metadata:
      annotations:
        kubernetes.io/change-cause: "Update nginx to 1.9.10"
```

`kubectl rollout status deployment nginx`

`kubectl rollout history deployment nginx`

`kubectl rollout pause deployment nginx`

`kubectl rollout resume deployment nginx`

### Undo Rollout

`kubectl rollout undo deployment nginx --to-revision=3`


## 13. Integrating Storage

### Services without Selectors

A Service can have the type **ExternalName**.

```yaml
kind: Service
apiVersion: v1
metadata:
  name: external-database
spec:
  type: ExternalName
  externalName: database.company.com
```

Or one can configure **Endpoints** manually for an IP Address.

```yaml
kind: Service
apiVersion: v1
metadata:
  name: external-ip-database
```

```yaml
kind: Endpoints
apiVersion: v1
metadata:
  name: external-ip-database
subsets:
  - addresses:
    - ip: 192.168.0.1
    ports:
    - port: 3306
```
