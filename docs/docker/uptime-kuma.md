---
title: Uptime Kuma
---
# Instalación de uptime kuma

Uptime Kuma es un contenedor que monitoriza el estado de los servicios y te notifica cuando alguno falla.

Instalarlo es muy fácil:

```yaml title="uptime-kuma.yml"
version: '3'
services:
    uptime-kuma:
        container_name: uptime-kuma
        image: louislam/uptime-kuma:1
        ports:
            - 3001:3001
        volumes:
            - ~/docker/volumes/uptime-kuma:/app/data
        restart: always
```