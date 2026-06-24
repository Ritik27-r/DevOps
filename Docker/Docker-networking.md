# Docker Networking

## What is Docker Networking?

Docker networking allows containers to **communicate with each other, the host machine, and external systems**.

Each container gets its own isolated network stack.

---

## Why Docker Networking Matters

* Enables microservices communication
* Allows database + backend interaction
* Supports multi-container apps
* Controls traffic flow and isolation

---

## Default Docker Networks

When Docker is installed, it creates three default networks:

```text id="n1e2t3"
bridge
host
none
```

---

## 1. Bridge Network (Default)

Most commonly used network.

* Containers get private IPs
* Can communicate via internal network
* Requires port mapping for external access

Example:

```bash id="b1r2i3"
docker run nginx
```

---

### Inspect bridge network:

```bash id="i1n2s3"
docker network inspect bridge
```

---

## 2. Host Network

Container shares host’s network directly.

* No isolation
* No port mapping needed
* High performance

Example:

```bash id="h1o2s3"
docker run --network host nginx
```

---

## 3. None Network

Completely disables networking.

* No internet access
* No communication

Example:

```bash id="n1o2n3"
docker run --network none nginx
```

---

## Container Communication

Containers in same network can communicate using:

* Container name
* Internal IP address

Example:

```text id="c1o2m3"
frontend → backend
```

---

## Creating Custom Networks

```bash id="c1r2n3"
docker network create my_network
```

---

## List Networks

```bash id="l1n2k3"
docker network ls
```

---

## Run Container in Custom Network

```bash id="r1u2n3"
docker run --network my_network nginx
```

---

## Inspect Network

```bash id="i1n2s3n"
docker network inspect my_network
```

---

## Container DNS Resolution

Docker provides built-in DNS inside networks.

Example:

```text id="d1n2s3"
backend container → database container
```

Instead of IP:

```bash id="i1p2a3"
ping db_container
```

---

## Port Mapping

Expose container services to host:

```bash id="p1o2r3"
docker run -p 8080:80 nginx
```

Mapping:

* Host: 8080
* Container: 80

---

## Network Drivers

Docker supports multiple drivers:

| Driver  | Purpose                  |
| ------- | ------------------------ |
| bridge  | Default isolated network |
| host    | Shares host network      |
| none    | No networking            |
| overlay | Multi-host networking    |
| macvlan | Assigns MAC address      |

---

## Overlay Networks (Advanced)

Used in:

* Docker Swarm
* Kubernetes-like environments

Allows communication between containers across multiple hosts.

---

## Container IP Address

Find IP:

```bash id="i1p2a3n"
docker inspect container_id | grep IPAddress
```

---

## Real-World Example: Web App

```text id="w1e2b3"
Frontend → Backend → Database
```

All containers connected via custom bridge network.

---

## Create Multi-Container Network

```bash id="m1u2l3"
docker network create app_net
```

Run containers:

```bash id="f1r2o3"
docker run -d --name db --network app_net mysql
docker run -d --name api --network app_net nodeapp
```

Now API can access DB using:

```text id="d1b2c3"
db:3306
```

---

## Networking Troubleshooting

### Check networks:

```bash id="l1s2n3"
docker network ls
```

---

### Inspect container:

```bash id="i1n2s3c"
docker inspect container_id
```

---

### Test connectivity:

```bash id="p1i2n3"
docker exec -it container ping db
```

---

## Common Networking Issues

* Port already in use
* Wrong network selected
* Container not in same network
* Firewall blocking ports
* DNS resolution failure

---

## Best Practices

* Use custom bridge networks
* Avoid using host network in production
* Use service names instead of IPs
* Limit exposed ports
* Separate networks for frontend/backend/db

---

## Security Considerations

* Do not expose unnecessary ports
* Use isolated networks for databases
* Restrict inter-container communication
* Use internal-only networks for sensitive services

---

## Summary

Docker networking enables:

* Container-to-container communication
* Host-to-container access
* External connectivity
* Secure microservice architecture

---

## What Next?

Next topic:

👉 **Docker-Volumes.md** (data persistence, storage, and container data management)

