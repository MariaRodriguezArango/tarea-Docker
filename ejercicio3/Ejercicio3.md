





#### María Rodriguez Arango

##### Ejercicio 3 Redes

Creamos una red bridge "redbd"

```
docker network create redbd
```

listamos para ver que esta creada

```
docker network ls
```

![](Ejercicio3.assets/0.PNG)

Creamos un contenedor con una imagen de maridadb que esté en la red creada antes

```
docker run -d --name bbdd --network=redbd -v /home/maria/redes:/var/lib/mysql -e MARIADB_ROOT_PASSWORD=temporal -e MARIADB_DATABASE=maria -p 3306:3306 mariadb
```

![](Ejercicio3.assets/1.PNG)

Creamos un contenedor con Adminer que se pueda conectar al contenedor de la BD

```
docker run --name adminer --link bbdd:db --network redbd -p 8080:8080 -d adminer
```

Comprobamos que contenedores se esta ejecutando

```
docker ps
```

![](Ejercicio3.assets/2.PNG)

Accedemos a la interfaz de Adminer desde el navegador

![](Ejercicio3.assets/3.PNG)



Nos conectamos a la base de datos

![](Ejercicio3.assets/4.PNG)

Creamos una base de datos desde la interfaz de Adminer

![](Ejercicio3.assets/5.PNG)

Comprobamos por comandos que la base de datos MariaArango se ha creado correctamente

```
docker exec -it bbdd bash
```

dentro del contenedor de la base de datos  nos conectamos a la base de datos

```
mysql -u root -p
```

una vez comprobado que esta creada la base de datos salimos primero de la base de datos y después del contenedor

```
exit
```

![](Ejercicio3.assets/7.PNG)

Borramos los contenedores, la red y los volúmenes utilizados:

primero paramos los contenedores

```
docker stop bbdd
```

```
docker stop adminer
```

borramos los contenedores

```
docker container rm bbdd adminer
```

borramos la red

```
docker network rm redbd
```

borramos los volúmenes

```
docker volume prune
```

Comprobamos que todo se ha eliminado todo:

listamos los volúmenes, redes y contenedores

```
docker volume ls
```

```
docker network ls
```

```
docker ps -a
```

![](Ejercicio3.assets/8.PNG)