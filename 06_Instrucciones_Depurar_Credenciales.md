# Guía Práctica: Depuración de Credenciales desde la Terminal

Si necesitas desvincular tus cuentas o cerrar sesión de forma segura en un computador antes de dejar de usarlo, sigue estos pasos desde la consola según tu sistema operativo.

---

## 1. Depuración en Windows (CMD o PowerShell)

En Windows, las contraseñas del sistema y sesiones web se guardan en el **Administrador de Credenciales**.

### Pasos:

1. **Listar credenciales existentes:**
   Abre la consola de comandos (`cmd`) o PowerShell y ejecuta:
   ```cmd
   cmdkey /list
   ```
   *Esto imprimirá una lista completa de los destinos (`Target`) donde hay contraseñas guardadas.*

2. **Eliminar una credencial específica:**
   Identifica el valor del campo `Target:` (por ejemplo, `Target: LegacyGeneric:target=git:https://github.com`) y elimina la credencial con:
   ```cmd
   cmdkey /delete:NombreDelDestino
   ```
   *Ejemplo:*
   ```cmd
   cmdkey /delete:git:https://github.com
   ```

3. **Borrar credenciales del Administrador de Git:**
   ```bash
   git credential-manager erase
   ```

---

## 2. Depuración en macOS (Terminal)

En macOS, las contraseñas se almacenan en el sistema de **Keychain (Llavero)** y se pueden gestionar desde la terminal mediante el comando `security`.

### Pasos:

1. **Listar credenciales genéricas guardadas:**
   ```bash
   security dump-keychain
   ```

2. **Eliminar credenciales genéricas (por servicio y/o usuario):**
   ```bash
   security delete-generic-password -l "NombreDelServicio"
   ```
   *O especificando el usuario:*
   ```bash
   security delete-generic-password -a "tu_usuario" -s "nombre_del_servicio"
   ```

3. **Eliminar contraseñas de red/internet:**
   ```bash
   security delete-internet-password -s "github.com"
   ```

---

## 3. Pasos Adicionales Recomendados (Windows / macOS / Linux)

Para asegurar una limpieza completa antes de entregar o dejar de usar la máquina:

### A. Borrar Claves SSH Almacenadas
Si generaste claves SSH para conectarte a servidores o repositorios:
* **Windows (PowerShell):**
  ```powershell
  Remove-Item -Recurse -Force ~/.ssh/*
  ```
* **macOS / Linux (Terminal):**
  ```bash
  rm -rf ~/.ssh/*
  ```

### B. Limpiar Caché y Configuración Global de Git
Restablece las variables globales de usuario en Git para desvincular tu nombre y correo:
```bash
git config --global --unset user.name
git config --global --unset user.email
git config --global --unset credential.helper
```

### C. Cerrar Sesiones Activas en Navegadores
Recuerda cerrar manualmente la sesión activa en tus navegadores web o borrar los datos de navegación (Cookies y Caché) antes de salir.