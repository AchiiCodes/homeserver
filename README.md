# Media Server Docker Compose Setup

This README provides instructions for setting up a media server using Docker Compose with various services like Plex, Sonarr, Radarr, and more. The configuration ensures that all services run smoothly on a local network with appropriate data persistence.

![Architecture](/architecture.drawio.svg)

## Table of Contents

- [Media Server Docker Compose Setup](#media-server-docker-compose-setup)
  - [Table of Contents](#table-of-contents)
  - [Prerequisites](#prerequisites)
  - [Configuration](#configuration)
    - [Volumes](#volumes)
    - [Networks](#networks)
    - [Services](#services)
  - [Usage](#usage)

## Prerequisites

- Docker installed on your system.
- Docker Compose installed.
- Appropriate folder structure on your host machine.

## Configuration

### Volumes

The following volumes are defined to persist data:

- `plex-data`: Binds to `d:/media`.
- `download-data`: Binds to `d:/media/downloads`.
- `shows-data`: Binds to `d:/media/shows`.
- `movies-data`: Binds to `d:/media/movies`.

### Networks

A single bridge network named `homeserver` is used to connect all services.

### Services

This setup includes the following services:

1. **Homarr**
   - **Image**: `ghcr.io/ajnart/homarr:latest`
   - **Ports**: `7575:7575`
   - **Volumes**: 
     - `/var/run/docker.sock`
     - `./config/docker/homarr/configs:/app/data/configs`
     - `./config/docker/homarr/icons:/app/public/icons`
     - `./config/docker/homarr/data:/data`
   - **Network**: `homeserver`

2. **Plex**
   - **Image**: `lscr.io/linuxserver/plex:latest`
   - **Ports**: `32400:32400`
   - **Volumes**:
     - `./config/docker/plex/config:/config`
     - `plex-data:/media`
   - **Network**: `homeserver`

3. **Portainer**
   - **Image**: `portainer/portainer-ce:alpine`
   - **Ports**: `9000:9000`
   - **Volumes**:
     - `/var/run/docker.sock:/var/run/docker.sock`
   - **Network**: `homeserver`

4. **Sonarr**
   - **Image**: `lscr.io/linuxserver/sonarr:latest`
   - **Ports**: `8989:8989`
   - **Volumes**:
     - `./config/docker/sonarr/data:/config`
     - `download-data:/downloads`
     - `shows-data:/shows`
   - **Network**: `homeserver`

5. **Radarr**
   - **Image**: `lscr.io/linuxserver/radarr:latest`
   - **Ports**: `7878:7878`
   - **Volumes**:
     - `./config/docker/radarr/data:/config`
     - `download-data:/downloads`
     - `movies-data:/movies`
   - **Network**: `homeserver`

6. **Prowlarr**
   - **Image**: `lscr.io/linuxserver/prowlarr:latest`
   - **Ports**: `9696:9696`
   - **Volumes**:
     - `./config/docker/prowlarr/data:/config`
   - **Network**: `homeserver`

7. **qBittorrent**
   - **Image**: `linuxserver/qbittorrent:version-4.6.0-r0`
   - **Ports**: `8090:8090`
   - **Volumes**:
     - `./config/docker/provision/qbittorrent:/config`
     - `download-data:/downloads`
   - **Network**: `homeserver`

8. **Requestrr**
   - **Image**: `thomst08/requestrr:latest`
   - **Ports**: `4545:4545`
   - **Volumes**:
     - `./config/docker/requestrr/config:/root/config`
   - **Network**: `homeserver`

9. **Proxy**
   - **Image**: `jc21/nginx-proxy-manager:latest`
   - **Ports**: `80:80`, `81:81`, `443:443`
   - **Volumes**:
     - `./config/docker/proxy/data:/data`
     - `./config/docker/proxy/letsencrypt:/etc/letsencrypt`
   - **Network**: `homeserver`

## Usage

1. Clone the repository or copy the `docker-compose.yml` file to your working directory.
2. Ensure the folder structure on your host machine matches the volume bindings.
3. Run the following command to start all services:
   ```bash
   docker-compose up -d
