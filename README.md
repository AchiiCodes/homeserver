# Medialab

[![Docker Compose](https://img.shields.io/badge/Docker--Compose-blue?logo=docker&logoColor=white)](https://docs.docker.com/compose/)
![sonarr Badge](https://img.shields.io/badge/sonarr-2596BE?logo=sonarr&logoColor=fff&style=flat)
![Homarr Badge](https://img.shields.io/badge/Homarr-FA5252?logo=homarr&logoColor=fff&style=flat)
![radarr Badge](https://img.shields.io/badge/radarr-FFCB3D?logo=radarr&logoColor=000&style=flat)  
![Plex Badge](https://img.shields.io/badge/Plex-EBAF00?logo=plex&logoColor=fff&style=flat)
[![Prowlarr](https://img.shields.io/badge/Prowlarr-22223b?logo=prowlarr&logoColor=white)](https://prowlarr.com/)
![qbittorrent Badge](https://img.shields.io/badge/qbittorrent-2F67BA?logo=qbittorrent&logoColor=fff&style=flat)
[![Requestrr](https://img.shields.io/badge/Requestrr-4B8DF8?logo=data:image/svg+xml;base64,PHN2ZyBmaWxsPSIjZmZmIiB2aWV3Qm94PSIwIDAgMzAgMzAiIHdpZHRoPSIzMCIgaGVpZ2h0PSIzMCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48Y2lyY2xlIGN4PSIxNSIgY3k9IjE1IiByPSIxNSIgZmlsbD0iIzRiOGRmOCIvPjxwYXRoIGQ9Ik0yMSAxM2gtNnYtM2MwLTEuMS0uOS0yLTItMnMtMiAuOS0yIDJ2M2gtNmMtMS4xIDAtMiAuOS0yIDJ2N2MwIDEuMS45IDIgMiAyaDE4YzEuMSAwIDItLjkgMi0ydi03YzAtMS4xLS45LTItMi0yem0tNiA2Yy0xLjEgMC0yLS45LTItMnMuOS0yIDItMiAyIC45IDIgMi0uOSAyLTItMnoiIGZpbGw9IiNmZmYiLz48L3N2Zz4=)](https://github.com/darkalfx/requestrr)
![Nginx Proxy Manager Badge](https://img.shields.io/badge/Nginx%20Proxy%20Manager-F15833?logo=nginxproxymanager&logoColor=fff&style=flat)
[![Overseerr](https://img.shields.io/badge/Overseerr-FF6C2C?logo=overseerr&logoColor=white)](https://overseerr.dev/)

This README describes a homelab setup using Docker Compose to manage and automate downloading, requesting, and organizing movies and TV series. The configuration brings together services like Plex, Sonarr, Radarr, and others to provide a seamless media server experience with persistent storage and easy access on your local network.

![Architecture](/architecture.drawio.svg)

## Prerequisites

- Docker installed on your system.
- Docker Compose installed.
- Appropriate folder structure on your host machine.


## Usage

1. Clone the repository or copy the `docker-compose.yml` file to your working directory.
2. Ensure the folder structure on your host machine matches the volume bindings.
3. Run the following command to start all services: ```docker-compose up -d```

### Service URLs

| Service      | URL                                  |
|--------------|--------------------------------------|
| Homarr       | http://localhost:7575                |
| Plex         | http://localhost:32400/web           |
| Portainer    | http://localhost:9000                |
| Sonarr       | http://localhost:8989                |
| Radarr       | http://localhost:7878                |
| Prowlarr     | http://localhost:9696                |
| qBittorrent  | http://localhost:8090                |
| Requestrr    | http://localhost:4545                |
| Proxy (NPM)  | http://localhost:81 (admin UI)       |
| Overseerr    | http://localhost:5055                |