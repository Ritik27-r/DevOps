# Docker Images

## What is a Docker Image?

A Docker image is a **read-only template** used to create containers.

It contains everything needed to run an application:

* Base OS (minimal)
* Application code
* Dependencies
* Environment configuration

---

## Image vs Container

| Image     | Container        |
| --------- | ---------------- |
| Blueprint | Running instance |
| Read-only | Read-write layer |
| Stored    | Executed         |

Example:

```text id="i1m2a3"
nginx image → nginx container
```

---

## Image Layers Concept

Docker images are built in **layers**.

Each instruction in a Dockerfile creates a new layer.

```text id="l1a2y3"
Layer 3 → Application code
Layer 2 → Dependencies
Layer 1 → Base image (Ubuntu)
```

---

## Why Layers are Important

* Faster builds (cache reuse)
* Smaller updates (only changed layers rebuilt)
* Efficient storage
* Easy rollback

---

## Pulling Images

Download image from Docker Hub:

```bash id="p1u2l3"
docker pull nginx
```

Specific version:

```bash id="p1u2v3"
docker pull nginx:1.25
```

---

## Listing Images

```bash id="l1i2s3"
docker images
```

Output includes:

* Repository
* Tag
* Image ID
* Size

---

## Image Tags

Tags define versions of images.

Example:

```text id="t1a2g3"
nginx:latest
nginx:1.25
nginx:alpine
```

---

## Running Image as Container

```bash id="r1u2n3"
docker run nginx
```

Detached mode:

```bash id="d1e2t3"
docker run -d nginx
```

---

## Building Custom Images

Docker images are built using a **Dockerfile**.

```bash id="b1u2i3"
docker build -t myapp .
```

---

## Inspecting Images

```bash id="i1n2s3"
docker inspect nginx
```

Shows:

* Layers
* Metadata
* Configuration

---

## Removing Images

```bash id="r1m2i3"
docker rmi nginx
```

Force remove:

```bash id="f1r2m3"
docker rmi -f nginx
```

---

## Dangling Images

Unused intermediate images:

```bash id="d1a2n3"
<none>:<none>
```

Remove all unused images:

```bash id="p1r2u3"
docker image prune
```

---

## Image History

Shows layer-by-layer build steps:

```bash id="h1i2s3"
docker history nginx
```

---

## Saving Images

Export image to file:

```bash id="s1a2v3"
docker save -o myimage.tar nginx
```

---

## Loading Images

Import image from file:

```bash id="l1o2a3"
docker load -i myimage.tar
```

---

## Image Registry Flow

```text id="r1e2g3"
Build → Tag → Push → Registry → Pull → Run
```

---

## Pushing Images to Docker Hub

### Step 1: Login

```bash id="l1o2g3"
docker login
```

---

### Step 2: Tag image

```bash id="t1a2g3b"
docker tag myapp user/myapp:v1
```

---

### Step 3: Push image

```bash id="p1u2s3h"
docker push user/myapp:v1
```

---

## Image Caching

Docker reuses layers if nothing changes.

Example:

* If base image unchanged → no rebuild needed
* Only modified layers are rebuilt

---

## Optimizing Image Size

Best practices:

* Use alpine images
* Remove unnecessary packages
* Combine commands in Dockerfile
* Clean cache after install

Example:

```text id="a1l2p3"
nginx:alpine (smaller than full nginx image)
```

---

## Multi-Stage Builds (Concept)

Used to reduce final image size:

* Stage 1: Build application
* Stage 2: Run application

Only final stage is shipped.

---

## Common Image Issues

* Image not found → wrong tag/name
* Pull error → network/registry issue
* Large image size → bad Dockerfile
* Cache issues → rebuild needed

---

## Image Security Tips

* Use official images
* Scan images for vulnerabilities
* Avoid latest tag in production
* Keep images minimal

---

## Common Commands Summary

```bash id="s1u2m3"
docker pull
docker images
docker rmi
docker build
docker tag
docker push
docker save
docker load
docker history
docker inspect
```

---

## Summary

Docker images are:

* Immutable templates
* Built in layers
* Stored in registries
* Used to create containers

They are the foundation of Docker-based deployments.

---

## What Next?

Next topic:

👉 **Docker-Containers.md** (runtime behavior, lifecycle, execution, and container management)

