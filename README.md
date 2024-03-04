# Info de la materia: ST0263-TOPICOS ESPECIALES EN TELEMATICA

# Estudiante(s): Valentina Morales Villada, vmoralesv@eafit.edu.co

# Profesor: Edwin Nelson Montoya Munera, emontoya@eafit.edu.co


# Nombre del proyecto: Reto 1 y 2

# 1. Breve descripción de la actividad

Red P2P no estructurada basada en servidor central. En la cual cada proceso tiene uno o más microservicios que componen un sistema de compartición de archivos distribuido y descentralizado.  

## 1.1. Que aspectos cumplió o desarrolló de la actividad propuesta por el profesor (requerimientos funcionales y no funcionales)
### Requisitos funcionales

- Autenticación de peers (login, logout)
- Consulta de recursos (sendIndex)
- Servicio de transferencia de archivos (download, upload)
- Servicio de cambio de moneda (currency exchange)

### Requisitos no funcionales

- Escalabilidad
- Rendimiento
- Mantenibilidad
- Disponibilidad

## 1.2. Que aspectos NO cumplió o desarrolló de la actividad propuesta por el profesor (requerimientos funcionales y no funcionales)

En general se pudo cumplir con lo propuesto en el enunciado del proyecto. Tal vez pudo faltar un mejor manejo de errores desde el servidor central.

# 2. Información general de diseño de alto nivel, arquitectura, patrones, mejores prácticas utilizadas.

![image](https://github.com/vaalmo/vmoralesv-st0263/assets/83479274/722f3c68-c58b-4f1e-9f2f-6de397383388)


### Mejores Prácticas

- Distribución modular: El sistema se organizó de tal manera que todos los servicios y módulos de clientes y server grpc, tuvieran su propio archivo y carpeta, para que sea más fácil localizar los archivos a la hora de hacer cambios.
- Escalabilidad horizontal: Esto nos permite agregar tantos peers como queramos fácilmente.
- Gestión de configuraciones: Toda la información sensible como ips o puertos quedó guardada en un archivo de configuración y no quemada dentro del código.
- Tolerancia a fallos: Esto ayudó a que cuando surgieran errores, no se muriera el código, sino que mandara mensaje de error y pudiera seguir corriendo.

# 3. Descripción del ambiente de desarrollo y técnico: lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.

## Como se compila y ejecuta.

Primero se deben crear las instancias correpondientes en AWS, de central-server, peer1 y peer2. Preferiblemente con ip's elásticas.

Una vez ya creadas, se debe acceder a cada una de ellas remotamente mediante SSH y se clona el repositorio con el proyecto. Además se debe instalar docker, para luego poder correr los contenedores.

Se realizan los cambios en el _docker-compose.yml_ de las instancias de los peers, para especificar el puerto, y en los archivos .env para espcificar las ip's expuestas y la del servidor central. Adicionalmente se debe modificar el archivo .env del servidor central, ya que en este se especifica el puerto por donde este va a estar escuchando.

Para editar el docker-compose.yml en las instancias de peer1 y peer2
```
vi docker-compose.yml
```

Para editar el archivo .env (en central_server, peer1 y peer2)
```
touch .env
vi .env
```

Luego de crear los archivos de configuración, queda hacer _build_ y correr la parte del contenedor específica para cada instancia.

Para central-server:
```
docker compose build 
docker compose up
```

Para el PServer de peer1 y peer2: 

```
docker compose build
docker compose up pserver
```

Para el PClient de peer1 y peer2:

```
docker compose run -i pclient
```

Con esto ya todas las instancias están corriendo y se pueden realizar las pruebas por medio del CLI de los PClients de los peers. 


## Detalles del desarrollo.

El servidor central fue desarrollado en Golang y tanto el PCliente como el PServidor fueron desarrollados en Python. Se desplegaron tres instancias EC2 de AWS, una para el servidor central (central-server), y dos para peers (peer1 y peer2).

## Detalles técnicos

Endpoints:  

- /login
- /logout
- /sendIndex
- /indexTable
- /query
- /getPeerUploading



## Descripción y como se configura los parámetros del proyecto (ej: ip, puertos, conexión a bases de datos, variables de ambiente, parámetros, etc)

Como ya fue mencionado las ip's se configuran en los archivos de _docker-compose.yml_ y en los archivos _.env_, lo mismo para las variables de entorno. En cuanto a bases de datos, no fueron utilizadas para este proyecto. 


## Opcional - Detalles de la organización del código por carpetas o descripción de algún archivo.

![image](https://github.com/vaalmo/vmoralesv-st0263/assets/83479274/5dc0bff4-8142-4718-bbd6-6811be670b2d)

![image](https://github.com/vaalmo/vmoralesv-st0263/assets/83479274/c7463716-e39c-4cdb-8226-2cb85d4c2990)


# 4. Descripción del ambiente de EJECUCIÓN (en producción) lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.

Se utilizó Python para el desarrollo del PClient y el PServer y Golang para el servidor central. En cuanto a las librerias, se usaron principalmente para los peers: 

grpcio==1.62.0
grpcio-tools==1.62.0
protobuf==4.25.3
python-dotenv==1.0.1
requests==2.28.1

Y para el servidor central fueron bastantes (se pueden consultar en el archivo requirements.txt del central-server)

## IP o nombres de dominio en nube o en la máquina servidor.

IPS elásticas en AWS. No hubo necesidad de nombre de dominio.

## Como se lanza el servidor.

Solo basta con hacer en la máquina luego de clonar el repositorio.

```
docker compose build
docker compose up
```


## Una mini guía de como un usuario utilizaría el software o la aplicación

Debe correr, como ya antes mencionado en detalle, el central-server, el pserver del peer1, el pserver del peer2 y los dos pclientes para probar el programa con sus microservicios.


## Opcionalmente - si quiere mostrar resultados o pantallazos 

![screenshot 2024-03-04](https://github.com/vaalmo/vmoralesv-st0263/assets/83479274/aeae9edd-1d41-41fb-aa2b-356044c14991)

![image](https://github.com/vaalmo/vmoralesv-st0263/assets/83479274/9ec17571-216d-40c9-a785-17568f8d53ab)



# 5. Otra información que considere relevante para esta actividad.

# referencias:

#### [grpc with python](https://www.youtube.com/watch?v=WB37L7PjI5k)
#### [Install docker](https://docs.docker.com/compose/install/linux/)
#### url de donde tomo info para desarrollar este proyecto

#### Video

link:  https://youtu.be/QJnk5angS9A


