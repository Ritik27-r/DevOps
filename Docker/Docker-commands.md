# Docker Commands Cheat Sheet

## What is this file?

This is a **quick reference guide** of the most important Docker commands used in real-world DevOps work.

---

## Image Commands

### Pull an image

```bash id="p1u2l3"
docker pull nginx
```

---

### List images

```bash id="l1i2m3"
docker images
```

---

### Remove image

```bash id="r1m2i3"
docker rmi nginx
```

---

### Remove all unused images

```bash id="p1r2u3"
docker image prune
```

---

### Build image from Dockerfile

```bash id="b1u2i3"
docker build -t myapp .
```

---

### View image history

```bash id="h1i2s3"
docker history nginx
```

---

## Container Commands

### Run container

```bash id="r1u2n3"
docker run nginx
```

---

### Run in detached mode

```bash id="d1e2t3"
docker run -d nginx
```

---

### Run with name

```bash id="n1a2m3"
docker run --name my_container nginx
```

---

### Run with port mapping

```bash id="p1o2r3"
docker run -p 8080:80 nginx
```

---

### List running containers

```bash id="l1s2c3"
docker ps
```

---

### List all containers

```bash id="a1l2c3"
docker ps -a
```

---

### Stop container

```bash id="s1t2o3"
docker stop container_id
```

---

### Start container

```bash id="s1t2a3"
docker start container_id
```

---

### Restart container

```bash id="r1e2s3"
docker restart container_id
```

---

### Remove container

```bash id="r1m2c3"
docker rm container_id
```

---

### Force remove container

```bash id="f1r2m3"
docker rm -f container_id
```

---

## Debugging Commands

### View logs

```bash id="l1o2g3"
docker logs container_id
```

---

### Follow logs live

```bash id="f1l2o3"
docker logs -f container_id
```

---

### Inspect container details

```bash id="i1n2s3"
docker inspect container_id
```

---

### View running processes

```bash id="p1r2o3"
docker top container_id
```

---

## Exec Commands

### Open shell inside container

```bash id="e1x2e3"
docker exec -it container_id bash
```

---

### Alternative shell

```bash id="s1h2e3"
docker exec -it container_id sh
```

---

## System Commands

### Docker version

```bash id="v1e2r3"
docker --version
```

---

### Docker system info

```bash id="i1n2f3"
docker info
```

---

### Disk usage

```bash id="d1i2s3"
docker system df
```

---

### Cleanup unused data

```bash id="p1r2u3c"
docker system prune
```

---

## Volume Commands

### Create volume

```bash id="c1r2v3"
docker volume create my_volume
```

---

### List volumes

```bash id="l1v2o3"
docker volume ls
```

---

### Inspect volume

```bash id="i1v2o3"
docker volume inspect my_volume
```

---

### Remove volume

```bash id="r1m2v3"
docker volume rm my_volume
```

---

## Network Commands

### List networks

```bash id="l1n2w3"
docker network ls
```

---

### Create network

```bash id="c1r2n3"
docker network create my_network
```

---

### Inspect network

```bash id="i1n2w3"
docker network inspect my_network
```

---

### Remove network

```bash id="r1m2n3"
docker network rm my_network
```

---

## Docker Compose Commands

### Start services

```bash id="u1p2s3"
docker-compose up
```

---

### Start in background

```bash id="d1c2o3"
docker-compose up -d
```

---

### Stop services

```bash id="d1o2w3"
docker-compose down
```

---

### Build services

```bash id="b1u2i3"
docker-compose build
```

---

### View logs

```bash id="l1c2o3"
docker-compose logs
```

---

## Image Transfer Commands

### Save image to file

```bash id="s1a2v3"
docker save -o image.tar nginx
```

---

### Load image from file

```bash id="l1o2a3"
docker load -i image.tar
```

---

## Tag & Push Commands

### Tag image

```bash id="t1a2g3"
docker tag myapp user/myapp:v1
```

---

### Login to Docker Hub

```bash id="l1o2g3"
docker login
```

---

### Push image

```bash id="p1u2s3"
docker push user/myapp:v1
```

---

## Quick Summary

| Category   | Key Commands             |
| ---------- | ------------------------ |
| Images     | pull, build, rmi, images |
| Containers | run, ps, stop, rm, exec  |
| Debug      | logs, inspect, top       |
| System     | info, prune, df          |
| Volumes    | volume create/ls/rm      |
| Networks   | network create/ls/rm     |
| Compose    | up, down, build, logs    |

---

## Final Note

Docker commands are not about memorizing everything — they are about:

* Understanding patterns
* Practicing workflows
* Knowing what to search quickly

---

## What Next?

Next topic:

👉 **Docker-Best-Practices.md** (real production-level usage rules and DevOps standards)

