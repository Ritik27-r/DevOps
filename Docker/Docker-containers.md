# Docker Containers

## What is a Container?

A Docker container is a **running instance of a Docker image**.

It is an isolated environment that runs an application with its dependencies.

---

## Image vs Container

| Image          | Container        |
| -------------- | ---------------- |
| Blueprint      | Running instance |
| Static         | Dynamic          |
| Read-only      | Read-write layer |
| Stored on disk | Executes process |

Example:

```text id="i1m2c3"
nginx image → nginx container (running web server)
```

---

## Container Lifecycle

```text id="l1i2f3"
Created → Running → Paused → Stopped → Deleted
```

---

## Creating a Container

### Basic run

```bash id="c1r2e3"
docker run nginx
```

---

### Detached mode (background)

```bash id="d1e2t3"
docker run -d nginx
```

---

### Naming a container

```bash id="n1a2m3"
docker run --name my_nginx nginx
```

---

### Port mapping

```bash id="p1o2r3"
docker run -p 8080:80 nginx
```

Host → Container mapping:

* 8080 → host machine
* 80 → container port

---

## Listing Containers

### Running containers only

```bash id="r1u2n3"
docker ps
```

---

### All containers

```bash id="a1l2l3"
docker ps -a
```

---

## Starting a Container

```bash id="s1t2a3"
docker start container_id
```

---

## Stopping a Container

```bash id="s1t2o3"
docker stop container_id
```

Gracefully stops container process.

---

## Restarting a Container

```bash id="r1e2s3"
docker restart container_id
```

---

## Removing a Container

```bash id="r1m2c3"
docker rm container_id
```

Force remove:

```bash id="f1r2m3"
docker rm -f container_id
```

---

## Container Logs

View output of running container:

```bash id="l1o2g3"
docker logs container_id
```

Follow logs in real-time:

```bash id="f1l2o3"
docker logs -f container_id
```

---

## Executing Commands Inside Container

### Open shell inside container

```bash id="e1x2e3"
docker exec -it container_id bash
```

If bash is not available:

```bash id="s1h2e3"
docker exec -it container_id sh
```

---

## Inspect Container

Get detailed info:

```bash id="i1n2s3"
docker inspect container_id
```

Includes:

* Network settings
* Mounts
* Environment variables
* State

---

## Container States

| State   | Meaning                          |
| ------- | -------------------------------- |
| Created | Container exists but not started |
| Running | Active execution                 |
| Paused  | Suspended temporarily            |
| Exited  | Stopped                          |
| Dead    | Failed state                     |

---

## Environment Variables in Containers

```bash id="e1n2v3"
docker run -e ENV=production nginx
```

---

## Detached vs Foreground Mode

### Foreground

```bash id="f1r2o3"
docker run nginx
```

### Detached

```bash id="d1e2t4"
docker run -d nginx
```

---

## Auto Remove Container

Container deletes automatically after exit:

```bash id="a1u2t3"
docker run --rm nginx
```

---

## Resource Limits

Limit memory:

```bash id="m1e2m3"
docker run -m 512m nginx
```

Limit CPU:

```bash id="c1p2u3"
docker run --cpus="1.5" nginx
```

---

## Container Networking Basics

Containers get:

* Internal IP address
* Virtual network interface
* DNS resolution (by name)

Check IP:

```bash id="i1p2a3"
docker inspect container_id | grep IPAddress
```

---

## Container File System

Each container has:

* Read-only image layers
* Writable container layer

Changes inside container do NOT affect image.

---

## Copy Files Between Host and Container

### Copy from container to host

```bash id="c1p2y3"
docker cp container_id:/file.txt .
```

### Copy from host to container

```bash id="c4p5y6"
docker cp file.txt container_id:/tmp/
```

---

## Common Container Issues

* Port already in use
* Container exits immediately
* Permission errors
* Missing dependencies
* Crash due to wrong command

---

## Debugging Containers

Check logs:

```bash id="l1o2g3b"
docker logs container_id
```

Check process:

```bash id="p1s2e3"
docker top container_id
```

Inspect details:

```bash id="i1n2s3b"
docker inspect container_id
```

---

## Best Practices

* Use meaningful container names
* Run containers in detached mode for services
* Always map ports explicitly
* Avoid running as root when possible
* Clean unused containers regularly

---

## Common Commands Summary

```bash id="s1u2m3"
docker run
docker ps
docker stop
docker start
docker restart
docker rm
docker exec
docker logs
docker inspect
docker cp
```

---

## Summary

Containers are:

* Lightweight runtime instances
* Isolated processes
* Based on images
* Temporary by design

They are the core execution unit in Docker.

---

## What Next?

Next topic:

👉 **Dockerfile-Basics.md** (how to build your own Docker images step-by-step)

