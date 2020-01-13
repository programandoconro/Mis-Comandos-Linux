# Una lista de comandos Linux, por Ro

Privilegios absolutos (root)

```su```

Si el usuario pertenece al grupo de administradores

```sudo -i``` 

Crear Usuario

```sudo useradd nombreusuario```

Para agregar usuarios a grupos, por ejemplo, grupo sudo

```usermod -aG sudo nombreusuario```

Eliminar usuario

```userdel nombreusuario```

Para cambiar la contraseña utilizamos:

```passwd```

Para ver los grupos a los que pertenece el usuario

```group nombreusuario``` 


Actualizar 

 ```
 sudo -i
 apt update -y
 apt upgrade -y
 apt autoremove -y
 
 ```
O,

``` apt update -y && apt upgrade -y && apt autoremove -y```

Instalar todo tipo de programas en Linux, por ejemplo, htop: 

```sudo apt install htop -y```


Reiniciar, apagar en 30 min, apagar ahora.
```
 reboot
 shutdown -h +30
 poweroff -f
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

Limpiar la pantalla en la terminal

``` clear # o Crtl-L```

Ver la historia del terminal

```history```

Montar USB externo

```sudo mount -rw /dev/sd* /carpeta```

Crear un archivo vacio:

 ```touch nombrearchivo```
 
Crear un archivo con un texto corto:

``` echo "Texto corto" > nombrearchivo ```

Si utilizamos >> agregamos el texto sin reemplazar el archivo. 

``` echo "Agregamo texto nuevo" >> nombrearchivo```

Si queremos aplicar un comando a un archivo, por ejemplo, un sript mysql, usamos "<" 

mariadb --user=root --password -s < mariadb.sql

Para echar un ojo a un archivo corto:

 ```cat nombrearchivo```

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

Para saber dispositivos conectados a los puertos USB:

```lsusb```
 
Ver las conexiones sockets de nuestro equipo

``
ss
ss -l
`` 
Ip y Wifi.

```
 ifconfig
 ip address
 iwconfig
```
 
Para saber el nombre del host.

```hostname```
 
Para cambiar el nombre de la computadora:

```hostnamectl set-hostname nuevonombre```

Ver los puertos abiertos en una red
```
nmap localhost
# Para evaluar la red local entera:
nmap 192.168.1.1/24 #(o 192.168.0.1/24)
#filtrar por puerto y estado 
nmap -Pn 192.168.1.1/24 -p22 -open  
# Auditar 
nmap -Pn **PublicIP**/24 
```
Conectar por SSH

 ``` ssh usuario@servidor.local```
 
Conectar SSH sin password
 
 ```
 ssh-keygen
 ssh-copy-id -i ~/.ssh/id_rsa.pub usuario@servidor.local
 ```
Compartir archivos via SSH

```scp nombrearchivo mi@servidor.local:~```


Bloquear IPs

```
 iptables -A INPUT -s $IPbloquear -j DROP
 ```
 
Usuario y tiempo conectado
```
uname -r
uptime -p
```

Descargar archivos desde la terminal, por ejemplo, instalador de RStudio para Debian 10 y Ubuntu 19. 

 ```wget https://download1.rstudio.org/desktop/bionic/amd64/rstudio-1.2.5001-amd64.deb```

 Bajar videos 
 
```
youtube-dl #linkayoutube
# solamente audio
youtube-dl --extract audio --format mp3 
```
Con el programa vlc, podemos escuchar y controlar la música desde la línea de comandos. 

 ```cvlc /music```
Almacenamiento de los discos

 ``df``
 
Si queremos saber donde está un dispositivo USB, disco duro y sus particiones:

 ```fdisk -l```

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


Con neofetch podemos ver detalles de nuestro sistema de manera divertida. 

 ```neofetch```
 
 
Descomprimir archivos
 ```
 unzip *.zip
 gunzip example.txt.gz
 ```

Instalación de aplicaciones .deb. Tambien es posible usar gdebi. 

``` dpkg -i archivo.deb && apt install -f```

Los siguientes comandos utilizan systemctl para controlar servicios del sistema.
```
 systemctl enable nombreservicio
 systemctl start nombreservicio
 systemctl stop nombreservicio
 systemctl disable nombreservicio
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

``` elinks https://medium.com/learn-love-code/how-to-set-up-your-professional-data-science-environment-6df74eb06aa4 ```

Controlar la accesibilidad de los archivos y carpetas de nuestro sistema, por ejemplo, dar todo tipo de acceso a un archivo:
```
 sudo chmod a+rwx nombrearchivo
 #O para que solamente root pueda acceder a ellos:
 sudo chmod 700 nombrearchivo
```
# Manejo de archivos y Data Mining

Para listar los archivos que tengan un patrón, por ejemplo, que terminen en .iso. 

 ```ls | grep *.iso```
 
Para saber el número de archivos en una carpeta:

``` ls | wc -l```

Conocer la cantidad de filas en una archivo

```wc -l archivo```


Para acceder a las primeras y últimas filas:

 ```
 head -10 archivo
 tail -10 archivo
 ```

Si el archivo es demasiado grande, podemos separarlo en varias partes, por ejemplo, cinco:

```split -n l/5 nombrearchivo x```

Para seleccionar la quinta columna, utilizamos:

```awk '{print $5}' nombrearchivo```

Separar columnas en función de un caracter, por ejemplo, dos puntos (:)

 ```cut -d ':' -f1 nombrearchivo```

Eliminar la primera fila de datos

```sed 1d *.txt```

Seleccionar quinta columna

```awk '{print $5}' *.txt``` 


Cambiar el orden de columnas

```
awk '{ print $3, $1 }' *.txt

ps -ef | awk -F " " '{print $2}' 
```

Cortar una sección intermedia de filas
```sed -n '250, 260p' *.txt > **.txt```

Para buscar archivos

```
sudo apt-get install mlocate
locate -i 
```
# Programas

## Git

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

## Docker (o Podman)

``` 
 docker ps -a
 docker images
 docker run -it ubuntu 
 docker build . -tagname  # Necesitas un archivo Dockerfile en el directorio

# docker-compose
docker-compose -f docker-compose.yml up
```
## Tor 

Para navegar de manera anónima.  Simplemente descárgalo (https://www.torproject.org/dist/torbrowser/8.5.4/tor-browser-linux64-8.5.4_en-US.tar.xz) 

 ```
 tar -xvJf tor-browser-linux64-8.5.4_en-US.tar.xz
 ./tor-browser_en-US/Browser/start-tor-browser &
 ```

 ## Anaconda
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
# Juegos en Terminal
 
 ```
 apt-get install bastet moon-buggy ninvaders nsnake pacman4console neofetch figlet -y
 bastet
 moon-buggy
 ...
 figlet HOLA AMIGO 
 ``` 
 El próximo comando te hará sentir en la matrix. (apt install cmatrix)
 
 ```cmatrix```

# COMANDOS NIVEL INTERMEDIO 

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
Programar tareas

```
rm -f /var/run/crond.pid #delete pid
cron 00 00 *** myUpdate.sh #todos los dias a las 12
````
Cambiar el tamaño de las fuente en terminal. 
```dpkg-reconfigure console-setup```

Provocar sonidos en el computador (apt install beep / yum install beep)

```
beep -f 4000 -D 500 -l 100 -r 100
```
Ver lista de fuentes 

```nano /etc/apt/sources.list```

Cuando conectado por SSH, elegir en cual servidor mostrar el display. 
```
export DISPLAY=:0 # en servidor
export DISPLAY=:1 # en local
 ```
Enviar archivo via ncat por tunel ssh

```
cat myDocument.pdf | ssh me.myserver.com nc -l -p 20000
# cliente
nc me.myserver.com 20000 > myDocument.pdf
 ```
# IOT

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
 
Audio ssh rasp 

```amixer scontrols```

Busca el dispositivo y ajustar el volumen 

```amixer sset 'PCM' 100%```

# Ciclos Loop

## For 

          for i in {1..10} ; do 
              echo "hola $i"; 
          done

           #!/bin/bash
            for i in $( ls ); do
                echo item: $i
            done
      
## Otro For 

            #!/bin/bash
            for i in `seq 1 10`;
            do
                    echo $i
            done    
            
## While
             #!/bin/bash 
             COUNTER=0
             while [  $COUNTER -lt 10 ]; do
                 echo The counter is $COUNTER
                 let COUNTER=COUNTER+1 
             done
    
## Until
             #!/bin/bash 
             COUNTER=20
             until [  $COUNTER -lt 10 ]; do
                 echo COUNTER $COUNTER
                 let COUNTER-=1
             done
             
###########################################################################

# Links a Posts Relacionados:

https://programandoconro.wordpress.com/2019/10/02/mis-99-comandos-favoritos-en-gnu-linux/
https://programandoconro.wordpress.com/2020/01/02/10-trucos-en-linux-para-programadores-principiantes/

