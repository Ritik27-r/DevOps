# Docker Architecture

## What is Docker Architecture?

Docker architecture explains how Docker components work together to build, run, and manage containers.

It follows a **client-server model**.

---

## High-Level Overview

```text id="a1r2c3h"
Docker Client  →  Docker Daemon  →  Containers
                      ↓
                Docker Images
                      ↓
               Docker Registry
```

---

## Core Components

### 1. Docker Client

The Docker Client is the command-line interface (`docker` command) used by users.

Examples:

```bash id="c1l2i3"
docker run nginx
docker build .
docker ps
```

It sends requests to the Docker Daemon using REST API.

---

### 2. Docker Daemon (dockerd)

The Docker Daemon is the **background service** that does the actual work.

Responsibilities:

* Builds images
* Runs containers
* Manages networks
* Handles volumes
* Communicates with registry

It runs on the host machine.

---

### 3. Docker Host

The machine where Docker is installed.

It contains:

* Docker daemon
* Images
* Containers
* Networks

---

### 4. Docker Images

Images are **read-only templates** used to create containers.

Example:

```text id="i1m2g3"
nginx image → used to create nginx container
```

---

### 5. Docker Containers

Containers are **running instances of images**.

Example:

```text id="c1o2n3"
nginx image → nginx container (running web server)
```

Containers are:

* Lightweight
* Isolated
* Temporary (can be stopped or removed)

---

### 6. Docker Registry

A registry stores Docker images.

Most common:

* Docker Hub (default public registry)

Other examples:

* Amazon ECR
* Google Container Registry
* Private registries

---

## How Docker Works Internally

### Step-by-step flow:

### Step 1: User runs command

```bash id="s1t2e3"
docker run nginx
```

---

### Step 2: Docker Client sends request

Client sends API request to Docker Daemon.

---

### Step 3: Daemon checks image

If image is not available locally:

* It contacts Docker Registry

---

### Step 4: Image is pulled

```text id="p1u2l3"
Docker Hub → Image downloaded
```

---

### Step 5: Container is created

Docker creates:

* File system
* Network interface
* Process isolation

---

### Step 6: Container starts

Application runs inside isolated environment.

---

## Docker Architecture Diagram (Simplified)

```text id="d1i2a3"
User
  ↓
Docker CLI
  ↓
Docker Daemon (dockerd)
  ↓
-------------------------
| Images | Containers   |
| Networks | Volumes    |
-------------------------
  ↓
Docker Registry (Hub)
```

---

## Docker Engine

Docker Engine is the core system that includes:

* Docker daemon
* REST API
* CLI

It is responsible for running Docker.

---

## Container Runtime

Docker uses container runtimes to run containers.

Common runtime:

* containerd
* runc

---

## Namespaces (Isolation)

Docker uses Linux namespaces for isolation:

| Namespace | Purpose                     |
| --------- | --------------------------- |
| PID       | Process isolation           |
| NET       | Network isolation           |
| MNT       | Filesystem isolation        |
| UTS       | Hostname isolation          |
| IPC       | Inter-process communication |

---

## Control Groups (cgroups)

cgroups manage resource usage:

* CPU limits
* Memory limits
* Disk I/O limits

Example:

```text id="c1g2r3"
Container cannot use more than 512MB RAM
```

---

## Docker Networking Layer

Docker creates virtual networks for containers:

* Bridge network (default)
* Host network
* Overlay network

---

## Storage Layer

Docker uses layered filesystem:

* Each image layer is read-only
* Containers add writable layer on top

This makes Docker efficient.

---

## Image Layers Concept

```text id="l1a2y3"
Layer 3 → App changes
Layer 2 → Dependencies
Layer 1 → Base OS
```

---

## Docker Lifecycle

```text id="l1i2f3"
Image → Container → Running → Stopped → Removed
```

---

## Docker vs Traditional Systems

| Feature     | Traditional Server | Docker     |
| ----------- | ------------------ | ---------- |
| Setup       | Manual             | Automated  |
| Environment | Inconsistent       | Consistent |
| Scaling     | Hard               | Easy       |
| Deployment  | Slow               | Fast       |

---

## Common Architecture Problems

* Image not found → registry issue
* Container crash → runtime issue
* Port conflict → networking issue
* Permission denied → daemon issue

---

## Best Practices

* Use official images
* Avoid large base images
* Keep containers stateless
* Limit container resources
* Use private registries for production

---

## Summary

Docker architecture is built on:

* Client (you)
* Daemon (engine)
* Images (blueprints)
* Containers (running apps)
* Registry (storage)

All working together to make deployment fast and consistent.

---

## What Next?

Next topic:

👉 **Docker-Images.md** (deep dive into image layers, tagging, and building images)

