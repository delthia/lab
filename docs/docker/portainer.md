# Instalación de portainer

En un servidor con docker instalado, portainer se puede instalar con el siguiente comando

```bash
docker run -t -d -p 9000:9000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock d -v ~/docker/volumes/portainer:/data portainer/portainer-ce:latest
```