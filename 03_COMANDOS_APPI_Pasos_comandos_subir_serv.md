Jupyter Book: https://wilmerpineda.github.io/modulo2_mlops_python/intro.html
Actividad módulo 2: https://wilmerpineda.github.io/ejercicio2_mlops_python/
Repo: GitHub - wilmerpineda/modulo2_mlops_python: Módulo 2 del curso de MLOps en Python



## Comandos 
## Instalar librerias y dependencias 
poetry install

# Poner en ejecucion flast api
./.venv/Scripts/python.exe -m uvicorn main:app






Ultilidades de Docker 
prophet


### Crear los siguientes archivos
- Crear archivo: readme.md
- Crear archivo: main.py
contenido:
"
from fastapi import FastAPI
app = FastAPI(
    title="Ejemplo Clase 02 - FastAPI",
    description="Ejemplo de una API REST con FastAPI",
)
@app.get("/")
def read_root():
    return {"message": "Hola, mundo!"}

@app.get("/sumar")
def sumar(a:float, b:float):
    total = a + b
    return {
            "resultado": total
            }
"
- Crear archivo: __init__.py


### Crear entorno virtual
- python -m venv .venv
### Activar entorno virtual 
.venv\Scripts\Activate


### Inciar poetry init
poetry init
poetry add fastapi
poetry add uvicorn

poetry install --no-root

---> no aplica -----> python -m main:app




### inciar servicio de Fast api  
python -m uvicorn main:app
python -m uvicorn main:app --reload
 
### Ir a la ruta 
http://127.0.0.1:8000/docs


### Ejecutar con un CURL
curl.exe -X GET "http://127.0.0.1:8000/sumar?a=100&b=30" -H "accept: application/json"
