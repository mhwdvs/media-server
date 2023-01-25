# media-server

Applications:
- Jellyfin
- Jackett
- Sonarr
- Radarr
- Qbittorrent

## Environment variables

Example `.env` file
```
PUID=1000
PGID=1000
STORAGE_PATH=/media-server
TZ=Australia/Perth
```

## Todo

- URLs from Jackett and qbittorrent currently have to be manually fixed (from http://localhost:9114/asd to http://jackett:9114/asd)
- Qibittorrent credentials are currently admin/adminadmin
- have to manually add /downloads folder to sonarr/radarr media management screens
- have to manually disable anonymous usage statistic logging in sonarr/radarr 
- have to set preferred protocol in sonarr/radarr to torrent only
