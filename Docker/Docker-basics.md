# Docker Basics

## What is Docker?

Docker is a platform used to **build, ship, and run applications inside containers**.

A container packages an application with everything it needs:

* Code
* Runtime
* System tools
* Libraries
* Dependencies

This makes applications run the same in every environment.

---

## Why Docker is Used

* Eliminates “it works on my machine” problem
* Lightweight compared to virtual machines
* Fast startup time
* Easy scaling
* Consistent environments across Dev, Test, Production

---

## Docker vs Virtual Machine

| Feature     | Docker Container      | Virtual Machine |
| ----------- | --------------------- | --------------- |
| OS          | Shares host OS kernel | Full OS per VM  |
| Size        | Lightweight (MBs)     | Heavy (GBs)     |
| Boot time   | Seconds               | Minutes         |
| Performance | High                  | Lower           |
| Isolation   | Process-level         | Full system     |

---

## Key Docker Concepts

### 1. Image

A **read-only template** used to create containers.

Example:

```text id="i1m2a3g"
nginx, ubuntu, node
```

---

### 2. Container

A **running instance of an image**.

Example:

```text id="c1o2n3t"
nginx container running web server
```

---

### 3. Dockerfile

A script used to build Docker images.

---

### 4. Docker Engine

Core software that runs Docker.

---

## Docker Architecture

```text id="a1r2c3h"
Docker Client → Docker Daemon → Images → Containers
```

### Components:

#### Docker Client

Command-line tool (`docker`)

#### Docker Daemon

Background service that manages containers

#### Docker Registry

Stores images (Docker Hub)

---

## How Docker Works

1. Write Dockerfile
2. Build image
3. Run container
4. Application runs inside container

---

## Installing Docker (Ubuntu)

```bash id="i1n2s3t"
sudo apt update
sudo apt install docker.io -y
```

Start Docker:

```bash id="s1t2a3r"
sudo systemctl start docker
sudo systemctl enable docker
```

Check version:

```bash id="v1e2r3"
docker --version
```

---

## First Docker Command

```bash id="h1e2l3l"
docker run hello-world
```

This:

* Pulls image from Docker Hub
* Creates container
* Runs it

---

## Basic Docker Workflow

```text id="w1o2r3k"
Pull Image → Create Container → Run Application
```

---

## Checking Docker Status

```bash id="s1t2a3t"
docker info
```

---

## Listing Images

```bash id="l1i2s3t"
docker images
```

---

## Listing Containers

### Running containers:

```bash id="r1u2n3"
docker ps
```

### All containers:

```bash id="a1l2l3"
docker ps -a
```

---

## Running a Container

```bash id="r1u2n4"
docker run nginx
```

Run in background:

```bash id="d1e2t3"
docker run -d nginx
```

---

## Naming a Container

```bash id="n1a2m3"
docker run --name mynginx nginx
```

---

## Port Mapping

```bash id="p1o2r3"
docker run -p 8080:80 nginx
```

* 8080 → host machine
* 80 → container

---

## Stopping Containers

```bash id="s1t2o3"
docker stop container_id
```

---

## Starting Containers

```bash id="s1t2a4"
docker start container_id
```

---

## Removing Containers

```bash id="r1m2c3"
docker rm container_id
```

Force remove:

```bash id="f1r2c3"
docker rm -f container_id
```

---

## Removing Images

```bash id="r1i2m3"
docker rmi image_id
```

---

## Docker Logs

```bash id="l1o2g3"
docker logs container_id
```

Follow logs:

```bash id="f1o2l3"
docker logs -f container_id
```

---

## Inspect Container

```bash id="i1n2s4"
docker inspect container_id
```

---

## Interactive Container

```bash id="i1n2t3"
docker run -it ubuntu bash
```

---

## Exit Container

```bash id="e1x2i3"
exit
```

---

## Detached vs Foreground Mode

### Foreground:

Terminal stays attached

### Detached:

```bash id="d1e2t4"
docker run -d nginx
```

---

## Docker Pull Image

```bash id="p1u2l3"
docker pull nginx
```

---

## Docker Push (to registry)

```bash id="p1u2s4"
docker push username/image_name
```

---

## Common Docker Commands Summary

```bash id="s1u2m3"
docker run
docker ps
docker images
docker stop
docker start
docker rm
docker rmi
docker logs
docker exec
docker pull
docker push
```

---

## Common Mistakes

* Forgetting port mapping
* Running containers without `-d`
* Not cleaning unused images
* Confusing image vs container
* Using latest tag blindly

---

## Best Practices

* Use specific image versions
* Clean unused containers regularly
* Use `.dockerignore`
* Avoid running as root inside container
* Use small base images (alpine)

---

## Summary

Docker helps you:

* Package applications
* Run consistent environments
* Deploy faster
* Scale easily

---

## What Next?

Next topic:

👉 **Docker-Architecture.md** (deep dive into how Docker engine, daemon, and registry work)

