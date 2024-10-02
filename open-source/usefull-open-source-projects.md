# Usefull Open Source Projects

### Util

**Language Tool Server:** grammarly alternative | [https://github.com/languagetool-org/languagetool](https://github.com/languagetool-org/languagetool)

**Rssbridge:** rss util tool

**moodle:** udemy alternative

### System Monitoring

**uptime-kuma:** [**uptime-kuma**](https://github.com/louislam/uptime-kuma)\
**grafana**

### Chat Boat

**typebot:** [https://github.com/baptisteArno/typebot.io](https://github.com/baptisteArno/typebot.io)

### LinkTree Alternative

**linkstack:** [https://github.com/linkstackorg/linkstack](https://github.com/linkstackorg/linkstack)

### Form

discourse: [https://github.com/discourse/discourse](https://github.com/discourse/discourse)

**flarum:** [https://github.com/flarum/flarum](https://github.com/flarum/flarum)

### Container Web Browser

**docker firefox:** [https://github.com/linuxserver/docker-firefox](https://github.com/linuxserver/docker-firefox)

```bash
docker run -d \
  --name=firefox \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Etc/UTC \
  -p 3000:3000 \
  -p 3001:3001 \
  -v /DATA/AppData/firefox:/config \
  --shm-size="1gb" \
  --restart unless-stopped \
  lscr.io/linuxserver/firefox:latest
```

### Q\&A

**incubator-answer:** [https://github.com/apache/incubator-answer](https://github.com/apache/incubator-answer)

### Feature Toggle

**feature flag:** [https://github.com/Unleash/unleash](https://github.com/Unleash/unleash)

### Cloud OS

**CasaOs:** open source hosted web os

**KasmDesktop:** virtual workspace | [https://kasmweb.com/](https://kasmweb.com/)

### Video Editor

**OpenShot**

### **Yt Downloader**

**metube:** [**https://github.com/alexta69/metube**](https://github.com/alexta69/metube)

```bash
docker run -d -p 8065:8081 -v /DATA/AppData/yt:/downloads ghcr.io/alexta69/metube
```

### Designer

**PenPot:** figma alternative self hosted

**ExcaliDraw:** self hosted diagram designer

### Proxy

**traefik:**

### **Finance**

**Firefly III**

### **Productivity And Utility**

**shiori:** bookmark manager | [**https://github.com/go-shiori/shiori**](https://github.com/go-shiori/shiori)

**wallabag:** bookmark manager

**privatebin:** copy paste (pastebin alternative)

**novu:** notification platform

**formio:** javascript form generator

**apache-airflow:**  scheduler

**linkwarden:** Self-hosted collaborative bookmark manager

**commafeed:** rss reader&#x20;

**freshrss:** [https://github.com/FreshRSS/FreshRSS](https://github.com/FreshRSS/FreshRSS)

**plane.io** : [https://github.com/makeplane/plane](https://github.com/makeplane/plane)

**Mealie:** self hosted recipe manager | [https://github.com/mealie-recipes/mealie](https://github.com/mealie-recipes/mealie)

**Visual Studio Code Server:** [https://github.com/linuxserver/docker-code-server](https://github.com/linuxserver/docker-code-server)

### Documents Storage & Edit

**Paperless-ngx:** self hosted document storage

**Stirling-pdf:** self hosted pdf editor (edit,merge,create etc.).

### Media Server

**jellyfin:** media streaming self hosted

### Url Shortener

**Yourls:** An open-source URL shortener.&#x20;

**Shlink:** Another open-source URL shortener.&#x20;

Slash: link sharing | [https://github.com/yourselfhosted/slash](https://github.com/yourselfhosted/slash)

```bash
docker run -d --name slash -p 5231:5231 -v /DATA/AppData/slash/:/var/opt/slash yourselfhosted/slash:latest
```

### File Management&#x20;

**Filebrowser:** A file browser similar to Google Drive.&#x20;

```bash
docker run -d -p 89:80 --name filebrowser filebrowser/filebrowser
```

**Nextcloud:** A secure server solution for managing and sharing your data.&#x20;

### Virtualization

**Proxmox:** A powerful virtualization platform for running virtual machines.&#x20;

### Project Management

**Focalboard:** An open-source project management tool.&#x20;

```bash
docker run -d -it -p 90:8000 mattermost/focalboard 
```

### Note-Taking&#x20;

**Xournal++ :** A note-taking platform that lets you write on your screen as if using a pen.&#x20;

### Mapping and Navigation

**Organic Maps:** An open-source alternative to Google Maps.

### Media Streaming

**Navidrome:** A self-hosted alternative to Spotify.&#x20;

```bash
docker run -d --name navidrome --restart=unless-stopped --user $(id -u):$(id -g) -v C:/Users/user/my-musics:/music -v C:/path/to/data:/data -p 4533:4533 -e ND_LOGLEVEL=info deluan/navidrome:latest 
```

### Communication and Collaboration&#x20;

**Mirotalk:** A free, open-source video conferencing platform.&#x20;

**Outline:** A self-hosted alternative to Confluence for team collaboration.&#x20;

### Home Automation&#x20;

**Homebridge:** An open-source platform for integrating IoT devices and creating a smart home environment.&#x20;

### Cloud Storage&#x20;

**Minio:** A self-hosted alternative to Amazon S3 for object storage.&#x20;

### Content Saving&#x20;

**Wallabag:** A self-hosted platform for saving and organizing links, websites, and articles.&#x20;

### Utility and Productivity&#x20;

**ShareX:**  A versatile screen capture and recording tool.&#x20;

### Password Management&#x20;

**Vaultwarden:**  A self-hosted password management solution based on Bitwarden.
