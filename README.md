# info de la materia: ST0263-TOPICOS ESPECIALES EN TELEMATICA

# Estudiante(s): Valentina Morales Villada, vmoralesv@eafit.edu.co

# Profesor: Edwin Nelson Montoya Munera, emontoya@eafit.edu.co


# Nombre del proyecto: Reto 1 y 2
#
# 1. Breve descripción de la actividad
#
<texto descriptivo>

## 1.1. Que aspectos cumplió o desarrolló de la actividad propuesta por el profesor (requerimientos funcionales y no funcionales)
### Requisitos funcionales

- Autenticación de peers
- Consulta de recursos 
- Servicio de transferencia de archivos
- Servicio de cambio de moneda

### Requisitos no funcionales

- Escalabilidad
- Rendimiento
- Mantenibilidad
- Disponibilidad

## 1.2. Que aspectos NO cumplió o desarrolló de la actividad propuesta por el profesor (requerimientos funcionales y no funcionales)


# 2. información general de diseño de alto nivel, arquitectura, patrones, mejores prácticas utilizadas.

### Mejores Prácticas

- Distribución modular: 
- Escalabilidad horizontal: Esto nos permite agregar tantos peers como queramos fácilmente.
- Gestión de configuraciones: Toda la información sensible como ips o puertos quedó guardada en un archivo de configuración y no quemada dentro del código.
- Tolerancia a fallos: 

# 3. Descripción del ambiente de desarrollo y técnico: lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.

## como se compila y ejecuta.

```
docker compose up 
```

## detalles del desarrollo.

El servidor central fue desarrollado en Golang y tanto el PCliente como el PServidor fueron desarrollados en Python. Se desplegaron tres instancias EC2 de AWS, una para el servidor central (central-server), y dos para peers (peer1 y peer2).

## detalles técnicos

Endpoints: 

## descripción y como se configura los parámetros del proyecto (ej: ip, puertos, conexión a bases de datos, variables de ambiente, parámetros, etc)
## opcional - detalles de la organización del código por carpetas o descripción de algún archivo. (ESTRUCTURA DE DIRECTORIOS Y ARCHIVOS IMPORTANTE DEL PROYECTO, comando 'tree' de linux)
## 
