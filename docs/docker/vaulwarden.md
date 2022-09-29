---
title: Bitwarden
---
# Instalación de bitwarden

Vaultwarden es una imagen de servidor alternativa compatible con la de bitwarden.

Bitwarden es un gestor de contraseñas con extensiones para los navegadores y aplicaciones para los sistemas operativos móviles.

El funcionamiento de este contenedor es bastante sencillo, por lo que solo necesita un volumen para los datos y abrir el puerto correspondiente en docker.

```yaml title="vaultwarden.yml"
version: '3'
services:
    vaultwarden:
        container_name: vaultwarden
        image: vaultwarden/server:latest
        ports:
            - 82:80
        volumes:
            - ~/docker/volumes/vw-data:/data
        restart: always
        environment:
            - SIGNUPS_ALLOWED=false
```

Configuración de nginx para vaultwarden:

```nginx_configuration_file title="vaultwarden-docker"
server {
    server_name vault.dominio.com;

    location / {
        proxy_pass http://localhost:82;
    }
}
```