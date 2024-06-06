## Esquema para el ejercicio
![Imagen](imagenes/esnquema-ejercicio5.PNG)

### Crear la red

docker network create net-wp

### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias

docker run -d --name mysql --network net-wp -e MYSQL_ROOT_PASSWORD=my-secret-pw -e MYSQL_DATABASE=wordpress -e MYSQL_USER=wpuser -e MYSQL_PASSWORD=wppassword mysql:8


### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias

docker run -d --name wordpress --network net-wp -e WORDPRESS_DB_HOST=mysql:3306 -e WORDPRESS_DB_NAME=wordpress -e WORDPRESS_DB_USER=wpuser -e WORDPRESS_DB_PASSWORD=wppassword -p 9300:80 wordpress


De acuerdo con el trabajo realizado, en la el esquema de ejercicio el puerto a es 9300

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
![image](https://github.com/Cesar96LAN/2024A-ISWD633-GR1/assets/119013340/a20c9c61-6d8c-4539-946f-f25ef8f86696)


Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

![image](https://github.com/Cesar96LAN/2024A-ISWD633-GR1/assets/119013340/14c72683-3b75-4186-a5bb-3fe7426dd9df)


### Eliminar el contenedor wordpress

docker rm -f wordpress

### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

docker run -d --name wordpress --network net-wp -e WORDPRESS_DB_HOST=mysql:3306 -e WORDPRESS_DB_NAME=wordpress -e WORDPRESS_DB_USER=wpuser -e WORDPRESS_DB_PASSWORD=wppassword -p 9300:80 wordpress


### ¿Qué ha sucedido, qué puede observar?

Una pantalla en blanco





