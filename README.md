# media-server

A completely self-contained media server running on Docker

## Architecture Overview

![Media Server High-Level Architecture Overview](https://www.plantuml.com/plantuml/png/bLFBRjmm3BphAtXh0sJt2ueW2nJe0sdI9a4lHGzQcRQ5LKINehq9YlvxQSjQUzDJVRA6vCnGfAwJM9R-AS0NhBo51-G16JxwfjtSu801TknQB-YaPuGx3GuUZqQy1FpF6jDPTx0Dmdjo1-JV1lJxyHb3UAbzQd_EPqr2aVdqGD4opuTxMos7RtilGimOI-uz_kenISbuUm4VGe_IH_F7c9aMtcstLv1Ppx5CRaoEPMobONByNzoSPC-uNw65_IIvsLoTx1N9DLRarjXAzbNo8hQ6JIH14Eg0QZZbJ9TJ4QRuHg2rmvW1UmGVI-7bbBBl1P9_weAlFQPvQ11HZiG77nk3iO9HGRigCypwDxjRCrCjG3OJi9RHJR4u2kr2W3JkY5EPcHyh67Ir2ekp4QpJU0AqhWMI5ZdRjEh2wfhXSqT9ooY21Y6Giw6mRISDbTL8maKi4sYn3Ob0XI86fP2MgM_QYSTHh7sZUrp1zw-tfNJLk_QMH_neVKWgYXaQ-_uK1LazpCsplf2f-oLrD73NYTSD29UGT1e9EcBPrCH7ovNUCn232zHNq5AIyuk_rbzzl7y1 "Media Server High-Level Architecture Overview")

## Setup

- Configure environment variables
- `docker compose up -d`
- Configure individual services (first time only)

### Environment variables

Example `.env` file
```
# general config
PUID=1000
PGID=1000
STORAGE_PATH=/path/to/media/server/storage
# see here https://en.wikipedia.org/wiki/List_of_tz_database_time_zones
TZ=Australia/Perth

# gluetun config
VPN_SERVICE_PROVIDER=mullvad
OPENVPN_USER=mullvad_account_number
SERVER_COUNTRIES=australia

# ports
JELLYFIN_PORT=8096
JACKETT_PORT=9117
SONARR_PORT=8989
RADARR_PORT=7878
QBITTORRENT_PORT=6881
REQUESTRR_PORT=4545
```

### A note for WSL2 users

If you don't intend to store data on your system's main storage device (ie. your WSL drive), symlinks from Qbittorrent's downloads folder to Jellyfin's media directories will not work, and instead copies will be made of all media, doubling used storage capacity. If you don't want to store all your media-server data on your WSL drive then a Linux virtual machine running Docker may be good alternative.

## Todo

- Qbittorrent credentials are currently admin/adminadmin
- have to manually add /downloads folder to sonarr/radarr media management screens
- have to manually disable anonymous usage statistic logging in sonarr/radarr 
- have to set preferred protocol in sonarr/radarr to torrent only
- Have to manually configure Qbittorrent to seed

## Further reading

- Kubernetes networking: https://cloud.redhat.com/blog/guide-to-kubernetes-egress-network-policies

## Disclaimer

This project is only intended for the download and management of;
- Shows with open licenses or expired copyrights (eg. Big Buck Bunny)
- Content you already own on physical media
    - Maybe you don't have a Blu-Ray player?

I do not recommend or endorse illegitimate usage of any of the services arranged with this docker configuration. Don't use this configuration for anything that may be considered illegal in your place of residence. Observe that all liability and warrenty is waived via the GNU General Public License v3.0.