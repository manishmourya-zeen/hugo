---
title: "Kubernetes Deployment Strategies"
date: 2026-04-25
draft: false
tags: ["kubernetes", "devops", "deployment", "docker"]
author: "Your Name"
description: "Exploring different Kubernetes deployment strategies and their use cases."
---

## Overview

Kubernetes provides multiple deployment strategies to update applications with zero downtime and risk mitigation. This guide covers the most common approaches.

## 1. Rolling Update (Default)

Gradually replaces old pods with new ones.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
spec:
  replicas: 4
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 1
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: myapp
        image: myapp:v2
```

**Pros:** No downtime, gradual rollout  
**Cons:** Takes longer, version mixing during update

## 2. Blue-Green Deployment

Run two identical production environments (blue and green).

```bash
# Deploy green (new version)
kubectl apply -f green-deployment.yaml

# After testing, switch traffic
kubectl patch service myapp -p '{"spec":{"selector":{"version":"green"}}}'

# Keep blue running for quick rollback
```

**Pros:** Instant rollback, full testing in production environment  
**Cons:** Requires double resources

## 3. Canary Release

Gradually shift traffic to new version.

```yaml
apiVersion: networking.istio.io/v1alpha3
kind: VirtualService
metadata:
  name: myapp
spec:
  hosts:
  - myapp
  http:
  - match:
    - headers:
        user-agent:
          regex: ".*Canary.*"
    route:
    - destination:
        host: myapp
        subset: v2
  - route:
    - destination:
        host: myapp
        subset: v1
      weight: 95
    - destination:
        host: myapp
        subset: v2
      weight: 5
```

**Pros:** Low risk, early issue detection  
**Cons:** Complex monitoring needed

## 4. Recreate Strategy

Stop old version, start new version.

```yaml
strategy:
  type: Recreate
```

**Pros:** Simple  
**Cons:** Downtime, not recommended for production

## Monitoring Deployments

```bash
# Watch deployment progress
kubectl rollout status deployment/myapp

# View rollout history
kubectl rollout history deployment/myapp

# Rollback to previous version
kubectl rollout undo deployment/myapp

# Rollback to specific revision
kubectl rollout undo deployment/myapp --to-revision=2
```

## Summary

Choose your deployment strategy based on your requirements and risk tolerance.
