# Zabbix Using Docker Compose

Run Zabbix as Docker microservices, using Docker Compose and official Zabbix Docker images.
Project goals:

- Be simple and lightweight
- Use SSL for web dashboard
- Store persistent data on the host filesystem

Based on https://github.com/heyvaldemar/zabbix-traefik-letsencrypt-docker-compose


## Getting started

### Basic steps
1. Edit the .env file to update the database password
1. Make a self-signed SSL certificate via the following commands:

```
mkdir certs
cd certs
openssl dhparam -out dhparam.pem 2048
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout ssl.key -out ssl.crt
chmod a+r ssl.key
cd ..
```
3. Start the Zabbix instance: `docker compose up -d`

### Configure the Zabbix server to monitor itself

1. Login using the initial username (Admin) and password (zabbix)
1. In the menu, select Monitoring > Hosts
1. Click Zabbix server and select Configuration > Host
1. Under Interfaces, set DNS name to `zabbix-agent` and set Connect to to DNS.
1. Click the Update button

### The Zabbix Agent

By default, this Docker Compose file runs a container with the Zabbix
agent to monitor the host computer. If you prefer to run the Zabbix
agent directly on the host computer, you can start the other containers
without the Zabbix agent by specifying the zabbix-base.yml configuration
file, for example:

```
docker compose -f zabbix-base.yml up -d
```


## Disclaimer

This configuration is designed to run on a secure LAN. It is not hardened or tested
to be deployed on a server on the internet.
