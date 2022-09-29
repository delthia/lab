---
title: Gitea
---
# Instalación de gitea

![Gitea homepage](screenshots/Screenshot%202022-09-28%20at%2022-05-04%20Gitea%20Git%20with%20a%20cup%20of%20tea.png)

Gitea es un servidor de git con bastantes características. Lo utilizan proyectos como [codeberg](https://codeberg.org/), pero también tiene un lugar en un servidor local, para ayudar a gestionar y sincronizar repositorios entre ordenadores sin tener que subirlos a un servidor desconocido.

La parte más complicada de la configuración del contenedor es hacer funcionar correctamente el ssh en el puerto 22, ya que colisiona con el del huésped si está en el mismo puerto. Aunque existen métodos para situar el ssh del contenedor en el mismo puerto, la manera más fácil de solucionarlo es utilizar un puerto diferente del valor por defecto para gitea y/o para el huésped.

El siguiente _docker-compose_ instalará un contenedor de gitea sin una base de datos externa. Suficiente para una instalación pequeña con un usuario, pero probablemente no rinda lo suficiente si lo que se busca es una instalación con más usuarios y proyectos.

```yaml title="gitea.yaml"
version: "3"
networks:
    gitea:
        external: false

services:
    server:
        image: gitea/gitea:1.17.1
        container_name: gitea
        environment:
            - USER_UID=1000
            - USER_GID=1000
        restart: always
        networks:
            - gitea
        volumes:
            - ~/docker/volumes/gitea:/data
            - /etc/timezone:/etc/timezone:ro
            - /etc/localtime:/etc/localtime:ro
        ports:
            - "3000:3000"
            - "222:22"
```

Configuración de nginx para gitea:

```nginx_configuration_file title="gitea-docker"
server {
    listen 80;
    server_name git.dominio.com;

    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```