# Albergando servicios con docker

Docker es una utilidad libre para gestionar aplicaciones en contenedores. Resulta muy útil por su fácil administración y actualización.

Existe una WebUI para gestionar docker llamada [portainer](https://portainer.io). Para instalar portainer sigue [esta guía](portainer/)
Lista de servicios:
- Coder: Editor código en la web. Muy práctico para trabajar en cualquier ordenador que tenga un navegador web. [Página del proyecto](https://github.com/coder/code-server)

- Gitea: Servidor git simple. Útil para albergar tus repositorios de manera local, o para esas cosas que no quieres subir a GitHub o otro proveedor de git, pero que se beneficiarían de utilizar git; o simplemente para tener una copia local de tus repositorios fuera de tu ordenador. [Página del proyecto](https://gitea.io)

- Grafana. Grafana y Prometheus pueden utilizase para ecoger métricas de un endpoint de prometheys y mostrarlas con grafana. [Página del proyecto](https://grafana.com/)

- home-assistant

- Jellyfin: Un buen servidor multimedia. Útil para albergar todos esos CDs y DVDs que tienes por ahí pero que ya no utilizas porque prefieres eschucharlos a través de una plataforma de streaming. [Página del proyecto](https://jellyfin.org/)

- Nextcloud: Probablemente la parte más importante del sistema. Nextcloud es un servidor para compartir archivos que también incluye un calendario y un gestor de contactos. [Página del proyecto](https://nextcloud.com/)

- Uptime-Kuma: Un servicio de monitorización que puede notificarte cuando algo va mal. [Uptime Kuma](https://uptime.kuma.pet/)

- Vaultwarden: Un gestor de contraseñas. Esta imagen se basa y funciona con los clientes de bitwarden, pero incorpora todas las características _"premium"_ de manera gratuita. [Vaultwarden](https://github.com/dani-garcia/vaultwarden)