# PracticaFinal

Resolución de la Práctica final de Desplegaments d'Aplicacions WEB

Este proyecto implementa una aplicación MERN (MongoDB, Express, React/Angular, Node.js) utilizando Docker Compose para orquestar los contenedores de servicios, incluyendo MongoDB, Backend (Express), Frontend (React/Angular), Mongo-Express para la administración de la base de datos, y Nginx como LoadBalancer.

## Requisitos Previos

Antes de comenzar, asegúrate de tener instalado Docker y Docker Compose en tu sistema. Para más información, consulta la [documentación oficial de Docker](https://docs.docker.com/get-docker/) y [Docker Compose](https://docs.docker.com/compose/install/).

## Configuración del Proyecto

1. **Clonar el Repositorio**: Clona este repositorio en tu máquina local utilizando el siguiente comando:

    ```
    git clone https://github.com/MarcosFerMel/PracticaFinal.git
    ```

2. **Cambio a la rama `main_docker_compose`**:

    ```
    git checkout main_docker_compose
    ```

3. **Archivo `.env`**: Crea un archivo `.env` en la raíz del proyecto basándote en la siguiente estructura, ajustando las variables de entorno según sea necesario:

# MongoDB Configuration
MONGO_INITDB_ROOT_USERNAME=root_user
MONGO_INITDB_ROOT_PASSWORD=root_password
MONGO_DATABASE=mydatabase
MONGO_USER=myuser
MONGO_PASSWORD=mypassword

# Backend Configuration
BACKEND_PORT=4000
MONGO_URI=mongodb://myuser:mypassword@mongo_container:27017/mydatabase

# Frontend Configuration
FRONTEND_PORT=3000
API_URL=http://localhost:4000/api

# Mongo-Express Configuration
ME_CONFIG_MONGODB_ADMINUSERNAME=root_user
ME_CONFIG_MONGODB_ADMINPASSWORD=root_password
ME_CONFIG_MONGODB_SERVER=mongo_container

# Nginx Configuration
NGINX_PORT=80

# Prometheus Configuration (Optional)
PROMETHEUS_PORT=9090

# Grafana Configuration (Optional)
GRAFANA_PORT=3500


## Estructura de Carpetas

- `/backend`: Contiene el código fuente del servicio Backend.
- `/frontend`: Contiene el código fuente del servicio Frontend.
- `/mongo`: Incluye el dump de MongoDB para la restauración inicial de datos.
- `/loadbalancer`: Contiene la configuración de Nginx.
- `docker-compose.yml`: Define la configuración de todos los servicios.

## Puesta en Marcha del Proyecto

Para iniciar todos los servicios definidos en `docker-compose.yml`, ejecuta el siguiente comando en la raíz del proyecto:

```
docker-compose up -d
```

Esto construirá las imágenes (si es necesario) y arrancará los contenedores.

## Detener y Limpiar el Proyecto

Para detener y eliminar los contenedores, la red creada, y los volúmenes anónimos asociados con el proyecto, ejecuta:

```
docker-compose down -v
```

Este comando es útil para asegurar un estado limpio y evitar el almacenamiento de datos obsoletos entre ejecuciones.

## Acceso a los Servicios

- **Frontend**: Accede a la interfaz de usuario en [http://localhost](http://localhost).
- **Backend**: El API estará disponible en [http://localhost/api](http://localhost/api).
- **Mongo-Express**: Administra la base de datos MongoDB en [http://localhost:8081](http://localhost:8081).
- **Nginx LoadBalancer**: Se accede a través del puerto 80 por defecto.

## Monitorización

Si has configurado los servicios de Prometheus y Grafana para la monitorización, puedes acceder a:

- **Prometheus**: [http://localhost:9090](http://localhost:9090).
- **Grafana**: [http://localhost:3500](http://localhost:3500).

## Contribuciones

Las contribuciones son bienvenidas.

# Paso a paso de lo realizado:

####  1.- Creamos el directorio de la práctica

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/1.-%20Creamos%20el%20directorio%20de%20la%20pr%C3%A1ctica.jpg)

#### 2.- Creamos la estructura para la práctica

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/2.-%20Creamos%20la%20estructura%20para%20la%20pr%C3%A1ctica.jpg)
#### 3.- En la carpeta de backend creamos un Dockerfile y le damos contenido

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/3.-%20En%20la%20carpeta%20de%20backend%20creamos%20un%20Dockerfile%20y%20le%20damos%20contenido.jpg)
#### 4.- Hacemos lo mismo para la  carpeta del frontend

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/4.-%20Hacemos%20lo%20mismo%20para%20la%20%20carpeta%20del%20frontend.jpg)
#### 5.- Instalamos el package.json

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/5.-%20Instalamos%20el%20package.json.jpg)
#### 6.- Creamos el fichero .env con todas la variables que necesitamos para nuestro proyecto

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/6.-%20Creamos%20el%20fichero%20.env%20con%20todas%20la%20variables%20que%20necesitamos%20para%20nuestro%20proyecto.jpg)
#### 7.- Definimos en el docker-compose.yml todos los servicios que se nos piden, con la variables definidas en el fichero .env

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/7.-%20Definimos%20en%20el%20docker-compose.yml%20todos%20los%20servicios%20que%20se%20nos%20piden%2C%20con%20la%20variables%20definidas%20en%20el%20fichero%20.env.jpg)
#### 8.- Configuramos el ngnix.conf para que definir los endpoints que apuntarán a los servicios backend y servir los archivos estáticos para el frontend.

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/8.-%20Configuramos%20el%20ngnix.conf%20para%20que%20definir%20los%20endpoints%20que%20apuntar%C3%A1n%20a%20los%20servicios%20backend%20y%20servir%20los%20archivos%20est%C3%A1ticos%20para%20el%20frontend..jpg)
#### 9.- Creamos la imagen para el backend

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/9.-%20Creamos%20la%20imagen%20para%20el%20backend.jpg)
#### 10.- Generamos la imagen para el backend

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/10.-%20Generamos%20la%20imagen%20para%20el%20backend.jpg)
#### 11.- Instalamos los módulos de express y de mongoose

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/11.-%20Instalamos%20los%20m%C3%B3dulos%20de%20express%20y%20de%20mongoose.jpg)
#### 12.- Creamos el Dockerfile en nuestro raiz con el siguiente contenido

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/12.-%20Creamos%20el%20Dockerfile%20en%20nuestro%20raiz%20con%20el%20siguiente%20contenido.jpg)
#### 13.- Creamos el .dockerignore para que nos ignore la carpeta de node_modules ya que hemos definido en el Dockerfile la copia del package.json y la instalación y ya se generaría esa carpeta

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/14.-%20Creamos%20el%20.dockerignore%20para%20que%20nos%20ignore%20la%20carpeta%20de%20node_modules%20ya%20que%20hemos%20definido%20en%20el%20Dockerfile%20la%20copia%20del%20package.json%20y%20la%20instalaci%C3%B3n%20y%20ya%20se%20generar%C3%ADa%20esa%20carpeta.jpg)
#### 14.- Generamos nuestra imagen

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/15.-%20Generamos%20nuestra%20imagen.jpg)
#### 15.- Creamos nuestro contenedor para imagen creada dockernode

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/16.-%20Creamos%20nuestro%20contenedor%20para%20imagen%20creada%20dockernode.jpg)
#### 16.- Captura, de Docker Desktop, del contenedor creado con la imagen creada

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/16B.-%20Captura%2C%20de%20Docker%20Desktop%2C%20del%20contenedor%20creado%20con%20la%20imagen%20creada.jpg)
#### 17.- Comprobamos en el localhost_5000 que ya funciona desde nuestro contenedor

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/17.-%20Comprobamos%20en%20el%20localhost_5000%20que%20ya%20funciona%20desde%20nuestro%20contenedor.jpg)
#### 18.- Creamos un archivo de docker-compose.yml que nos permitirá componer los distintos contenedores para la práctica

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/18.-%20Creamos%20un%20archivo%20de%20docker-compose.yml%20que%20nos%20permitir%C3%A1%20componer%20los%20distintos%20contenedores%20para%20la%20pr%C3%A1ctica.jpg)
#### 19.- Construimos nuestra aplicación especificada en el docker-compose

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/19.-%20Construimos%20nuestra%20aplicaci%C3%B3n%20especificada%20en%20el%20docker-compose.jpg)
#### 20.- Iniciamos los servicios

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/20.-%20Iniciamos%20los%20servicios.jpg)
#### 21.- Captura, de Docker Desktop, de los servicios levantados

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/20B.-%20Captura%2C%20de%20Docker%20Desktop%2C%20de%20los%20servicios%20levantados.jpg)
#### 22.- Comprobamos los archivos que se están guardando

![](https://github.com/MarcosFerMel/PracticaFinal/blob/main/21.-%20Comprobamos%20los%20archivos%20que%20se%20est%C3%A1n%20guardando.jpg)
