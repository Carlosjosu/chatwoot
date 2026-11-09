# Despliegue de Chatwoot en AWS — Proyecto ABP

## 1. Descripción

Este repositorio documenta el proyecto ABP del Grupo 05 de la asignatura Computación en la Nube de la Universidad Nacional de Loja. El objetivo es desplegar la plataforma de atención al cliente Chatwoot utilizando servicios de Amazon Web Services (AWS).

El proyecto incluye una propuesta de arquitectura de red y una prueba de concepto mediante una instancia Amazon EC2.

## 2. Repositorio de origen

La aplicación Chatwoot se basa en el proyecto oficial de código abierto:

https://github.com/chatwoot/chatwoot

Este repositorio es un fork del proyecto original. Las configuraciones y evidencias específicas del proyecto ABP se documentan por separado.

## 3. Servicios y tecnologías utilizados

- **Amazon EC2:** instancia virtual para ejecutar la aplicación.
- **Amazon VPC:** red virtual donde se ubica la instancia.
- **Security Groups:** reglas de seguridad para controlar el acceso.
- **Ubuntu Server 24.04 LTS:** sistema operativo del servidor.
- **Docker Compose:** herramienta para gestionar los contenedores.
- **PostgreSQL:** base de datos de Chatwoot.
- **Redis:** servicio de apoyo para tareas y comunicación de la aplicación.
- **Nginx:** servidor web y proxy inverso.

## 4. Arquitectura implementada

La prueba de concepto utiliza una instancia EC2 en la región `us-east-2` (Ohio). Dentro del servidor se ejecutan Chatwoot, PostgreSQL, Redis y Sidekiq mediante Docker Compose. Nginx recibe las solicitudes web y las dirige hacia la aplicación.

La instalación se realizó en el directorio `/opt/chatwoot`.

## 5. Arquitectura propuesta

El diseño del proyecto contempla una VPC con seis subredes distribuidas en dos zonas de disponibilidad, además de un balanceador de carga, NAT Gateways, Amazon RDS, Amazon ElastiCache y Amazon S3.

Estos componentes pertenecen a la arquitectura propuesta y no deben confundirse con los recursos desplegados en la prueba de concepto.

## 6. Comandos principales de operación

Consultar el estado de los contenedores:

```bash
cd /opt/chatwoot
sudo docker compose -f docker-compose.production.yaml ps
```

Iniciar los servicios:

```bash
sudo docker compose -f docker-compose.production.yaml up -d
```

Detener los contenedores sin eliminar sus datos:

```bash
sudo docker compose -f docker-compose.production.yaml stop
```

Consultar los registros:

```bash
sudo docker compose -f docker-compose.production.yaml logs --tail=50
```

## 7. Seguridad

Los archivos con contraseñas, tokens, claves privadas y otras credenciales no forman parte de este repositorio. La configuración de producción requiere completar y validar el acceso HTTPS antes de utilizar información real de clientes.

## 8. Evidencias y entregables

- Informe del proyecto ABP en PDF.
- Diagrama de arquitectura de red.
- Capturas de la instancia EC2 y de las reglas de seguridad.
- Evidencia de Chatwoot funcionando en el navegador.
- Enlace al video demostrativo grupal: pendiente de publicación.

## 9. Integrantes

- Jorge Luzuriaga
- Emilio Jaramillo
- Carlos Granda
- Andrés Tapia
