# Dockerfile Basics

## What is a Dockerfile?

A Dockerfile is a **text file containing instructions to build a Docker image**.

It automates image creation instead of manually configuring containers.

---

## Why Dockerfile is Important

* Reproducible builds
* Version-controlled infrastructure
* Automation for CI/CD
* Consistent environments
* Easy deployment

---

## Dockerfile Workflow

```text id="w1o2r3"
Dockerfile → docker build → Image → Container
```

---

## Basic Structure of Dockerfile

Example:

```dockerfile id="d1o2c3"
FROM ubuntu:latest

RUN apt update && apt install -y python3

COPY app.py /app/app.py

WORKDIR /app

CMD ["python3", "app.py"]
```

---

## Key Dockerfile Instructions

### 1. FROM

Defines base image.

```dockerfile id="f1r2o3m"
FROM ubuntu:latest
```

---

### 2. RUN

Executes commands during image build.

```dockerfile id="r1u2n3"
RUN apt update
```

---

### 3. COPY

Copies files from host to image.

```dockerfile id="c1o2p3"
COPY app.py /app/
```

---

### 4. ADD

Similar to COPY but supports:

* URLs
* Tar extraction

---

### 5. WORKDIR

Sets working directory inside container.

```dockerfile id="w1o2r3k"
WORKDIR /app
```

---

### 6. CMD

Default command when container runs.

```dockerfile id="c1m2d3"
CMD ["python3", "app.py"]
```

---

### 7. ENTRYPOINT

Defines main executable (hard override behavior).

```dockerfile id="e1n2t3"
ENTRYPOINT ["python3"]
```

---

### 8. ENV

Sets environment variables.

```dockerfile id="e1n2v3"
ENV APP_ENV=production
```

---

### 9. EXPOSE

Documents container port.

```dockerfile id="e1x2p3"
EXPOSE 8080
```

---

## Building a Docker Image

```bash id="b1u2i3"
docker build -t myapp .
```

---

## Running Built Image

```bash id="r1u2n3"
docker run myapp
```

---

## Example: Python App Dockerfile

### app.py

```python id="p1y2t3"
print("Hello from Docker")
```

### Dockerfile

```dockerfile id="d1o2c3p"
FROM python:3.10

WORKDIR /app

COPY app.py .

CMD ["python", "app.py"]
```

---

## Example: Node.js App Dockerfile

```dockerfile id="n1o2d3e"
FROM node:18

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

CMD ["node", "index.js"]
```

---

## Dockerfile Layers

Each instruction creates a layer:

```text id="l1a2y3"
FROM → base layer
RUN → install dependencies
COPY → add files
CMD → runtime command
```

---

## Best Practices for Dockerfile

### 1. Use small base images

```dockerfile id="a1l2p3"
FROM alpine
```

---

### 2. Minimize layers

Combine commands:

```dockerfile id="c1o2m3"
RUN apt update && apt install -y curl git
```

---

### 3. Use .dockerignore

Avoid copying unnecessary files:

```text id="d1i2g3"
node_modules
.git
.env
```

---

### 4. Order instructions properly

Put rarely changing layers first:

* FROM
* RUN dependencies
* COPY source code

---

### 5. Avoid running as root

Use non-root user:

```dockerfile id="u1s2e3"
USER appuser
```

---

## Common Mistakes

* Not using .dockerignore
* Using large base images
* Wrong CMD format
* Copying unnecessary files
* Installing dependencies after copying code

---

## Debugging Dockerfile Builds

### Build step-by-step:

```bash id="b1u2i3d"
docker build --no-cache -t myapp .
```

---

### View image history:

```bash id="h1i2s3t"
docker history myapp
```

---

## CMD vs ENTRYPOINT

| Feature  | CMD             | ENTRYPOINT    |
| -------- | --------------- | ------------- |
| Override | Yes             | Limited       |
| Purpose  | Default command | Fixed command |

Example:

```dockerfile id="c1v2e3"
ENTRYPOINT ["python3"]
CMD ["app.py"]
```

---

## Multi-Stage Build (Intro)

Used to reduce image size:

```dockerfile id="m1u2l3"
FROM node AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

FROM nginx
COPY --from=builder /app/build /usr/share/nginx/html
```

---

## Real-World Flow

```text id="f1l2o3"
Write Dockerfile → Build image → Run container → Deploy app
```

---

## Summary

Dockerfile is:

* Blueprint for images
* Automation tool
* Core of CI/CD pipelines
* Essential for DevOps workflows

---

## What Next?

Next topic:

👉 **Docker-Networking.md** (bridge networks, host networking, container communication)

