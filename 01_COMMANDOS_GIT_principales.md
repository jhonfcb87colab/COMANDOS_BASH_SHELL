
### Clonar un repositorio 
git clone https://github.com/jfcruzibp/Polars.git temp_polars
git init
git remote add origin https://github.com/jfcruzibp/Polars.git
## Crea la rama principal
git branch -M main


##### ************************		INSTALAR PYTHON 		******************************
##### Ver python version
py --version
python --version
py -m pip --version

************************************************************************************************************************************************************************************************************************************************************************************************************************
************************		INSTALAR GIT 		******************************
##### revisar si esta instalado 
PS C:\ARC_ONEDRIVE\OneDrive\00000_DOCUMENTOS\UNIVERSIDAD SANTO TOMAS\SEMESTRE 02\05 MLOPS\ACTIVIDAD01\MLOPS>git


version de git
git --version

### Respositorio de Git del equipo de trabajo 
https://github.com/jjgomezreyes/MLOPS/


##### Descargar la última versión de main desde GitHub
git fetch origin main


#### Para reemplazar todo tu código local por la versión limpia de main, debes hacer un 
git reset --hard
# 1. Asegúrate de tener la versión más reciente de main de GitHub
git fetch origin main
# 2. Forzar a tu rama actual a ser una copia idéntica de origin/main
git reset --hard origin/main

##### Remplazar una rama ejemplo desde mi rama (feature/model-training)
# 1. Traer lo último de GitHub
git fetch origin main
# 2. Forzar tu rama actual a quedar idéntica a origin/main
git reset --hard origin/main
# 3. Limpiar archivos sueltos no rastreados (opcional)
git clean -fd




##### Configura Git en tu computador. Usa el mismo nombre y correo que quieres asociar a tus commits:
git config --global user.name "John Cruz"
git config --global user.email "jhonfcb87.colab@gmail.com"
git config --global user.email "johnfcb@gmail.com"
git config --global init.defaultBranch main

***** importante Creacion de una RAMA
git checkout -b origin/main
git checkout -b feature/data-preparation
git checkout -b feature/model-training
git checkout -b feature/mlflow-tracking
git checkout -b feature/model-interface-api
git checkout -b feature/model-Image-docker


***** los siguientes son los feeatures (ramas con los que se entrara a trabajar)
feature/data-preparation
feature/model-training 
feature/mlflow-tracking

##### Ver en que rama me encuentro 
*** Ver a la RAMA en que se encuentra  
git branch
git remote -v
git fetch --all --prune
git branch -r
git branch -a


#### Para traer todas las ramas y referencias del remoto, debes usar 
git fetch

********ver el estado del repositorio  (Ver archivos que nos esten trackeados)
git status


*** traer las Ramas
git pull
**** Ir a una rama 
git checkout feature/data-preparation
git checkout feature/model-training 
git checkout feature/mlflow-tracking


**** subi rama del repositorio (por archivo / todos los archivos)
****Todos los archivos
git add .
***solo un archivo
git add Archivo01.py

**** complementar con  compentarios el pull de la 
git commit -m "Actualizacion de la capa de datos en el consumo de la api yfinance con sus respctivas clases y funciones"
git commit -m "tercera actualizacion de los archivos de entrenamiento se re unibica en la carpeta SRC"


**** Envio de los cambios (la primera vez  al hacer un push en una nueva rama se genera un error pero se agregan otros comandos)
git push
***solucionar error 
git push --set-upstream origin feature/feature/data-preparation


Crea un repositorio de prueba. En GitHub, crea un repositorio llamado mlops-python-ambiente. Luego, desde tu carpeta local:
git init
git add .
git commit -m "Configura proyecto inicial"


### Forzar el commit 
git push --set-upstream origin feature/data-preparation


#### Para obligar al repositorio remoto (GitHub / GitLab / Bitbucket) a descartar lo que tenía antes y reemplazarlo al 100% por esta versión limpia:
git push origin feature/data-preparation --force

***Ver a la RAMA en que se encuentra  
git branch
### Enviar finalmente los ajustes 
git push

***ubicarse en la RAMA Main
git branch -M main

git remote add origin https://github.com/TU_USUARIO/mlops-python-ambiente.git
git push -u origin main


##### (Esto obliga a la rama feature/data-preparation a tomar el commit y el estado exacto en el que te encuentras).
git branch -f feature/data-preparation main






######### ************************************************************************************************************************************************************************

Evidencia para la primera clase
Antes de iniciar el trabajo técnico, cada estudiante debería poder mostrar una captura o salida de terminal con:

python --version
git --version
poetry --version
docker --version
git config --global user.name
git config --global user.email


************* Incializar GIT cuando hay fallas en las ramas 
Si este proyecto ya existe en un repositorio remoto

Necesitas agregar el remoto primero:

git remote add origin https://github.com/jfcruzibp/MLOPS_APIS
git fetch origin
git branch -a





Instala Poetry. Ejecuta este comando en PowerShell:
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
poetry --version
Crear un proyecto nuevo
poetry new mlops-clasificador
cd mlops-clasificador
poetry add pandas numpy scikit-learn joblib
poetry add --group dev pytest black ruff
poetry run python --version
Usar Poetry en una carpeta existente
mkdir mlops-pipeline
cd mlops-pipeline
poetry init
poetry add pandas scikit-learn
poetry run python main.py

Instalar Docker
docker --version
docker run hello-world

Validar instalación
docker --version
docker compose version
docker run hello-world
Comandos que debes reconocer
docker images
docker ps
docker ps -a
docker stop NOMBRE_CONTENEDOR
docker rm NOMBRE_CONTENEDOR


Primer Dockerfile de referencia
FROM python:3.12-slim
WORKDIR /app
COPY pyproject.toml poetry.lock ./
RUN pip install poetry && poetry config virtualenvs.create false && poetry install --no-interaction

COPY . .
CMD ["python", "main.py"]



