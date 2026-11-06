
### Crear carpeta de DOCKER FILE sin extencion 
Dockerfile 

### Agregar los siguientes comandos (es el que crea la imagen )
FROM python:3.11-slim


ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    MPLBACKEND=Agg \
    PIP_NO_CACHE_DIR=1

WORKDIR /app

RUN apt-get update \
    && apt-get install --no-install-recommends -y ca-certificates \
    && rm -rf /var/lib/apt/lists/*

COPY pyproject.toml poetry.lock README.md ./
COPY src/ ./src/

RUN python -m pip install --upgrade pip \
    && pip install poetry \
    && poetry config virtualenvs.create false \
    && poetry install --no-interaction --no-ansi

EXPOSE 8000

CMD ["uvicorn", \
     "smart_portfolio_api.main:app", \
     "--host", \
     "0.0.0.0", \
     "--port", \
     "8000" \
]


### Crear archivo de parametros 
compose.yaml

services:
  api:
    build:
      context: .
      dockerfile: Dockerfile

    container_name: smart-portfolio-api

    ports:
      - "8000:8000"

    restart: unless-stopped



### Crear archivo de parametros tambien YAML
compose.dev.yaml    

services:
  api:
    build:
      context: .
      dockerfile: Dockerfile

    container_name: smart-portfolio-api-dev

    ports:
      - "8000:8000"

    volumes:
     - ./src:/app/src

    command: 
     - uvicorn
     - smarrt_postfolio_api.main:app
     - --host
     - 0.0.0.0
     - --port
     - 8000
     - --reload




## COMANDOS UTILES DOCKER

### listar todas las imágenes almacenadas localmente
docker images
### Comandos útiles para inspeccionar y gestionar imágenes
#### Ver detalles profundos de una imagen (capas, configuración, variables):
### Bash
docker inspect financial-api:v1
### Eliminar una imagen que ya no necesites:
### Bash
docker rmi financial-api:v1
#### Eliminar imágenes huérfanas o sin usar para liberar espacio:
#### Bash
docker image prune



### 1. Construir la imagen de Docker
### Bash
docker build -t financial-api:v1 .
### 2. Ejecutar el contenedor con Docker directamente
### Bash
docker run -d -p 8000:8000 --name financial_api_container financial-api:v1
### (O si prefieres usar Docker Compose):
### Bash
docker compose up -d --build
#### Paso 5: Verificar que la API funciona en Docker
#### Revisar los logs del contenedor (verás el log del auto-setup descargando datos y entrenando el modelo al arrancar):
### Bash
docker logs -f financial_api_container
### Probar la salud de la API en el navegador o terminal:
Swagger UI: http://localhost:8000/docs
Endpoint Health: http://localhost:8000/health
Prueba cURL:


