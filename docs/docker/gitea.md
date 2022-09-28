# Instalación de gitea

```yml title="gitea.yaml"
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