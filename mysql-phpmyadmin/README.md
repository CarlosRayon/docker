# Entorno mysql y phpmyadmin

## Archivos

- El archivo _docker-compose.yml_ define los contenedores.
- En el directorio mysql_data se guardaran todas las configuraciones de mysql.

## Instalación

- Revisamos que los puertos correspondiente este libres.

- Ajustamos los usuarios y password a nuestro gusto.
  - Descomentamos si queremos uno usuario y una base datos creada por defecto.

-Ejecutamos:
`docker-compose up -d`

## Accesos

### Phpmyadmin

- Para acceder a phpmyadmin lo hacemos mediante la url _localhost:{puerto definido en .yml}_
- El usuario sera _root_ y el password el definido en el .yml

### Mysql

- Podemos acceder a mysql ejecutando un bash en el contenedor:

`docker exec -it {id || nombre contenedor} bash`

- Después ejecutamos:

`mysql -uroot -p`

Se nos pedirá un password que sera el definido en el .yml

### Acceso por ip

Para establecer un conexión a DB en el host debemos poner la ip del contenedor.
Para saber la mismo usamos:

`docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nombre_contenedor_id_mysql_container`
