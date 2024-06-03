# Variables de Entorno
### ¿Qué son las variables de entorno
Las variables de entorno en contenedores Docker son un mecanismo para configurar el comportamiento de las aplicaciones que se ejecutan dentro de los contenedores. 
Estas variables proporcionan una manera flexible de pasar información a las aplicaciones sin necesidad de modificar el código fuente. 
Pueden ser usadas para configurar aspectos como las credenciales de acceso, configuraciones de red, parámetros específicos de la aplicación, entre otros.

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>

```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

docker run -d --name main -e username=cesar96lan -e role=admin nginx:alpine

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR

![image](https://github.com/Cesar96LAN/2024A-ISWD633-GR1/assets/119013340/0e2714ed-5652-49ee-bde0-055c835a1515)


### Crear un contenedor con mysql:8 , mapear todos los puertos

docker run -d --name main -p 3306:3306 -e MYSQL_ROOT_PASSWORD=rootpassword -e MYSQL_DATABASE=mydatabase -e MYSQL_USER=myuser -e MYSQL_PASSWORD=mypassword mysql:8


### ¿El contenedor se está ejecutando?
no

### Identificar el problema
Problemas con las variables de entorno

### Eliminar el contenedor creado con mysql:8 

docker stop main


### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

Previo a esto es necesario crear el archivo y colocar las variables en un archivo, **.env** se ha convertido en una convención estándar, pero también es posible usar cualquier extensión como **.txt**.
```
docker run -d --name <nombre contenedor> --env-file=<nombreArchivo>.<extensión> <nombre imagen>
```
**Considerar**
Es necesario especificar la ruta absoluta del archivo si este se encuentra en una ubicación diferente a la que estás ejecutando el comando docker run.

### Crear un contenedor con mysql:8 , mapear todos los puertos y configurar las variables de entorno mediante un archivo

docker run -d --name main --env-file="D:\DOCUMENTOS EPN\6. SEXTO SEMESTRE\CONSTRUCCION Y EVOLUCION DE SOFTWARE\Práctica 2\variables.txt" -p 3306:3306 mysql:8

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR 

![image](https://github.com/Cesar96LAN/2024A-ISWD633-GR1/assets/119013340/8861f569-4764-40aa-9bf2-a8ed6a2c7999)


### ¿Qué bases de datos existen en el contenedor creado?

information_schema: Esta base de datos contiene metadatos sobre las bases de datos y las tablas del servidor MySQL.

performance_schema: Esta base de datos contiene instrumentación de rendimiento interna de MySQL.

sys: Esta base de datos contiene vistas que muestran información del sistema utilizando el sistema de rendimiento.
