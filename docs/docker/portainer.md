# Instalación de portainer

En un servidor con docker instalado, portainer se puede instalar con el siguiente comando
```bash
docker run -t -d -p 9000:9000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock d -v ~/docker/volumes/portainer:/data portainer/portainer-ce:latest
```

El siguiente paso es navegar a la IP del servidor en el puerto 9000. Verás un formulario en el que crear un usuario.

Después de iniciar sesión, esta será la página principal:

![Portainer dashboard](screenshots/Screenshot%202022-09-28%20at%2015-49-17%20Portainer.png)

Al hacer clic en _local_ aparecerá una lista de opciones para gestionar docker en el servidor que ejecuta portainer. En la barra lateral aparecerá un panel con la opción _Templates_, a partir del cual se pueden crear contenedores de manera automática.

![Local dashboard](screenshots/Screenshot%202022-09-28%20at%2015-53-07%20Portainer%20local.png)