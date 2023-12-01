# docker-plex-qbittorrent-servarr-configs
## Prerequisites
- Docker and Docker Compose installed on your system.

## Overview of Services
This configuration integrates multiple services to create a comprehensive media management and streaming solution:
- **Plex:** A media streaming service that organizes and allows you to stream your media content.
- **qBittorrent:** A torrent client for downloading media files.
- **Sonarr, Radarr, Prowlarr, Readarr, and Lidarr (collectively known as Servarr):** Automated media management tools. Sonarr manages TV shows, Radarr manages movies, Prowlarr is for indexing and searching, Readarr for eBooks, and Lidarr for music.

These services work together as follows:
1. **qBittorrent** downloads media files (movies, TV shows, music, etc.) based on torrent files.
2. **Servarr applications** automate the process of finding and downloading media. They interface with qBittorrent to download files and organize them appropriately.
3. **Plex** then accesses these organized media files, creating a user-friendly library that can be streamed to various devices.

## Setup
#### Setup Submodules
Servarr is included as a submodule in a separate repository.
```bash
git submodule update --init
```
#### Copy Template Config Files
Default configurations are provided in template environment files. Update the DATA_ROOT in each file to your storage location.
```bash
cp plex/env.template plex/.env
```
```bash
cp qbittorrent/env.template qbittorrent/.env
```
```bash
cp servarr/env.template servarr/.env
```

#### Start Services
Each service has a docker-compose.yml file, sourcing environment variables from the respective .env files.

###### Start Plex
```bash
docker compose -f plex/docker-compose.yml up -d 
```
###### Start qBittorrent
```bash
docker compose -f qbittorrent/docker-compose.yml up -d
```
###### Start Servarr
```bash
docker compose -f servarr/docker-compose.yml up -d
```

## Service URLs
Once started, services are accessible at the following URLs:

- qBittorrent: http://localhost:8080
- Plex: http://localhost:32400/web
- Sonarr: http://localhost:8989
- Radarr: http://localhost:7878
- Prowlarr: http://localhost:9696
- Readarr: http://localhost:8787
- Lidarr: http://localhost:8686

## Documentation Links
- [Plex Documentation](https://support.plex.tv/)
- [qBittorrent Documentation](https://www.qbittorrent.org/)
- [Servarr Wiki Documentation](https://wiki.servarr.com)
