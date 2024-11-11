# About Linux

Start typing here...


====Directorios====

/bin , /sbin , /usr/bin , /usr/sbin : Contienen archivos ejecutables esenciales y comandos del sistema
/etc : Archivos de configuración el sistema
/home : Directorios personales de los usuarios
/var : Datos variables como registros y archivos de bases de datos

====Comandos====
mount : Montar directorios
pwd : Obtener la ruta del directorio actual
cd : Cambiar de directorio
ls : Listar directorios
ls -lS : Lista los directorios ordenados por tamaño
date : Retorna el dia
cal : Retorna el calendario del mes actual
uptime : Retorna el promedio de uso de la pc
cat : Visualizacion de algun archivo
whoami : Retorna el usuario actual
history : Retorna el historial de comandos de la terminal
!<id> : Retorna el comando del historial con el id dado
head :
less :
tail :
touch <nombre> : Crear archivos
mkdir <nombre> : Crear directorios
man :
rm :
mv <archivo> <directorio> : Mueve un archivo a otro directorio
mv <archivo> <nombre> : Renombra un archivo
free : Retorna la memoria libre
df -h : Retorna espacio en disco
ps :
cut :
diff :
grep :
more : Si un comando retorna mucha información, el more nos deja verlo desde arriba y cargar la información con ENTER o SPACE
sudo su: Sale al usuario root


(root)useradd -m <nombre> -G <grupo> -s /bin/bash (-g es grupo principal, -G es grupo secundario)
(root)passwd <nombre> : Le pone o cambia la contraseña al usuario
su <nombre> : login a ese usuario
usermod -a -g <grupo> <nombre> : Agregar usuario a grupo


¿Como asignar o quitar permisos a un grupo?
¿Como poner y quitar usuarios de un grupo?

A nivel fichero r=leer w=escribir x=ejecutar
A nivel directorio r=listar w=modificar x=acceder

===chmod===
owner group other
4 2 1
r w x

chown :
sed :
htop : Ver los procesos que se están ejecutando y la memoria que ocupan
sudo -i : Entrar como root
groupadd : Agregar un nuevo grupo
usermod :
usermod -L <nombre> : Bloquea un usuario

cat /etc/passwd : Directorio de usuarios con sus grupos

-----------------------------------------------------------------------
Podemos generar un sshkey para evitar tener que hacer login cada que queramos conectarnos de un servidor a otro, para eso usamos:
ssh-keygen , por defecto lo guarda en /home/<user>/.ssh
ssh-copy-id <server ip>
Ahora cada que queramos conectarnos no hace falta hacer login
ssh <server ip>
scp *.gz <server2_PRIVATE_IP>:~/

tar -xvf -xzf -xcf

umask :

awk :
awk -F :

apt autoremove : Borra los paquetes deprecados
sudo apt clean : Borra paquetes almacenados en cache