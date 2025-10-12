# Zabbix Using Docker Compose

Run Zabbix as Docker microservices, using official Zabbix Docker images.
Forked from https://github.com/heyvaldemar/zabbix-traefik-letsencrypt-docker-compose

## TODO
- Move volumes to local storage
- Remove zabbix network
- Getting started instructions
  - Configure Zabbix monitoring
  - SSL & DH parameters
- Make SSL optional - fallback to HTTP

## Done
- Remove hardcoded Caddy config
- Remove extra web proxy by using Nginx directly
- Remove traefik network
