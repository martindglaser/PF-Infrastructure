## Despliegue con Docker
Este proyecto utiliza Docker Compose para orquestar y ejecutar todos los servicios (frontend, backend, api-ia) de forma unificada. Esta guía reemplaza el método anterior de iniciar cada repositorio de forma individual.

## Prerrequisitos
Antes de comenzar, asegúrate de tener instalado y en ejecución:

-Git

-Docker Desktop (Es fundamental que la aplicación esté abierta y corriendo antes de continuar).

## Configuración de Entorno
Este proyecto requiere una variable de entorno para la API de Google. Esta configuración solo es necesaria la primera vez.

En la carpeta raíz del proyecto (al mismo nivel que docker-compose.yml), crea un archivo nuevo llamado .env.

Abre el archivo .env y añade la siguiente línea, reemplazando el valor de ejemplo por tu clave de API:

GOOGLE_API_KEY=TU_API_KEY_DE_GOOGLE_GEMINI

## Inicio de Servicios
Para construir las imágenes de Docker e iniciar todos los contenedores, abre una terminal en la carpeta raíz del proyecto y ejecuta:

docker-compose up -d --build

Detalle de los comandos:

--build: Fuerza la reconstrucción de las imágenes. Es necesario la primera vez o si se realizan cambios en el código fuente (ej. Dockerfile, requirements.txt).

-d: (Modo "detached") Ejecuta los contenedores en segundo plano.

## Acceso a la Aplicación
Una vez que los contenedores se hayan iniciado correctamente (puedes verificar su estado en Docker Desktop), la aplicación estará disponible en:

Frontend (Aplicación Web): http://localhost:5173

## Cómo Detener los Servicios
Para detener y eliminar todos los contenedores y redes creados por Docker Compose, ejecuta:

docker-compose down

## La próxima vez que abras VS Code, solo tienes que hacer esto:
Asegúrate de que Docker Desktop esté abierto y luego, en tu terminal, ejecuta:

docker-compose up -d