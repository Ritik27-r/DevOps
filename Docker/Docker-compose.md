# Docker Compose

## What is Docker Compose?

Docker Compose is a tool used to **define and run multi-container Docker applications** using a single YAML file.

Instead of running multiple `docker run` commands, you define everything in one file.

---

## Why Docker Compose is Used

* Manage multi-container apps easily
* Single configuration file
* Simplifies networking between services
* Faster development setup
* Easy environment replication

---

## Compose vs Docker CLI

| Docker CLI              | Docker Compose      |
| ----------------------- | ------------------- |
| One container at a time | Multiple containers |
| Manual setup            | Automated setup     |
| Complex commands        | Simple YAML file    |

---

## Docker Compose File

Default file name:

```text id="d1o2c3"
docker-compose.yml
```

---

## Basic Structure

```yaml id="y1a2m3"
version: "3.8"

services:
  app:
    image: nginx
    ports:
      - "8080:80"
```

---

## Key Components

### 1. version

Defines Compose file version.

```yaml id="v1e2r3"
version: "3.8"
```

---

### 2. services

Defines containers.

---

### 3. image

Specifies Docker image.

```yaml id="i1m2g3"
image: nginx
```

---

### 4. build

Build image from Dockerfile.

```yaml id="b1u2i3"
build: .
```

---

### 5. ports

Maps ports between host and container.

```yaml id="p1o2r3"
ports:
  - "8080:80"
```

---

### 6. volumes

Attaches storage.

```yaml id="v1o2l3"
volumes:
  - my_data:/app
```

---

### 7. environment

Sets environment variables.

```yaml id="e1n2v3"
environment:
  - ENV=production
```

---

## Running Docker Compose

### Start services

```bash id="u1p2s3"
docker-compose up
```

Detached mode:

```bash id="d1e2t3"
docker-compose up -d
```

---

## Stop services

```bash id="s1t2o3"
docker-compose down
```

---

## View running containers

```bash id="p1s2c3"
docker ps
```

---

## Example: Web App + Database

```yaml id="e1x2a3"
version: "3.8"

services:
  web:
    image: nginx
    ports:
      - "8080:80"

  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root
```

---

## Multi-Container Architecture

```text id="a1r2c3"
Frontend → Backend → Database
```

All services defined in one YAML file.

---

## Named Volumes in Compose

```yaml id="v1o2l3c"
volumes:
  db_data:
```

Usage:

```yaml id="u1s2e3"
services:
  db:
    image: mysql
    volumes:
      - db_data:/var/lib/mysql
```

---

## Networks in Compose

Compose automatically creates a default network.

Services can communicate using service names:

```text id="n1e2t3"
db:3306
```

---

## Example: Full Stack App

```yaml id="f1u2l3"
version: "3.8"

services:
  frontend:
    image: nginx
    ports:
      - "8080:80"

  backend:
    build: ./backend
    ports:
      - "5000:5000"
    environment:
      - DB_HOST=db

  db:
    image: postgres
    environment:
      POSTGRES_PASSWORD: root
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:
```

---

## Build with Compose

```bash id="b1u2i3c"
docker-compose build
```

---

## Logs in Compose

```bash id="l1o2g3"
docker-compose logs
```

Follow logs:

```bash id="f1o2l3"
docker-compose logs -f
```

---

## Restart Services

```bash id="r1e2s3"
docker-compose restart
```

---

## Remove Everything

```bash id="d1o2w3"
docker-compose down -v
```

Removes:

* Containers
* Networks
* Volumes (optional)

---

## Scaling Services

```bash id="s1c2a3"
docker-compose up --scale web=3
```

Runs multiple instances of service.

---

## Environment Files (.env)

Instead of hardcoding values:

```text id="e1n2v3f"
DB_PASSWORD=root
```

Use in compose:

```yaml id="y1a2m3c"
environment:
  - DB_PASSWORD=${DB_PASSWORD}
```

---

## Common Mistakes

* Wrong indentation in YAML
* Forgetting ports mapping
* Not using service names for communication
* Mixing up build and image
* Not cleaning old containers

---

## Best Practices

* Keep services modular
* Use `.env` files
* Always define volumes for databases
* Use service names instead of IPs
* Keep compose files version controlled

---

## Summary

Docker Compose helps you:

* Run multiple containers easily
* Manage full applications
* Simplify networking
* Automate environment setup

---

## What Next?

Next topic:

👉 **Docker-Commands.md** (complete cheat sheet of all Docker CLI commands)

