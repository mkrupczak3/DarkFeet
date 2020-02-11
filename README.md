# Shadowsocks setup
A [docker compose](https://docs.docker.com/compose/compose-file/) setup for a [shadowsocks](https://github.com/shadowsocks) server. Designed to provide a fast and easy way to set up secure and private connections for breaking through the Great Firewall of China.

Shadowsocks服务器的（Docker Compose）设置。 旨在提供一种快速简便的方法来建立安全的私人连接，以突破中国的防火墙。

```yaml
version: "3.3"

services:

  shadowsocks:
    image: shadowsocks/shadowsocks-libev
    ports:
      - "8388:8388/tcp" # <-- change me (if you want)
      - "8388:8388/udp" # <-- change me(if you want)
    environment:
      - METHOD=aes-256-gcm
      - PASSWORD=9MLSpPmNt # <-- change me
    restart: always

  watchtower: # (optional) auto-update when new version released
    image: v2tec/watchtower
    container_name: watchtower
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - /root/.docker/config.json:/config.json
    restart: unless-stopped
```
