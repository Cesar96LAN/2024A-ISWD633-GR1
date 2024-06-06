### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:11.21-alpine3.17

docker run --name mi-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres:11.21-alpine3.17

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4

docker run --name mi-pgadmin -p 80:80 -e PGADMIN_DEFAULT_EMAIL=miemail@example.com -e PGADMIN_DEFAULT_PASSWORD=mipassword -d dpage/pgadmin4


La figura presenta el esquema creado en donde los puertos son:
- a: (completar con el valor)
- b: (completar con el valor)
- c: (completar con el valor)

![Imagen](imagenes/esquema-ejercicio3.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.
#CAPTURA DEL LOGIN

![image](https://github.com/Cesar96LAN/2024A-ISWD633-GR1/assets/119013340/4dfa2a20-c8ba-4343-89da-41677ca53090)


### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.

-- Crear la base de datos "info"
CREATE DATABASE info;

-- Conectarse a la base de datos "info"
\c info;

-- Crear la tabla "personas"
CREATE TABLE personas (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(100)
);

-- Agregar registros
INSERT INTO personas (nombre) VALUES ('Juan'),('María'),('Cesar');


## Desde el servidor postgresl
### Acceder al servidor

psql -U postgres


### Conectarse a la base de datos info

\c info;


### Realizar un select *from personas
# CAPTURA DE PANTALLA DEL RESULTADO
![image](https://github.com/Cesar96LAN/2024A-ISWD633-GR1/assets/119013340/34b4297a-b137-45f2-b038-97eed96a09f5)
