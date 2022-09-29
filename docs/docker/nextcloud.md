---
title: Nextcloud
---
# Instalación de nextcloud

![Nextcloud homepage](screenshots/Screenshot%202022-09-28%20at%2022-12-34%20Dashboard%20-%20Nextcloud.png)

Nextcloud es probablemente el contenedor más importante en mi día a día. Consiste en un sistema completo para subir y gestionar archivos, calendarios, contactos, tareas y hasta noticias y pódcasts. Aunque su rendimiento no es el mejor (independientemente del hardware en el que se ejecute), es suficientemente rápido y la cantidad de funcionalidades que tienen le hacen una utilidad excepcional, ya sea para un único usuario, para compartir archivos con familiares y amigos, o para trabajar en grupo.

También existe la posibilidad de conectar nextcloud con una suite de oficina para editar archivos desde el navegador de manera colaborativa, pero no he conseguido poner a funcionar el servidor integrado de collabora en la raspberry, el contenedor de collabora por separado, ni la suite de onlyoffice.

El siguiente _docker-compose_ instalá un contenedor de nextcloud con una base de datos mariadb.
```yaml title="nextcloud.yml"
version: '2'
services:
    db:
        container_name: nextcloud-mariadb
        image: mariadb:10.5
        restart: always
        command: --transaction-isolation=READ_COMMITED --binlog-format=ROW
        volumes:
            - ~/docker/volumes/nextcloud-db:/var/lib/mysql
        environment:
            - MYSQL_ROOT_PASSWORD=nextclouddbpassword
            - MYSQL_PASSWORD=nextclouddbpassword
            - MYSQL_DATABASE=nextcloud
            - MYSQL_USER=nextcloud
    app:
        container_name: nextcloud
        image: nextcloud:latest
        restart: always
        ports:
            - 8080:80
        volumes:
            - ~/docker/volumes/nextclodud:/var/www/html
        environment:
            - MYSQL_PASSWORD=nextclouddbpassword
            - MYSQL_DATABASE=nextcloud
            - MYSQL_USER=nextcloud
            - MYSQL_HOST=db
```

Configuración de nginx para nextcloud:

```nginx_configuration_file title="nextcloud-docker"
server {
    server_name cloud.dominio.com;

    add_header Strict-Transport-Security "max-age=15552000; includeSubDomains";

    location / {
        proxy_pass http://localhost:8080;

        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;

        add_header Strict-Transport-Security "max-age=15552000; includeSubDomains; preload";
        client_max_body_size 0;

        access_log /var/log/nginx/nextcloud.access.log;
        error_log /var/log/nginx/nextcloud.error.log;
    }

    location /.well-known/carddav {
        return 301 $scheme://$host/remote.php/dav;
    }

    location /.well-known/caldav {
        return 301 $scheme://$host/remote.php/dav;
    }
}
```