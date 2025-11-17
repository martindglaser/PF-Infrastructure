# 🤖 Pruebas Automáticas QA con Inteligencia Artificial (BDT Global)

Este repositorio contiene la infraestructura principal y la orquestación de servicios para la plataforma BDT Global. La aplicación utiliza una arquitectura de microservicios gestionada por Docker Compose para unificar el Frontend, el Backend y el servicio de Inteligencia Artificial.

## 🏛️ Arquitectura del Proyecto

Este repositorio actúa como el "orquestador". No contiene el código fuente de la aplicación en sí, sino que utiliza **submódulos de Git** para gestionar y unificar los tres servicios principales. El archivo `docker-compose.yml` define cómo se construyen y conectan estos servicios.

### ⚙️ Servicios

1.  **`PF-Frontend` (Servicio: `frontend`)**
    * **Descripción:** Es la interfaz de usuario con la que interactúa el usuario final.
    * **Tecnología:** Aplicación React (Vite).
    * **URL (Local):** `http://localhost:5173`.

2.  **`PF-Backend` (Servicio: `backend`)**
    * **Descripción:** Es el servidor principal que maneja la lógica de negocio, la comunicación con la base de datos y sirve como puerta de enlace.
    * **Tecnología:** Aplicación C# ASP.NET Core.
    * **URL (Local):** `http://localhost:5288` (mapeado desde el puerto 5000 del contenedor).

3.  **`PF-API-IA` (Servicio: `api-ia`)**
    * **Descripción:** Es el microservicio especializado que se comunica con la API de Google Gemini. Procesa las solicitudes de análisis, genera las descripciones y sugerencias de la IA.
    * **Tecnología:** Aplicación Python con Flask.
    * **URL (Local):** `http://localhost:5001`.

## 💻 Stack Tecnológico

| Categoría            | Tecnología                   |
|                      |                              |
| **Orquestación**     | Docker Compose               |
| **Frontend**         | React, Vite                  |
| **Backend**          | C# .NET (ASP.NET Core)       |
| **Servicio IA**      | Python, Flask, Google Gemini |

## ✅ Prerrequisitos para la Instalación

Antes de comenzar, asegúrate de tener instalado y en ejecución:

* **Git**
* **Docker Desktop** (Es fundamental que la aplicación esté abierta y corriendo antes de continuar).
* Una **Clave API de Google Gemini** (para el análisis de IA).

## 🚀 Instalación

1.  **Clonar el repositorio y submódulos:**
    Abre tu terminal y clona este repositorio. El flag `--recurse-submodules` es importante para descargar automáticamente el código de los repositorios `PF-Frontend`, `PF-Backend` y `PF-API-IA`.

    ```bash
    git clone --recurse-submodules [https://github.com/martindglaser/PF-Infrastructure.git](https://github.com/martindglaser/PF-Infrastructure.git)
    ```

    *(Si ya lo clonaste sin el flag, puedes ejecutar los siguientes comandos para inicializar los submódulos)*:
    ```bash
    git submodule sync --recursive
    git submodule update --init --recursive
    ```

2.  **Acceder al directorio:**
    ```bash
    cd PF-Infrastructure
    ```

3.  **Crear archivo de entorno (`.env`):**
    Este paso es crucial. Debes crear un archivo `.env` en la raíz del proyecto para proporcionar tu clave de API al servicio `api-ia`. Puedes usar el `.env.example` como plantilla.

    (Recuerda reemplazar `TU_GOOGLE_GEMINI_API_KEY_ACA` con tu clave real)
    ```bash
    echo GOOGLE_API_KEY=TU_GOOGLE_GEMINI_API_KEY_ACA > .env
    ```
    El `docker-compose.yml` está configurado para leer este archivo y pasarlo como variable de entorno al contenedor `api-ia`.

4.  **Construir y ejecutar los contenedores:**
    Este comando leerá el `docker-compose.yml`, construirá las imágenes de Docker para cada servicio (basado en sus respectivos `Dockerfile`) y los iniciará en segundo plano (`-d`).

    ```bash
    docker-compose up -d --build
    ```

## 🌐 Acceso a la Aplicación

¡Listo! Una vez que los contenedores estén en funcionamiento, podrás acceder a la aplicación desde tu navegador:

* **Aplicación Principal (Frontend):** **`http://localhost:5173/`**

### Endpoints de APIs (para pruebas)

* **Endpoint del Backend:** `http://localhost:5288`
* **Endpoint de la API de IA:** `http://localhost:5001`

### 🛑 Cómo detener la aplicación

Para detener todos los servicios y eliminar los contenedores, ejecuta:

```bash
docker-compose down