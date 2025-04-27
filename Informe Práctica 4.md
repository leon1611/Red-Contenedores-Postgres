# Practica # contenedores mysql y phMyAdmin y red de Docker
## 1. Titulo
**Practica No 4**: Creación de Contenedores mysql y de pgAdmin para conectarlos a través de una red de Docker.
## 2. Tiempo de duración
Se utilizo un tiempo de 1 hora y media para la realización de esta práctica
## 3. Fundamentos:

En esta práctica se aprenderán los conceptos básicos sobre la creación y configuración de contenedores Docker para gestionar una base de datos MySQL y una interfaz gráfica phpMyAdmin. Docker permite crear contenedores aislados para ejecutar aplicaciones, y en este caso, se utilizarán para desplegar y administrar MySQL y phpMyAdmin en un entorno controlado.

Durante la práctica, se aprenderán los siguientes conceptos clave:

- **Contenedores Docker:** Un contenedor es un entorno aislado que ejecuta una aplicación junto con sus dependencias.
    
- **Redes Docker:** Las redes permiten la comunicación entre contenedores, asegurando que las aplicaciones puedan interactuar de manera segura y eficiente.
    
- **phpMyAdmin:** Es una herramienta de administración de bases de datos MySQL a través de una interfaz web, utilizada comúnmente para administrar bases de datos de manera fácil..

Se utilizaron los siguientes comandos para crear y configurar los contenedores y la red:

- **`docker network create`**: Para crear una red personalizada.
- **`docker run -d --name pgadmin -p 8090:80 -e PGADMIN_DEFAULT_EMAIL=mllituma@sudamericano.edu.ec -e PGADMIN_DEFAULT_PASSWORD=1611 dpage/pgadmin4`**: Para crear un contenedor de pgAdmin.
- **`docker run -d --name dbpsql -e POSTGRES_PASSWORD=1611 -p 5432:5432 postgres`**: Para crear un contenedor de Postgres.

## 4. Conocimientos previos.
   
Para realizar esta práctica, es necesario tener conocimientos básicos sobre **Docker**, como la creación y gestión de contenedores y redes, así como la manipulación de bases de datos MySQL.

PostgreSQL es un sistema de base de datos relacional de código abierto, altamente robusto y confiable, diseñado para manejar cargas de trabajo de datos complejas. Originado en 1986 en la Universidad de California en Berkeley como parte del proyecto POSTGRADOS, ha mantenido un desarrollo activo durante más de 35 años. Su arquitectura probada, la integridad de los datos, su extensibilidad y el respaldo de una comunidad de código abierto lo han consolidado como una opción preferida para muchas organizaciones. PostgreSQL es compatible con todos los sistemas operativos principales, cumple con el modelo ACID desde 2001, y ofrece extensiones potentes como PostGIS para bases de datos geoespaciales. Su facilidad de uso y versatilidad lo hacen ideal para almacenar datos de manera segura y eficiente, según PostgreSQL Global Development Group. (2025).

PgAdmin 4 nos permite acceder a todas las funcionalidades de la base de datos, consulta, manipulación y gestión de datos, incluso opciones avanzadas como manipulación del motor de replicación Slony-I. De acuerdo con pgAdmin Development Team. (2025), pgAdmin se puede implementar como una aplicación web configurando la aplicación para que se ejecute en modo servidor. Se puede consultar la implementación del servidor sobre cómo ejecutar pgAdmin en modo servidor.

## 5. Objetivos a alcanzar
   
- Crear un contenedor para MySQL con credenciales personalizadas.
    
- Crear un contenedor para phpMyAdmin y configurarlo para conectarse a MySQL.
    
- Establecer una red Docker personalizada para la comunicación entre los contenedores.
    
- Crear una base de datos de prueba desde phpMyAdmin.
  
## 6. Equipo necesario:
  
- Computador con sistema operativo **MacOS:** 13.7.1 
- **Procesador:** 2,3 GHz Intel Core i5
- **Memoria:** 8 GB 
- Conexión a Internet para el material de apoyo

## 7. Material de apoyo.
   
- Documentación oficial de Docker
- Videos y foros de la comunidad Docker
- Videos Material de Apoyo (EVA)
- CheatSheet redes de contenedores en Notion
  
## 8. Procedimiento

**Paso 1:** Verificación de la versión de Docker y descarga de la imagen oficial de PostgreSQL.

Figura 1. Comando **"docker -v "**. 

<img width="877" alt="1" src="https://github.com/user-attachments/assets/99aecc76-4b27-4497-a28b-28b32f6106c4" />



**Paso 2:** Creamos el contenedor de PostgreSQL (`dbsql`) ejecutando el siguiente comando para crear el contenedor y exponerlo en el puerto 5432.

Figura 2. Comando **"docker run -d --name dbsql -e"**.

<img width="877" alt="1" src="https://github.com/user-attachments/assets/99aecc76-4b27-4497-a28b-28b32f6106c4" />

<img width="929" alt="3" src="https://github.com/user-attachments/assets/142b28c9-b9ff-4735-89d7-f52c81139400" />



**Paso 3:** Creamos el contenedor de PGAdmin (`pgadmin`) y lo expondremos en el puerto 8090.

Figura 3. Comando **"docker run -d --name pgadmin -p 8090:80 -e "**. 

<img width="909" alt="2" src="https://github.com/user-attachments/assets/989cd011-c484-4f3c-b221-bf7625f25274" />

<img width="1045" alt="5" src="https://github.com/user-attachments/assets/d8056f63-a906-4d39-9e39-0cb03bb41e52" />

<img width="1044" alt="6" src="https://github.com/user-attachments/assets/ddd488a6-dbf4-4a7b-aef3-41c4cce9796c" />


**Paso 4:** Crear una red personalizada llamada `redleo` 

Figura 4. Comando **"docker network create --attachable  "**. 

<img width="550" alt="4" src="https://github.com/user-attachments/assets/32df07c1-05bc-47ba-b299-2b17a9b672d7" />



**Paso 5:** Conectar los contenedores de PostgreSQL y PGAdmin a la red `redleo`.

Figura 5. Comando **"docker network connect "**. 

<img width="547" alt="11" src="https://github.com/user-attachments/assets/9e8482d1-8233-4cda-9226-8c16b821075a" />

<img width="1083" alt="7" src="https://github.com/user-attachments/assets/f34ecc31-6b57-41a9-8978-e30a0cac6a00" />



**Paso 6:** Verificar los contenedores conectados a la red. Este comando muestra las IPs asignadas a cada contenedor.

Figura 6. Comando **"docker inspect"**. 

<img width="916" alt="9" src="https://github.com/user-attachments/assets/5cf0b0a0-debf-4b91-8d52-8c8e68998a1c" />


**Paso 7:** Crear una base de datos en phpMyAdmin.

Figura 7. Nombre de base de datos **"appweb "**. 

<img width="1082" alt="8" src="https://github.com/user-attachments/assets/7cb7a5d5-16c6-452e-a5e5-570630fa18c8" />

<img width="1066" alt="10" src="https://github.com/user-attachments/assets/87c12b74-cbb8-4073-8ad9-905fc643c130" />



## 9. Resultados esperados:
    
La práctica me permitió crear y gestionar contenedores de **PostgreSQL** y **PGAdmin** utilizando Docker. A través de este proceso, pude familiarizarme con el uso de Docker para implementar bases de datos y aplicaciones de administración de bases de datos de manera eficiente, sin necesidad de realizar configuraciones locales complicadas.

Después de completar todos los pasos, logré levantar dos contenedores: uno para **PostgreSQL** en el puerto 5432 y otro para **PGAdmin** en el puerto 8090. Con esto, pude acceder a PGAdmin a través de mi navegador e ingresar con las credenciales proporcionadas (email: `mllituma@sudamericano.edu.ec`, password: `1611`), lo que me permitió gestionar las bases de datos de manera intuitiva y visual.

Además, la creación de una red Docker personalizada y la conexión de los contenedores a esa red me permitió asegurar que ambos contenedores pudieran comunicarse entre sí sin problemas. Este proceso también me ayudó a entender cómo funcionan las redes en Docker y cómo manejar conexiones entre contenedores de manera aislada.

En resumen, esta práctica fue muy útil para adquirir habilidades en la configuración y manejo de bases de datos dentro de contenedores Docker, y cómo acceder a herramientas como PGAdmin para administrar esos datos de manera eficiente y controlada.

<img width="1045" alt="5" src="https://github.com/user-attachments/assets/57b485cc-835f-4392-9b40-5e10b3d50025" />

<img width="1044" alt="6" src="https://github.com/user-attachments/assets/09d3fb30-16ac-4b27-920c-0bfdaa1e6f77" />

<img width="1066" alt="10" src="https://github.com/user-attachments/assets/6100b52a-fc60-434c-8f71-e647c2d0ff47" />

## 10. Bibliografía

- pgAdmin Development Team. (2025). _pgAdmin – PostgreSQL Tools_. Recuperado de [https://www.pgadmin.org/](https://www.pgadmin.org/)

- PostgreSQL Global Development Group. (2025). _PostgreSQL: A powerful, open-source object-relational database system_. Recuperado de [https://www.postgresql.org](https://www.postgresql.org)
