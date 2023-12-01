# docker-plex-qbittorrent-servarr-configs
## Prerequisites
- Docker and Docker Compose installed on your system.

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
cp qbittorrent/env.template qbittorrent/.env
cp servarr/env.template servarr/.env
```

#### Start Services
Each service has a docker-compose.yml file, sourcing environment variables from the respective .env files.
```bash
# Start Plex
docker compose -f plex/docker-compose.yml up -d 

# Start qBittorrent
docker compose -f qbittorrent/docker-compose.yml up -d

# Start Servarr
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
