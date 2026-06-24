# Docker Best Practices

## Why Best Practices Matter

Docker makes things easy—but without discipline, it can lead to:

* Large images
* Slow deployments
* Security risks
* Hard-to-maintain systems

This file focuses on **real production-grade Docker usage**.

---

## 1. Use Small Base Images

Prefer lightweight images:

```dockerfile id="b1a2s3"
FROM alpine
```

Or minimal language images:

* `python:slim`
* `node:alpine`

Avoid full OS images unless required.

---

## 2. Use Specific Image Tags

❌ Bad:

```dockerfile id="b1a2d3"
FROM nginx:latest
```

✅ Good:

```dockerfile id="g1o2o3"
FROM nginx:1.25
```

Why:

* Prevents unexpected updates
* Ensures stable builds

---

## 3. Use .dockerignore

Prevent unnecessary files from being copied:

```text id="d1i2g3"
node_modules
.git
.env
__pycache__
```

---

## 4. Minimize Layers

Combine commands:

❌ Bad:

```dockerfile id="b1a2d3c"
RUN apt update
RUN apt install -y curl
```

✅ Good:

```dockerfile id="g1o2o3c"
RUN apt update && apt install -y curl
```

---

## 5. Use Multi-Stage Builds

Reduce final image size:

```dockerfile id="m1u2l3"
FROM node AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

FROM nginx
COPY --from=builder /app/build /usr/share/nginx/html
```

---

## 6. Don’t Run Containers as Root

Create a non-root user:

```dockerfile id="u1s2e3"
RUN useradd appuser
USER appuser
```

---

## 7. Keep Containers Stateless

Containers should NOT store important data.

Use:

* Volumes
* External databases

---

## 8. Use Environment Variables

❌ Bad:
Hardcoding values inside image

✅ Good:

```dockerfile id="e1n2v3"
ENV NODE_ENV=production
```

Or:

```bash id="r1u2n3"
docker run -e NODE_ENV=production app
```

---

## 9. Proper Port Exposure

Document ports clearly:

```dockerfile id="e1x2p3"
EXPOSE 8080
```

And map them explicitly:

```bash id="p1o2r3"
docker run -p 8080:8080 app
```

---

## 10. Use Health Checks

Ensure container is running properly:

```dockerfile id="h1e2a3"
HEALTHCHECK CMD curl -f http://localhost:8080 || exit 1
```

---

## 11. Avoid Installing Unnecessary Packages

Keep images clean:

* No debugging tools in production
* No extra build tools in runtime images

---

## 12. Optimize Cache Usage

Order Dockerfile properly:

```dockerfile id="c1a2c3"
COPY package.json .
RUN npm install
COPY . .
```

Why:

* Dependencies cached
* Faster rebuilds

---

## 13. Use Fixed Dependencies

Lock versions:

* npm package-lock.json
* pip requirements.txt

Avoid:

* Floating versions

---

## 14. Log Properly

Use stdout/stderr:

❌ Bad:
Writing logs inside container filesystem

✅ Good:

```text id="l1o2g3"
console.log / stdout logs
```

---

## 15. Clean Up Unused Resources

```bash id="c1l2e3"
docker system prune
```

Removes:

* Stopped containers
* Unused images
* Build cache

---

## 16. Secure Secrets Handling

❌ Never store in Dockerfile:

```dockerfile id="b1a2d3"
ENV PASSWORD=12345
```

Use:

* Docker secrets
* Environment variables
* External vaults

---

## 17. Use Restart Policies

Ensure reliability:

```bash id="r1e2s3"
docker run --restart always nginx
```

Options:

* no
* always
* unless-stopped
* on-failure

---

## 18. Limit Resources

Prevent container overload:

```bash id="c1p2u3"
docker run -m 512m --cpus="1.0" nginx
```

---

## 19. Version Everything

* Dockerfile changes
* Images
* Compose files

Always track changes in Git.

---

## 20. Keep Containers Single-Purpose

Each container should do ONE job:

* Web server
* Database
* Cache

Avoid combining multiple services.

---

## Common Mistakes

* Using latest tag in production
* Storing data inside container
* Huge images with unnecessary tools
* No .dockerignore file
* Running everything as root

---

## Production Workflow Example

```text id="p1r2o3"
Code → Dockerfile → Build Image → Push → Deploy Container
```

---

## Summary

Good Docker usage means:

* Small images
* Secure configurations
* Stateless design
* Clean builds
* Predictable deployments

---

## Final Note

Docker is simple to start with—but professional DevOps work depends on how disciplined your Docker practices are.

---

## End of Docker Series

You now have a complete Docker notes system:

* Basics
* Architecture
* Images
* Containers
* Dockerfile
* Networking
* Volumes
* Compose
* Commands
* Best Practices

---

If you want next, I can build:

👉 Kubernetes folder structure (same style, full DevOps depth)

