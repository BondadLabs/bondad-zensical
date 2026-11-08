---
date:
  created: 2026-10-24
  updated: 2026-11-03
authors: [ehsan]
categories: [Kubernetes, GPU]
tags: [gpu, maintenance]
links:
  - code.md
  - admonitions.md
---

# Draining a GPU node without losing jobs

A post with two categories, an updated date and related links, which show
in the sidebar of the post page.

<!-- more -->

## Cordon first

```bash
kubectl cordon gpu-node-07
kubectl get pods -A --field-selector spec.nodeName=gpu-node-07
```

!!! warning
    `--delete-emptydir-data` deletes scratch data on the node.

## Then drain

```bash
kubectl drain gpu-node-07 --ignore-daemonsets --delete-emptydir-data
```

Uncordon once the node passes its health checks.
