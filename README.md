# repositorioSO
_Para ver ruta en la que se encuentra_
  pwd

_Actualizar repositorios_
  apt-get update

_Dar permisos de super usuario a cualquier comando_
  sudo

_Instalar software desde repositorios_
  apt install
  snap  `tambien se puede usar`

_Limpiar terminal_
  clear

_Revisar posibilidades de comandos o software_
  apt search
  
  _Ver datos de red_
ip addr

_Ver IP de maquina_
nmap [IP]

_Hacer ping de alguna maquina_
ping [IP]

_Crear directorios_
mkdir

_Ver procesos, con parametro -aux se ven procesos activos_ 
_Con top se ven procesos en tiempo real, es mas interactivo_
ps -aux
top
pstree
htop `debe instalarse`

_Concatenar comandos_
|

_Buscar_
grep 
find 

_Matar procesos_
kill -9 [nombre]

_Ver que usuario esta usando el sistema_
whoami

_Entrar como super usuario `root`_
sudo su
sudo -i
su root

_Establecer contraseñas_
sudo passwd [usuario]

_Crear archivos_
touch

_Editar archivos de texto_
vim
nano

_Enlistar lo que contiene el directorio actual_
ls -l

_Mostrar contenido del archivo_
cat 
more
less

_Ver usuarios y sus datos_
cat /etc/passwd

_Ver datos de la memoria_
  sudo dmidecode --type 17
  cat/proc/meminfo

_Recorrer procesos actuales y leer cuantos KB/s usa cada uno_
  for file in /proc/*/status ; do awk '/VmSwap|Name/{printf $2 " " $3}END{ print ""}' $file; done | sort -k 2 -n -r | less

_Comando para leer memoria disponible_
  free -h

_Comando para dar prioridad a la memoria swap_
  swapon

_Comando Swampiness: editar # de cuanto porcentaje de memoria usa en RAM_
  cat /proc/sys/vm/swappiness
  
_Crear un disco de memoria RAM_
sudo mkdir /mnt/ram_disk

_Montar un sistema de archivos usando RAM_
sudo mount -t tmpfs -o size=1024m new_ram_disk /mnt/ram_disk

_Ver detalles de directorios_
df -h

_Ver tamaño de archivo_
  du -h archivo.png

_Ver fecha de creación, último acceso_
  stat archivo.png

_Tipo de archivo_
  file archivo.png
  
_Propietario y grupo, lista de permisos. Cambio de propietario, otorgar permisos_
  chown user1 archivo.png
  chmod 777 archivo.png 
  
_Mostrar el espacio en disco usado_ 
  df -h
  
_Mount: Montaje de dispositivos en el sistema de archivos_
  /etc/fstab 
  mount /dev/cdrom /mnt

_Gparted: Administra las particiones_
  sudo apt install gparted
  
_gnome-disk-utility: Muestra información sobre el disco_
  sudo apt install gnome-disk-utility

_Matar un proceso_
  kill -9 $PID
  
  _Ver version de bash_
  bash --version

_Ver ubicación de los intérpretes_ 
  echo $SHELL

_Ver todos los shells instalados_
  cat /etc/shells
 
_Cambiar bash a ksh_
  chsh -s /bin/zsh 

_Ejecutarlo scripts_
./script.sh
bash script.sh

_Imprimir_
echo

_Inicio de scripts en bash: `shebang`_
#!/bin/bash

_Dar permisos de ejecutar a scripts_
chmod +x script.sh
chmod 755 script.sh

_Declarar variables y asignarles un valor_
NAME=$(hostname)

_Debugg_
~/scripts> bash -x script.sh 

_Instalar paquetes_
dpkg -t [nombre]

_Formato basico de programacion en bash_
**if** [ condicion ];
then
 accion1
else
 accion2
fi

**for** i in variable
do
 accion1 $i
done

**while** [ variable ]
do
  accion1
  accion2
done

**function** F1()
{
accion1
}
F1

_Entrada de usuario_
read variable

_Servidor de Software_
  docker pull store/gitlab/gitlab-ce:10.2.4-ce.0

_Servidor DHCP_
  docker pull sw4iot/isc-dhcp
  docker pull gartz/simple-dns

_Servidor SSH, FTP, SAMBA_
  docker pull itsthenetwork/nfs-server-alpine
  docker pull stanback/alpine-samba

_Servidor FTP y Servidor Web_
  docker pull stilliard/pure-ftpd
  docker pull inwt/r-shiny

_Servidor de Respaldos_
  docker pull nextcloud

_Servidor Proxy_
  docker pull minimum2scp/squid

_Servidor de Logs_
  docker pull splunk/splunk 
  
_Kali Linux_
  docker pull kalilinux/kali-linux-docker
  
_Ubuntu_
  docker pull ubuntu
  
_Ver datos de docker_
sudo docker info

_Ver imagenes descargadas_
sudo docker images

_Descargar version de ubuntu mas actual_
sudo docker pull ubuntu:latest

_Para correr imagenes_
docker run [images name]

_Ver los contenedores que esten UP. Para ver incluso los contenedores que ya terminaron de ejecutar se usa -a_
docker ps
docker ps -a

_Correr un contenedor de forma interactiva (i) y abrir su terminal (t). Con el parámetro -v se va a crear un volumen donde se le pone ruta de host y del cliente para que se guarden datos ahi, ya que al borrar contenedores se borran los datos obtenidos._
docker run -ti ubuntu
docker run -v /tmp://cosas nginx:alpine ash

_Se puede correr un contenedor y ser borrado apenas se sale_
docker run -ti --rm [image]

_Comando para correr comandos de fondo_
docker run -d (contenedor)

_Comando para asignar nombre a contenedor_
docker run --name (nombre) (contenedor)

_Detener contenedores_
docker stop (name) (id)

_Borrar contenedores_
docker rm (name) (id)

_Borrar imagenes_
docker rmi (name:version) (ID)

_Comando FROM que toma que imagen base está siendo utilizada_
FROM ubuntu

_Comando RUN para realizar acciones_
RUN echo "Hola"

_Con el comando ADD se puede agregar archivos tipo fichero cuando se vaya a crear una imagen_
ADD index.html /var/www/index.html

_Comando ENV para agregar variables_
ENV variable1= "valor1"

_Ejecutar un comando al arrancar el contenedor. Con CMD se modifica el primer comando que se usará_
CMD["uname","-a"]

_ Publicar puertos de la imagen: Con EXPOSE se declara que puerto tcp va a estar open para conexión de red. Para poder habilitar el puerto, se entra con el comando run y una variable -p especificando los puertos del host y del contenedor
EXPOSE 80

_Ver contraseñas en linux_
  /etc/passwd
  /etc/shadow
  sudo passwd root
  
_Ver contraseñas en windows_
  lsadump::sam sam3.hiv system.hiv
  `revisar editor de registro HKEY LOCAL MACHINE SAM export`
  
_Cracking Hashes_
  john --show passwords.txt
  cat hashes.txt

_Ver version de GUI de nmap_
  zenmap

_uso de firewall_
  sudo apt-get install iptables
  sudo iptables -L -v
  sudo iptables -A INPUT -p tcp --dport [numero de puerto] ACCEPT
  sudo iptables -A INPUT -j DROP
  sudo iptables -A INPUT -s [IP] -j ACCEPT
  sudo iptables -A INPUT -s [IP] -j DROP

_Descargar ICMP /Broadcast_
/etc/sysctl.conf
net.ipv4.icmp_echo_ignore_all = 1
net.ipv4.icmp_echo_ignore_broadcasts = 1
sysctl -p

_Ejecucion de parches_
sudo apt update / sudo ap upgrade
sudo pacman -Syuu
yum -y update
`Windows Update`

_Gestion de logs_
/var/log/auth.log
/var/log/message # Todos los logs disponibles del sistema 
/var/log/auth.log # logs de autentificacion
/var/log/kern.log # Logs del Kernel
/var/log/cron.log # logs de crond 
/var/log/maillog # logs del correo del servidor
/var/log/boot.log # Logs de inicio del sistema
/var/log/mysqld.log # Logs de MySQL 
/var/log/apache/access.log # Logs de Apache
/var/log/secure # logs de autentificacion
/var/log/utmp # registro de inicios de sesion
/var/log/wtmp 
/var/log/yum.log # Log de Yum
