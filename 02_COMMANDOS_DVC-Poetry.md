
## Libro de configuraciones
- https://wilmerpineda.github.io/guia_config_python_mlops/

## configuracion POETRY
#### Instala Poetry. Ejecuta este comando en PowerShell:
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -


#### Revisar version 
poetry --version

## Pasos ejemplo clase 
- crear carpeta Ejemplo_clase
- Desde consola
poetry --version

poetry init
-- Se da ENTER  hasta que finalice


##### Instalar paquetes  por medio de POETRY
poetry add pandas mlflow dvc scikit-learn joblib numpy
- por etapas 
poetry add "pandas>2.3.0,<3.0"
poetry add dvc
poetry add scikit-learn
poetry add mlflow
poetry add "numpy<2.2.0"
poetry add yfinance

##### Crear el ambiente virtual 
poetry install --no-root

#### 
python -m poetry run python -c "import session_duration; print('ok')"
- Ajustada 
poetry run python -c "import session_duration; print('ok')"

genera error por que no tiene la session_duration

# 1. Inicializa Git en tu directorio actual
git init

# 2. Ahora sí, inicializa DVC (ya no necesitarás el --subdir si Git está aquí mismo)
poetry run dvc init
##### Inciar poetry desde cero 
poetry run dvc init -f

### Llamaar el DVC del poetry (Se puede saltar el paso anterior)
poetry run dvc init --subdir
#### cuando ya existe 
poetry run dvc init --subdir -f

##### configurar el conjunto de datos
* Importar archivo "params.yaml"
* crear capeta "src"
* importar archivo de ejemplo de generador  de datos "generate_data.py"

#### Crear los datos de MOCK
- comandos 
poetry run python -m generate_data --params params.yaml (No funciono = "No module named generate_data")
##### Crear archivo config
- Importar archivo "config.py" que contiene las funciones ("load_params","ensure_parent")

##### Comandos ajustados
###### asignacion del PATH
- $env:PYTHONPATH = "src"  
###### Probar si funciona python
- comandos
poetry run python -c "print('Hola mundo')"
poetry run python -m generate_data --params params.yaml
- Esta debe ser la respuesta: Dataset mock creado en data\raw\session_data.csv con 1500 filas.


### Ejecutar el entrenamiento 
##### Opcion 1
$env:PYTHONPATH="src"; poetry run python src/train_models.py

#####  Opcion 2
poetry run python -m src.train_models


