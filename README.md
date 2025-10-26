\# 🧪 Práctica No. 3: Crear volúmenes para persistir base de datos con PostgreSQL



\## 👨‍💻 Datos del estudiante

\*\*Nombre:\*\* Carlos Sudamericano  

\*\*Carrera:\*\* Ingeniería en Sistemas  

\*\*Fecha:\*\* 25 de octubre de 2025  



---



\## 🎯 Objetivo

Comprobar la diferencia entre el uso de contenedores PostgreSQL con y sin volúmenes en Docker, demostrando la persistencia de datos.



---



\## 🧩 Parte 1: Base de datos sin volumen



\### 🔹 Creación del contenedor

```bash

docker run --name server\_db1 -e POSTGRES\_PASSWORD=1234 -d -p 5432:5432 postgres

```



\### 🔹 Operaciones realizadas

\* Creación de la base de datos `test`.

\* Creación de la tabla `customer`.

\* Inserción de registros.

\* Eliminación del contenedor.

\* Verificación de pérdida de datos.



\### ✅ Resultado

Los datos se eliminaron al remover el contenedor.



---



\## 🧩 Parte 2: Base de datos con volumen



\### 🔹 Crear volumen

```bash

docker volume create pgdata

```



\### 🔹 Crear contenedor con volumen

```bash

docker run --name server\_db2 -e POSTGRES\_PASSWORD=1234 -d -p 5433:5432 -v pgdata:/var/lib/postgresql/data postgres

```



\### 🔹 Operaciones realizadas

\* Creación de la base de datos `test`.

\* Creación de la tabla `customer`.

\* Inserción de registros.

\* Eliminación del contenedor.

\* Recreación del contenedor con el mismo volumen.



\### ✅ Resultado

Los datos persistieron correctamente gracias al volumen `pgdata`.



---



\## 📘 Conclusiones

\* Los volúmenes permiten mantener los datos aunque se elimine el contenedor.

\* Sin volúmenes, los datos se pierden al eliminar el contenedor.

\* Docker Volumes son esenciales en entornos de producción para persistir información.



---



\## 📎 Referencias

\* \[Documentación oficial de Docker Volumes](https://docs.docker.com/storage/volumes/)

\* \[PostgreSQL Docker Hub](https://hub.docker.com/\_/postgres)



