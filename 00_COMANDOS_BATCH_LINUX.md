# Guía Completa de Comandos Bash y Linux Más Utilizados

A continuación, se presenta una selección estructurada con las herramientas y comandos de Bash/Linux más potentes y utilizados en entornos profesionales (Administración de Sistemas, DevOps, Redes y Automatización), organizados por categorías clave.

| Categoría | Comando / Herramienta | Descripción y Propósito Principal | Ejemplo de Uso Clave |
| :--- | :--- | :--- | :--- |
| **Navegación y Archivos** | `ls` | Lista archivos y directorios con opciones de formato y permisos. | `ls -laht` (detallado, ocultos, ordenado por fecha) |
| | `cd` | Cambia el directorio de trabajo actual. | `cd /var/log/` |
| | `pwd` | Muestra la ruta absoluta del directorio actual. | `pwd` |
| | `cp` | Copia archivos o directorios. | `cp -r /origen/ /destino/` |
| | `mv` | Mueve o renombra archivos y directorios. | `mv archivo.txt nuevo_nombre.txt` |
| | `rm` | Elimina archivos o directorios permanentemente. | `rm -rf carpeta_obsoleta/` |
| | `mkdir` | Crea nuevos directorios (incluyendo padres). | `mkdir -p proyecto/data/raw` |
| | `touch` | Crea archivos vacíos o actualiza marcas de tiempo. | `touch script.sh` |
| | `cat` | Concatena y muestra el contenido de archivos en pantalla. | `cat archivo.txt` |
| | `less` / `more` | Visualizadores paginados de archivos grandes. | `less /var/log/syslog` |
| **Búsqueda y Filtros** | `find` | Busca archivos y directorios según criterios avanzados. | `find /var/log -name "*.log" -mtime +7` |
| | `locate` | Busca archivos rápidamente usando una base de datos indexada. | `locate nginx.conf` |
| | `grep` | Busca patrones o expresiones regulares en textos/archivos. | `grep -rn "ERROR" /var/log/` |
| | `awk` | Lenguaje de procesamiento y extracción de columnas/datos. | `awk -F',' '{print $1, $3}' datos.csv` |
| | `sed` | Editor de flujos para transformar texto de forma masiva. | `sed -i 's/antiguo/nuevo/g' config.cfg` |
| | `sort` | Ordena líneas de archivos de texto. | `sort -nr datos.txt` |
| | `uniq` | Filtra o reporta líneas duplicadas. | `sort archivo.txt \| uniq -c` |
| | `head / tail` | Muestra el principio o el final de un archivo. | `tail -f /var/log/syslog` (tiempo real) |
| | `wc` | Cuenta líneas, palabras y bytes en un archivo. | `wc -l archivo.txt` |
| **Redes y Conectividad** | `ping` | Verifica la conectividad de red con un host remoto. | `ping -c 4 8.8.8.8` |
| | `curl` | Transfiere datos desde o hacia un servidor (APIs/Web). | `curl -X GET "https://api.ipify.org"` |
| | `wget` | Descarga archivos de la web de forma recursiva/directa. | `wget https://url.com/archivo.zip` |
| | `netstat` / `ss` | Muestra conexiones de red, puertos abiertos y sockets. | `ss -tulpn` (puertos escuchando) |
| | `ip` | Configura y muestra interfaces, rutas y dispositivos de red. | `ip a` o `ip route` |
| | `nmap` *(Escanear redes)* | Escáner de puertos y descubrimiento de hosts en red. | `nmap -sS -p 1-1024 192.168.1.0/24` |
| | `tcpdump` | Analizador de paquetes de red en la línea de comandos. | `tcpdump -i eth0 port 80` |
| | `iftop` / `nload` | Monitorean el ancho de banda en tiempo real por interfaz. | `iftop -i eth0` |
| | `dig` / `nslookup` | Consultan registros DNS de dominios. | `dig google.com` |
| **Automatización y Procesos** | `cron` / `crontab` *(Automatizar tareas)* | Programa la ejecución automática de tareas en horarios definidos. | `crontab -e` (editar tareas programadas) |
| | `at` | Ejecuta comandos una sola vez en un momento futuro. | `echo "bash backup.sh" \| at 02:00` |
| | `nohup` | Ejecuta procesos inmunes a desconexiones de terminal. | `nohup python3 script.py &> output.log &` |
| | `screen` / `tmux` | Multiplexores de terminal para sesiones persistentes. | `tmux new -s sesion_etl` |
| | `ps` | Muestra los procesos activos del sistema. | `ps aux \| grep python` |
| | `top` / `htop` | Monitor interactivo de recursos del sistema en tiempo real. | `htop` |
| | `kill` / `killall` | Envía señales (terminación) a procesos activos. | `kill -9 12345` |
| | `systemctl` | Administra servicios del sistema (systemd). | `systemctl status postgresql` |
| | `bg` / `fg` | Gestionan tareas en segundo plano y primer plano. | `jobs` seguido de `fg %1` |
| **Monitoreo de Recursos** | `df` | Muestra el espacio disponible en disco en los sistemas de archivos. | `df -h` |
| | `du` | Estima el uso de espacio en disco por archivos/directorios. | `du -sh /var/lib/*` |
| | `free` | Muestra la memoria RAM y SWAP libre/utilizada. | `free -h` |
| | `uptime` | Muestra el tiempo de actividad del sistema y carga promedio. | `uptime` |
| | `vmstat` | Reporta estadísticas de memoria virtual, procesos y CPU. | `vmstat 2 5` |
| | `iostat` | Monitorea el rendimiento de las unidades de almacenamiento I/O. | `iostat -xz 2` |
| **Permisos y Usuarios** | `chmod` | Modifica los permisos de acceso de archivos y carpetas. | `chmod +x script.sh` |
| | `chown` | Cambia el usuario y grupo propietario de un archivo. | `chown -R usuario:grupo /var/www/` |
| | `sudo` | Ejecuta un comando con privilegios de superusuario. | `sudo apt update` |
| | `passwd` | Cambia la contraseña de usuario. | `passwd` |
| | `useradd` / `userdel` | Gestionan la creación y eliminación de usuarios del sistema. | `sudo useradd -m nuevo_usuario` |
| **Compresión y Paquetes** | `tar` | Empaqueta y desempaqueta archivos (tarball). | `tar -czvf respaldo.tar.gz /carpeta/` |
| | `zip` / `unzip` | Comprime y descomprime archivos en formato ZIP. | `unzip archivo.zip -d /destino/` |
| | `gzip` / `gunzip` | Comprime o descomprime archivos individuales formato `.gz`. | `gzip archivo.txt` |
| | `apt` / `yum` / `dnf` | Gestores de paquetes de software del sistema operativo. | `sudo apt install htop -y` |
| **Seguridad y Remoto** | `ssh` | Conexión segura remota a servidores. | `ssh -i clave.pem usuario@servidor_ip` |
| | `scp` | Copia segura de archivos entre hosts a través de SSH. | `scp local.txt user@remote:/ruta/` |
| | `rsync` | Sincronización eficiente y rápida de archivos locales/remotos. | `rsync -avz /origen/ user@remote:/destino/` |
| | `ufw` | Administrador simplificado del cortafuegos (Firewall). | `ufw allow 22/tcp` |
| | `iptables` | Configuración avanzada de reglas de filtrado de paquetes de red. | `iptables -L -v` |
| | `openssl` | Herramienta criptográfica para certificados y cifrado. | `openssl req -x509 -days 365 -newkey rsa:2048` |

## Buenas Prácticas Rápidas en Bash
* **Modo estricto para scripts:** Utiliza siempre `set -euo pipefail` al inicio de tus scripts para una mejor gestión de errores.
* **Registro de logs:** Redirige la salida estándar y de errores con `>> /ruta/archivo.log 2>&1`.