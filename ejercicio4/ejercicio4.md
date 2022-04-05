#### María Rodriguez Arango

##### Ejercicio 4 - imagen con Dockerfile



Creamos una carpeta : dockerweb

![](ejercicio4.assets/1.PNG)

Nos descargamos una plantilla de la página  HTML5UP ,la personalizamos y guardamos dentro de la carpeta creada anteriormente.

Creamos el archivo plano Dockerfile y también lo guardamos dentro de la carpeta DockerWeb

![](/ejercicio4.assets/3.PNG)

![](/ejercicio4.assets/2.PNG)



 Construimos la imagen

```
docker build -t ejercicio4
```

![](/ejercicio4.assets/4.PNG)



Creamos el contenedor a través de la imagen anterior

```
docker run -d -p 80:80 ejercicio4
```

![](/ejercicio4.assets/5.PNG)



Mostramos el acceso al navegador con el sitio servido

![](/ejercicio4.assets/6.PNG)



Subimos la imagen a nuestra cuenta Docker Hub:

Iniciamos sesión en Docker Hub

```
docker login
```

![](/ejercicio4.assets/7.PNG)

Subimos la imagen

```
docker tag ejercicio4 mariarodriguezarango/ejercicio4
```

```
docker push mariarodriguezarango/ejercicio4
```

![](/ejercicio4.assets/8.PNG)

Comprobamos que la imagen esta subida

![](/ejercicio4.assets/9.PNG)