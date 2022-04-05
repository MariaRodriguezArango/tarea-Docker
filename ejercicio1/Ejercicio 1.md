#### María Rodriguez Arango 

[TOC]



#### Ejercicio 1 - trabajo con imágenes

##### Servidor web

Arrancamos un contenedor que ejecute una instancia de la imagen php:7.4-apache, que se llame web y que sea accesible desde un navegador en el puerto 8000.

```
docker run -d --name web -v /home/maria/web:/var/www/html -p 8000:80 php:7.4-apache
```

![](./imagenes/servidor%20web/1.PNG)

comprobamos que el contenedor esta corriendo:

```
docker ps -a
```

![](Ejercicio%201%20-%20trabajo%20con%20im%C3%A1genes.assets/2.PNG)

Mostramos en el navegador el index.html creado anteriormente

![](Ejercicio%201%20-%20trabajo%20con%20im%C3%A1genes.assets/3.PNG)

Mostramos en el navegador la salida del archivo mes.php

![](Ejercicio%201%20-%20trabajo%20con%20im%C3%A1genes.assets/5.PNG)



Mostramos el tamaño del contendor una vez creado los dos ficheros

```
docker container ls -s
```

![](Ejercicio%201%20-%20trabajo%20con%20im%C3%A1genes.assets/7.PNG)



Paramos el contenedor

```
docker stop web
```

Borramos el contenedor

```
docker container rm web
```

Comprobamos que se haya borrado

```
docker ps -a
```

![](Ejercicio%201%20-%20trabajo%20con%20im%C3%A1genes.assets/6-16483840173412.PNG)

##### Servidor de base de datos

Arrancamos un contenedor que se llame bbdd y que ejecute una instancia de la imagen mariadb

```
docker run -d --name bbdd --env MARIADB_USER=invitado --env MARIADB_PASSWORD=invitado --env MARIADB_ROOT_PASSWORD=root -env MARIADB_DATABASE=prueba mariadb:latest
```

![](Ejercicio%201%20-%20trabajo%20con%20im%C3%A1genes.assets/1-16483840331013.PNG)



Nos conectamos al contenedor con el usuario y la contraseña 

```
docker exec -it bbdd mysql -u invitado -p 
```

Comprobamos que se ha creado la base de datos

```
show databases;
```

![](Ejercicio%201%20-%20trabajo%20con%20im%C3%A1genes.assets/2-16483840404214.PNG)

Comprobamos que no se puede borrar la imagen mariadb mientras el contenedor bbdd está creado

![](Ejercicio%201%20-%20trabajo%20con%20im%C3%A1genes.assets/3-16483842772955.PNG)



Mostramos la imágenes que hay en el registro local

![](Ejercicio%201%20-%20trabajo%20con%20im%C3%A1genes.assets/4.PNG)



Eliminamos el contenedor de bases de datos

```
docker rm bbdd
```

y compramos que no hay contenedores creados

```
docker ps -a
```

![](Ejercicio%201%20-%20trabajo%20con%20im%C3%A1genes.assets/5-16483844206656.PNG)
