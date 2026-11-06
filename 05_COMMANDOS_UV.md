4. Comandos útiles de UV
Comando	Descripción
uv init	Inicializa un nuevo proyecto
uv add <paquete>	Agrega una dependencia
uv remove <paquete>	Elimina una dependencia
uv sync	Sincroniza el entorno virtual con pyproject.toml
uv run <script>	Ejecuta un script en el entorno virtual
uv venv	Crea un entorno virtual
uv pip install <paquete>	Instala un paquete (como pip)



Ejemplo práctico de flujo de trabajo con UV
bash
# 1. Crear nuevo proyecto
uv init mi_proyecto
cd mi_proyecto

# 2. Agregar dependencias
uv add fastapi uvicorn

# 3. Agregar dependencias de desarrollo
uv add --dev pytest black

# 4. Sincronizar entorno
uv sync

# 5. Ejecutar tu aplicación
uv run uvicorn main:app --reload
