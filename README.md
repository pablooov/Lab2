# Lab2
# Guía de Instalación y Configuración: Neo4j y Cassandra

Este repositorio documenta el proceso de instalación y configuración de **Neo4j Desktop** y **Apache Cassandra** utilizando Docker. 

---

## Índice

1. [Instalación de Neo4j](#instalación-de-neo4j)
2. [Instalación de Cassandra con Docker](#instalación-de-cassandra-con-docker)
3. [Pruebas](#pruebas)
4. [Recursos Adicionales](#recursos-adicionales)

---

## Instalación de Neo4j

Sigue los pasos a continuación para instalar Neo4j Desktop:

1. **Descargar Neo4j Desktop**:
   - Abre tu navegador web y dirígete al sitio oficial: [https://neo4j.com](https://neo4j.com).
   - Haz clic en el enlace de descarga de Neo4j Desktop.
   - Selecciona la versión correspondiente a tu sistema operativo (en este caso, Windows) y haz clic en el botón "Download".
   - Llena el formulario de registro con los datos solicitados y haz clic en "Download Desktop".

2. **Instalar Neo4j Desktop**:
   - Abre el archivo descargado (un instalador `.exe`).
   - Sigue los pasos del asistente de instalación:
     1. Acepta los términos y condiciones.
     2. Selecciona el directorio donde deseas instalar Neo4j Desktop.
     3. Haz clic en "Siguiente" hasta completar la instalación.
     4. Asegúrate de marcar la opción "Ejecutar Neo4j Desktop" antes de finalizar.

3. **Configurar Neo4j Desktop**:
   - Al iniciar Neo4j Desktop, el programa verificará los requisitos del sistema y configurará el entorno de ejecución.
   - Espera a que termine la preparación de las aplicaciones relacionadas (Graph Apps) antes de continuar.

---

## Instalación de Cassandra con Docker

Sigue los pasos para instalar y configurar Apache Cassandra utilizando Docker:

1. **Instalar Docker Desktop**:
   - Ingresa al sitio oficial: [https://app.docker.com](https://app.docker.com) y busca el apartado "Docker Desktop".
   - Descarga la aplicación para tu sistema operativo e instálala siguiendo los pasos del asistente.

2. **Habilitar contenedores en Windows**:
   - Abre el **Símbolo del Sistema** y ejecuta el siguiente comando para habilitar el soporte de contenedores en Windows:
     ```bash
     wsl --install
     ```

3. **Crear una imagen de Cassandra**:
   - Una vez instalado Docker, abre Docker Desktop y crea una imagen para Cassandra.

4. **Crear un contenedor para Cassandra**:
   - Usa el siguiente comando para crear el contenedor y asignarle un nombre (en este caso, `Lab2`):
     ```bash
     docker run --name Lab2 -d cassandra
     ```

5. **Acceder al contenedor de Cassandra**:
   - Abre una terminal y ejecuta el siguiente comando para entrar en el contenedor:
     ```bash
     docker exec -it Lab2 bash
     ```

6. **Iniciar cqlsh para trabajar con Cassandra**:
   - Dentro del contenedor, ejecuta:
     ```bash
     cqlsh
     ```

---

## Pruebas

### Probar Neo4j
1. Abre Neo4j Desktop y crea un nuevo proyecto.
2. Inicia una base de datos y accede al navegador web en `http://localhost:7474`.
3. Usa las credenciales predeterminadas:
   - Usuario: `neo4j`
   - Contraseña: `neo4j`.

### Probar Cassandra
1. Conéctate al contenedor con el comando `docker exec -it Lab2 bash`.
2. Usa `cqlsh` para ejecutar comandos, por ejemplo:
   ```sql
   CREATE KEYSPACE test WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 1};
