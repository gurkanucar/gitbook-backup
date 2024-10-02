---
description: Lightweight
---

# Docker Debian Container

```bash
docker run -it --name debian-server --rm bitnami/minideb:latest bash -c "apt-get update && apt-get install -y curl wget vim nano net-tools iputils-ping ufw && bash"
```

```bash
docker run -it --name debian-server --rm debian:latest bash -c "apt-get update && apt-get install -y curl wget vim nano net-tools iputils-ping ufw && bash"
```
