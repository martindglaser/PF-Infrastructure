# Pruebas Automaticas QA con Inteligencia Artificial

## Prerrequisitos para la instalación
Antes de comenzar, asegúrate de tener instalado y en ejecución:

- Git

- Docker Desktop (Es fundamental que la aplicación esté abierta y corriendo antes de continuar).


## Instalación
#### Windows
Abrí Docker

Abrí tu terminal donde quieras que esté ubicado el proyecto y ejecutá los siguientes comandos:

(Recordá reemplazar tu API Key de Gemini en su comando)
    
    git clone https://github.com/martindglaser/PF-Infrastructure.git

    cd PF-Infrastructure

    git submodule sync --recursive
    git submodule update --init --recursive

    echo GOOGLE_API_KEY=INSERTA_TU_GOOGLE_GEMINI_API_KEY_ACA > .env

    docker-compose up -d --build

## Resultado
Ya debería estar corriendo tu aplicación en http://localhost:5173/
## Autores

- [@martindglaser](https://github.com/martindglaser)
- [@valentinosara](https://github.com/valentinosara)
- [@tatianapisani](https://github.com/tatianapisani)
- [@LucianoAmato7](https://github.com/LucianoAmato7)


