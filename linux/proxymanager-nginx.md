---
description: What is proxymanager and how to install it?
---

# Proxymanager Nginx

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption><p>nginx proxy manager web gui</p></figcaption></figure>

Nginx Proxy Manager is an open-source and application designed to simplify the management of Nginx’s proxy, SSL and more. **It is built with a user-friendly dashboard that aims to help those users who aren’t exactly Nginx CLI experts.** Plus, it also provides free SSL via Let’s Encrypt, Docker integration.

### Installation

First create directory and database

```bash
mkdir /opt/nginxproxymanager
mkdir /opt/nginxproxymanager/databases
touch /opt/nginxproxymanager/databases/nginxproxy.db
docker network create nginxproxyman
```

Then create a docker-compose file `nano /opt/nginxproxymanager/docker-compose.yml`

```yaml
version: "3"
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    container_name: 'nginxproxymanager'
    restart: unless-stopped
    ports:
      - '80:80' 
      - '443:443' 
      - '81:81' 
    environment:
      DB_SQLITE_FILE: "/data/database.sqlite"

    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt

networks:
  default:
    external:
      name: nginxproxyman
```

Run container and allow ports

```bash
cd /opt/nginxproxymanager
docker-compose up -d 
docker ps
sudo ufw allow 80
sudo ufw allow 443
sudo ufw allow 81
docker run --network nginxproxyman --name owncloud -d owncloud:latest
```
