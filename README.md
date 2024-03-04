# vmoralesv-st0263
Repositorio de retos y proyectos de Tópicos Especiales en Telemática 


# Info de la materia: ST0263 Tópicos Especiales en Telemática
#
# Estudiante(s): Valentina Morales Villada, vmoralesv@eafit.edu.co
#
# Profesor: Edwin Montoya, emontoya@eafit.edu.co
#

# Reto 1 y 2 
#
# 1. Breve descripción de la actividad
 Diseño e implementación de un sistema con arquitectura P2P, en el cual cada nodo tiene unos microservicios que soportan un sistema de compartición de archivos distribuido y descentralizado.
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

- Distribución modular: Gracias a esto
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
## opcionalmente - si quiere mostrar resultados o pantallazos 

# 4. Descripción del ambiente de EJECUCIÓN (en producción) lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.

# IP o nombres de dominio en nube o en la máquina servidor.

## descripción y como se configura los parámetros del proyecto (ej: ip, puertos, conexión a bases de datos, variables de ambiente, parámetros, etc)

## como se lanza el servidor.

## una mini guia de como un usuario utilizaría el software o la aplicación

## opcionalmente - si quiere mostrar resultados o pantallazos 

# 5. otra información que considere relevante para esta actividad.

# referencias:
<debemos siempre reconocer los créditos de partes del código que reutilizaremos, así como referencias a youtube, o referencias bibliográficas utilizadas para desarrollar el proyecto o la actividad>
## sitio1-url 
## sitio2-url
## url de donde tomo info para desarrollar este proyecto
