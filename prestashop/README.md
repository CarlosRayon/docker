## Instalación desde 0

Ya estaría todo todo instalado. Si queremos instalar de 0:

- Borramos el contenido de la carpeta _www_ y de la carpeta _data/mysql_
- Descargamos Prestashop desde: [Link descarga](https://www.prestashop.com/es/descargar-exito) descomprimimos y metemos en www
- Revisamos configuraciones docker-compose.yml y .env
- Ejecutamos:
  `docker-compose up -d`

- Con el contenedor creado. Ejecutamos un bash dentro del mismo:
  `docker exec -it {container_id} /bin/bash`

- Damos permisos a los ficheros prestashop
  `chown -R root:root /var/www/html/`
  `chmod 777 -R /var/www/html`

Cuando empiece instalación, debemos poner la ip del contenedor de la base datos. Vemos la ip con:
`docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container_id`

Pass, user y DB seran (las que definamos en .env para la mysql):
`prestashop`

Una vez instalado debemos borrar la capeta *www/install* si no no podremos acceder administrador.

# Instalacion (en este caso no tiene. Se debe instalar desde 0)

Ya tiene instalado un prestashop por defecto. Si queremos usar este hacemos lo siguiente. Si lo queremos instalar desde
cero hacemos los pasos de la Instalacion desde 0

Nos ubicamos en el directorio y ejecutamos:
`docker-compose up -d`

Debemos cambiar la ip del contenedor de la base de datos. Usamos el comando:
`docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container_id`

Y la ip que nos de la cambiamos en:
_www/app/config/parameters.php_

Pass, user y DB serán:

`prestashop`
