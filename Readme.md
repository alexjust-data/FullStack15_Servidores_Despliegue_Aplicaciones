
## AWS

Iniciamos con el video **1.mp4**

---

**trucos**

* `Ctrl+r` : es un buscador de comandos antiguos, has de decirle las palabras que quieres buscar
* `sudo !!` : cuando te olvidas poner sudo en el comando, esto te permite ejecutar ell mismo comando que antes con sudo delante

---

![](img/1.png)

---

```sh
Despliegue_AWS ls
    web15.pem

# usuario de acceso con ip
Despliegue_AWS ssh ubuntu@54.224.151.83
    "The authenticity of host '54.224.151.83 (54.224.151.83)' can't be established.
    ED25519 key fingerprint is SHA256:18BE2tcCHLs3H3pAK3aRXblKUhQ56RXbHu8KKBVN/ZM.
    This key is not known by any other names.
    Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
    Warning: Permanently added '54.224.151.83' (ED25519) to the list of known hosts.
    ubuntu@54.224.151.83: Permission denied (publickey)."

# se ha guardado laprimera vez esta huella: SHA256:18BE2tcCHLs3H3pAK3aRXblKUhQ56RXbHu8KKBVN/ZM
Despliegue_AWS ssh ubuntu@54.224.151.83
    ubuntu@54.224.151.83: Permission denied (publickey).

Despliegue_AWS ssh -i web15.pem ubuntu@54.224.151.83
    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    @         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    Permissions 0644 for 'web15.pem' are too open.
    It is required that your private key files are NOT accessible by others.
    This private key will be ignored.
    Load key "web15.pem": bad permissions
    ubuntu@54.224.151.83: Permission denied (publickey).

# protejemos el archivo
Despliegue_AWS chmod 600 web15.pem 

    Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 6.2.0-1017-aws x86_64)

    * Documentation:  https://help.ubuntu.com
    * Management:     https://landscape.canonical.com
    * Support:        https://ubuntu.com/advantage

    System information as of Tue Feb  6 14:30:07 UTC 2024

    System load:  0.00146484375     Processes:             95
    Usage of /:   20.5% of 7.57GB   Users logged in:       0
    Memory usage: 21%               IPv4 address for eth0: 172.31.39.104
    Swap usage:   0%

    Expanded Security Maintenance for Applications is not enabled.

    0 updates can be applied immediately.

    Enable ESM Apps to receive additional future security updates.
    See https://ubuntu.com/esm or run: sudo pro status


    The list of available updates is more than a week old.
    To check for new updates run: sudo apt update


    The programs included with the Ubuntu system are free software;
    the exact distribution terms for each program are described in the
    individual files in /usr/share/doc/*/copyright.

    Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
    applicable law.

    To run a command as administrator (user "root"), use "sudo <command>".
    See "man sudo_root" for details.

ubuntu@ip-172-31-39-104:~$ 

# para cerrar --> ubuntu@ip-172-31-39-104:~$ logout 
```

```sh
ubuntu@ip-172-31-39-104:~$ pwd
    /home/ubuntu

# ¿quien está conecta al servidor?
ubuntu@ip-172-31-39-104:~$ who
ubuntu   pts/0        2024-02-06 14:30 (77.243.86.2)

# creo archivo hello
ubuntu@ip-172-31-39-104:~$ touch hello
ubuntu@ip-172-31-39-104:~$ ls
    hello

# los archivos ocultos en formato lista
ubuntu@ip-172-31-39-104:~$ ls -l /
    total 64
    lrwxrwxrwx   1 root root     7 Dec  7 02:10 bin -> usr/bin
    drwxr-xr-x   4 root root  4096 Dec  7 02:15 boot
    drwxr-xr-x  15 root root  3200 Feb  6 12:31 dev
    drwxr-xr-x  93 root root  4096 Feb  6 12:31 etc
    drwxr-xr-x   3 root root  4096 Feb  6 12:31 home
    lrwxrwxrwx   1 root root     7 Dec  7 02:10 lib -> usr/lib
    lrwxrwxrwx   1 root root     9 Dec  7 02:10 lib32 -> usr/lib32
    lrwxrwxrwx   1 root root     9 Dec  7 02:10 lib64 -> usr/lib64
    lrwxrwxrwx   1 root root    10 Dec  7 02:10 libx32 -> usr/libx32
    drwx------   2 root root 16384 Dec  7 02:13 lost+found
    drwxr-xr-x   2 root root  4096 Dec  7 02:10 media
    drwxr-xr-x   2 root root  4096 Dec  7 02:10 mnt
    drwxr-xr-x   2 root root  4096 Dec  7 02:10 opt
    dr-xr-xr-x 158 root root     0 Feb  6 12:31 proc
    drwx------   4 root root  4096 Feb  6 12:31 root
    drwxr-xr-x  25 root root   860 Feb  6 14:30 run
    lrwxrwxrwx   1 root root     8 Dec  7 02:10 sbin -> usr/sbin
    drwxr-xr-x   8 root root  4096 Dec  7 02:17 snap
    drwxr-xr-x   2 root root  4096 Dec  7 02:10 srv
    dr-xr-xr-x  13 root root     0 Feb  6 12:31 sys
    drwxrwxrwt  11 root root  4096 Feb  6 12:32 tmp
    drwxr-xr-x  14 root root  4096 Dec  7 02:10 usr
    drwxr-xr-x  13 root root  4096 Dec  7 02:13 var

ubuntu@ip-172-31-39-104:~$ pwd
/home/ubuntu

ubuntu@ip-172-31-39-104:~$ cd ..
ubuntu@ip-172-31-39-104:/home$ ls
    ubuntu
ubuntu@ip-172-31-39-104:/home$ ls -l /
    total 64
    lrwxrwxrwx   1 root root     7 Dec  7 02:10 bin -> usr/bin
    drwxr-xr-x   4 root root  4096 Dec  7 02:15 boot
    drwxr-xr-x  15 root root  3200 Feb  6 12:31 dev
    drwxr-xr-x  93 root root  4096 Feb  6 12:31 etc
    drwxr-xr-x   3 root root  4096 Feb  6 12:31 home
    lrwxrwxrwx   1 root root     7 Dec  7 02:10 lib -> usr/lib
    lrwxrwxrwx   1 root root     9 Dec  7 02:10 lib32 -> usr/lib32
    lrwxrwxrwx   1 root root     9 Dec  7 02:10 lib64 -> usr/lib64
    lrwxrwxrwx   1 root root    10 Dec  7 02:10 libx32 -> usr/libx32
    drwx------   2 root root 16384 Dec  7 02:13 lost+found
    drwxr-xr-x   2 root root  4096 Dec  7 02:10 media
    drwxr-xr-x   2 root root  4096 Dec  7 02:10 mnt
    drwxr-xr-x   2 root root  4096 Dec  7 02:10 opt
    dr-xr-xr-x 155 root root     0 Feb  6 12:31 proc
    drwx------   4 root root  4096 Feb  6 12:31 root
    drwxr-xr-x  25 root root   860 Feb  6 14:30 run
    lrwxrwxrwx   1 root root     8 Dec  7 02:10 sbin -> usr/sbin
    drwxr-xr-x   8 root root  4096 Dec  7 02:17 snap
    drwxr-xr-x   2 root root  4096 Dec  7 02:10 srv
    dr-xr-xr-x  13 root root     0 Feb  6 12:31 sys
    drwxrwxrwt  11 root root  4096 Feb  6 12:32 tmp
    drwxr-xr-x  14 root root  4096 Dec  7 02:10 usr
    drwxr-xr-x  13 root root  4096 Dec  7 02:13 var
```

**SISTEMA DE FICHEROS**

* **/etc** : ficheros de configuración del sistema
* **/etc/init.d/** : Scripts que se ejecutan cuando arranca el sistema en
* **/etc/rc.d/** : Scripts que se ejecutan cuando arranca el sistema en
* **/home y /rooT** : ficheros de configuración del sistema
  - **/home/goku** : usuario del sistema
  - **/home/vegeta** : usuario del sistem
* **/root** : es la casa de root (superadministrador)
* **/sbin** : ejecutables de comandos  --> los programas
* **/tmp** : almacenar datos, serán eliminados cuando el sistema se reinicio o necesite espacio
* **/usr/bin**: ejecutables para cualquier usuario
* **/usr/lib**: librerías de programación (C/C++ habitualmente)
* **/usr/local**: archivos locales (desarrollados por ti)
* **/usr/sbin**: ejecutables sólo para administradores
* **/usr/share**: datos compartidos (documentación)
* **/usr/src**: código fuente del kernel de Linux
* **/var/log**: archivos de log
* **/var/mail**: buzones de e-mail de los usuarios
* **/var/run**: descriptores de procesos o sockets
* **/var/www**: archivos servidos por el servidor web

**JUGANDO CON ARCHIVOS Y DIRECTORIOSs**

* **mkdir `<foldername>`** : Crear un directorio
* **rmdir `<foldername>`** : Elimina recursivamente directorios y archivos.
* **rm -rf `<foldername>`** : PELIGRO: rm -rf / como root borraría todo el disco 
* **touch `<filename>`** : Crear un archivo vacío
* **nano `<filename>`** : Editar un archivo
* **vi `<filename>`**: Editar un archivo
* **cat `<filename>`** : Muestra el contenido de un fichero (ideal para archivos pequeños)
* **more `<filename>`** : Permite leer un fichero grande poco a poco
* **head `<filename>`** : Muestra las primeras líneas del fichero
* **tail `<filename>`** : Muestra las últimas líneas del fichero
* **tail -f `<filename>`** : Muestra en tiempo real el último contenido del fichero
* **wc `<filename>`** : Cuántas palabras tiene un archivo de texto
* **wc -l `<filename>`** : Cuántas líneas tiene un archivo de texto
* **diff `<file1> <file2>`** : Muestra las diferencias entre dos archivos
* **sort `<filename>`** : Ordena las líneas de un archivo de texto
* **grep `<filename> <query>`** : Filtra contenidos. Busca <query> en <filename>. Permite expresiones regulares.
* **cp `<source> <target>`** : Copia un archivo de un sitio a otro
* **mv `<source> <target>`** : Mueve o renombra un archivo
* **rm `<filename>`** : Eliminar un archivo
* **rm -f `<filename>`** : Para que no pregunte si estamos seguros de eliminar
* **ln `<source> <target>`** : Crea un alias del archivo. Si eliminamos el alias se elimina el archivo.
* **ln -s `<source> <target>`** : Crea un acceso directo. Si eliminamos el acceso directo, NO elimina el archivo. También conocido como enlace simbólico.

---

https://www.tecmint.com/35-practical-examples-of-linux-find-command/

* **find . -name `<filename>`** : Busca un archivo de nombre filename en el directorio actual y subdirectorios.
* **find / -name `<filename>`** : Busca un archivo de nombre filename en todo el sistema
* **man `<command name>`** : Muestra el manual del programa o comando

**USUARIOS GRUPOS Y PERMISOS**

**Usuarios y grupos**

* Linux es un sistema multiusuario
* Los usuarios no sólo son personas, también pueden ser servicios
(como el servidor web, servidor de correo, etc.)
* Las cuentas de usuario, pueden pertenecer a uno o varios grupos
* Hay unos grupos especiales de administrador (admin o sudo)
* Suele haber una cuenta de super-administrador: root
* En Ubuntu, el login con root está deshabilitado por seguridad

**Permisos de archivos**

* Cada archivo o carpeta pertenece a un usuario y un grupo
* Los permisos de Linux permiten definir tres tipos de acceso:
   - Lectura
   - Escritura y/o borrado
   - Ejecución (para archivos o scripts ejecutables)
* Estos tres tipos de acceso, se definen en tres niveles:
   - Propietario del archivo o carpeta
   - Usuarios del mismo grupo del archivo o carpeta
   - Otros usuarios fuera del grupo

---
![](img/2.png)

---
![](img/4.png)

---


**Modificar permisos de archivos y carpeta**

* **chmod `<target>`±rwx `<filename>`**
    - `<target>` = a / u / g / o
    - a = all / u = user/owner / g = group / o = other
* **chmod u+wrx backup** : Da (+) todos (rwx) los permisos para el propietario (u)
* **chmod a+x backup** : Da (+) permisos de ejecución (x) para todos (a)
* **chmod g+rx backup**: Da (+) permisos de lectura y ejecución (rx) a los usuarios del grupo (g)
* **chmod o-rw backup**: Quita (-) permisos de lectura y escritura (rw) a los otros usuarios (o)

* **adduser <username>** : Crear un usuario y un grupo con el mismo nombre del usuario y mete al usuario en dicho grupo. Esto lo registra en /etc/passwd y /etc/group


**Ejecutando como administrador**

* **sudo `<command>`** : Ejecuta lo que viene seguido de sudo como administrador. El usuario debe tener permiso de sudoer.
* **deluser `<username>`** : Elimina un usuario del sistema. Lo elimina de /etc/passwd
* **addgroup `<groupname>`** : Crea un grupo añadiéndolo a /etc/group
* **delgroup `<groupname>`** : Elimina un grupo de /etc/group No elimina los usuarios de ese grupo
* **adduser `<username> <groupname>`** : Añade el usuario al grupo en /etc/group
* **adduser `<username>` sudo** : Añade el usuario al grupo sudo en /etc/group Si eres sudo, tienes permisos para todo, da igual los permisos del archivo
* **chown `<newowner> <filename>`** : El archivo <filename> pasa a pertenecer a <newowner>
* **chown -R `<newowner> <foldername>** : Cambiar el propietario de <foldername> y todos sus archivos y subdirectorios. Es un cambio recursivo (-R)
* **chgrp `<newgroup> <filename>`** : El archivo <filename> pasa a pertenecer a <newgroup>
* **chgrp -R `<newgroup> <foldername>`** : Cambiar el grupo de <foldername> y todos sus archivos y subdirectorios. Es un cambio recursivo (-R)
* **chown `<user>:<group> <filename>`** : Cambiar el propietario y grupo a la vez
* **passwd `<username>`** : Cambiar contraseña de un usuario


**Apagar y reiniciar** En necesario que seas administrador o sudoer

* **shutdown** :  Apaga el servidor
* **reboot** : Reiniciar el servidor


**Instalando y desinstalando software**

Gestor de paquetes `apt-get`

En las distribuciones basadas en Debian (como Ubuntu), se puede instalar y desinstalar software a través del gestor de paquetes:`apt-get`
Este gestor se descarga paquetes ya compilados desde Internet para tu distribución y los instala en el sistema (descargando también otras dependencias si hiciera falta).

* **apt-get install `<package>`** : Instala el paquete `<package>` en el sistema
* **apt-get purge `<package>`** : Desinstala el paquete `<package>` del sistema
* **apt-get update** : Actualiza los repositorios de software para buscar actualizaciones
* **apt-get upgrade** : Instala todas las actualizaciones de paquetes


**Gestión de procesos**


* **top** [top: el CTRL+ALT+SUPR de Linux] : Muestra en tiempo real información de los los procesos ordenados por consumo de CPU (de mayor a menor). Para salir, pulsar la letra Q (de quit)
* **ps aux** : Muestra todos los procesos en ejecución con mucha información (no sólo los que más CPU consumen, com hace top)
* **ps aux | more** : Para poder ir viéndolos poco a poco
* **ps aux | grep `<command>`** : Para buscar un processo <command>
* **kill `<pid>`** : Mata el proceso número <pid>. Sólo vale para procesos nuestros.
* **sudo kill `<pid>`** : Para poder matar procesos de otros usuarios


**Gestionando el espacio en disco**

* **df** : Muestra el espacio libre de las particiones en bytes
* **df -h** : Muestra el espacio libre legible para humanos (h)
* **du `<folder>`** : Muestra lo que ocupa cada archivo dentro de `<folder>`
* **du -ch `<folder>`** : Más rápido (c) y entendible para humanos (h)


**Seguridad**

Consejos de seguridad

* Cambiar las contraseñas como mucho trimestralmente
* Cambia los puertos por defecto de los servicios que puedas
* Oculta los números de versión de los servicios
* Protege con SSL y autenticación HTTP los accesos de
administración de tus plataformas
* No uses /admin /adm /cms /backend /backoffice (sé original)
* Usa un firewall
* Haz copias de seguridad diarias...y haz ensayos de recuperación
* Mantén actualizado tu software
* Elimina los humanos: son la mayor brecha de seguridad


`fail2ban`

* Es un servicio que se encarga de proteger el sistema sobre ataques a diferentes servicios mediante monitorización de los logs (entre otros aspectos).
* Cuando detecta una amenaza, reacciona baneando la IP del posible atacante.
* A veces se pasa de protector y nos deja sin acceso a nosotros
* Es muy sencillo de configurar

Instalación `fail2ban`

```sh
sudo apt-get install fail2ban
```

* **`/etc/fail2ban/jail.conf`** : Fichero de configuración
* **`/etc/fail2ban/filter.d/`** : Configuración de filtros y acciones


**Comprimir y descomprimir**

Hay varias opciones, pero lo más habitual es usar tar + gzip:

* tar es un comando que empaqueta (junta varias carpetas en un archivo) pero no comprime
* gzip es un comando que comprime archivos (similar a zip)
* Se utiliza tar con la opción -z para comprimir en gzip
* También podemos usar zip, pero en Linux se usa mas .tar.gz

* **tar -czvf `<foo>`.tar.gz `<folder>`** : Comprime el directrorio <folder> en un archivo <foo>.tar.gz
* **tar -xzvf `<foo>`.tar.gz** : Descomprime <foo>.tar.gz en el directorio local
* **zip -r `<foo>`.zip `<folder>`** : Comprime el directrorio <folder> en un archivo <foo>.zip ACHTUNG: zip no suele venir instalado en Linux.
* **unzip <foo>.zip** : Descomprime el archivo <foo>.zip en el directorio actual. ACHTUNG: unzip no suele venir instalado en Linux.


**Redirección** 


En Bash podemos redirigir la salida de los comandos para que, en lugar de mostrarnos el resultado por pantalla, nos lo almacenen en un fichero. También podemos redirigir la entrada, para que un comando en lugar de esperar un dato por pantalla (o teclado) directamente lo tome de un fichero.


* **echo “hi” > hello.txt** : Guarda la salida del comando “echo” en el fichero “hello.txt”. Si el fichero existe, machaca su contenido.
Si no existe el fichero, lo crea.
* **echo “hi” >> hello.txt** : Igual que el anterior, pero: Si el fichero existe, añade el contenido al final. Si no existe el fichero, lo crea.
* **patch index.js < v1.patch** : Pasa el contenido de “hello.txt” como argumento al comando hello.


**Pipes**

Los pipes nos permiten pasar la información de un comando a otro como si fueran filtros. La salida de un comando se transforma en la entrada de otro comando.

* `cat quixote.txt | grep Rocinante | wc -l` : cat saca todo el contenido del fichero “quixote.txt” y se lo pasa como entrada al comando “grep Rocinante” que filtrará las líneas en las que aparece la palabra “Rocinante” y éste le pasa dicho resultado al comando “more” que nos permite ir leyendo poco a poco los resultados.


> [!NOTE]
> Repositorio de comandos:  http://www.commandlinefu.com/



## Scripting

* La bash permite almacenar comandos en un fichero de texto y ejecutarlos como si fuera programas.
* Proporciona incluso instrucciones de control de flujo y bucles
* Los ficheros deben tener permisos de ejecución para poder ser
tratados como programas.
* En la primera línea, se ha de indicar cuál es el intérprete que se
debe utilizar.
* Podemos utilizar otros lenguajes de scripting (python, php, perl...)

```sh
#!/bin/bash
# This is a comment
echo “My command is called $0\n” echo “The first argument is $1\n” for item in ‘$(ls)’
do
echo “- $item\n” done
```

```sh
#!/bin/bash para scripts bash o shellscript 
#!/bin/python para scripts python 
#!/bin/php para scripts php
```

**Variables implícitas** 

* **$@** lista de parámetros recibida por el comando
* **$0** nombre del propio comando/archivo
* **$1** primer parámetro
* **$2** segundo parámetro
...
* **$n** n-ésimo parámetro
* **`$?`** resultado de la salida del último comando (0 es OK, !=0 es KO) $$ número de proceso que se ejecuta
* **$#** número de parámetros recibidos por el comando


```sh
# Definición de variables
name=“hello” 
counter=0
```

```sh
# Uso de variables
echo “Hello $name” 
echo “Hello ${name}” 
echo “$counter times” 
echo “${counter} times”
```

```sh
# Usando la salida de un comando
files=$(ls) # Ejecuta el comando ls y guarda su salida en “files” 
echo $files
```


```sh
# Condicionales

if <condition> then
<stuff>
else
<otherstuff>
fi
```


```sh
# Condiciones de las condicionales

if cp $source $target # si se ejecuta bien cp
if test -f $source # si $source es un fichero
if [ -f “$source” ] # si $source es un fichero
if [ -d “$source” ] # si $source es un directorio if [ -e “$source” ] # si $source existe
if $source = $target # si $source es igual a $target
if $source != $target # si $source es distinto a $target
```

```sh
# Condiciones de las condicionales: numéricas

if $numA -eq $numB # $numA == $numB 
if $numA -ne $numB # $numA != $numB 
if $numA -ge $numB # $numA >= $numB 
if $numA -gt $numB # $numA > $numB 
if $numA -le $numB # $numA <= $numB 
if $numA -lt $numB # $numA < $numB
```

```sh
# Case

case <variable> in <value1>)
<stuff>
;;
<value2> | <value3>)
<otherstuff>
;; *)
;; esac
```

```sh
# Bucle for

for file in $(ls) 
do
    <stuff>
done
```

**Salida**

Cuando nuestro programa acaba bien, debe devolver `exit 0`. Si algo va mal, deberemos devolver un número distinto de cero (lo suyo es diferenciar los tipos de error con números).

```sh
# Funciones

function <name> ()
{
    <commands>
    return <int>
}
```


**Ejecutar en background**

* **`<command>` &** : Ejecutar en background sin deconexión

ACHTUNG: No vale para ejecutar en segundo plano y desconectarnos. El sistema puede matar el proceso pasado un tiempo.

* **nohup `<command>` &** : Ejecutar en background con desconexión. La posible salida que pueda sacar el comando, la almacenará en un archivo llamado nohup.out


**Programando tareas automáticas**


El cron

* Todos los sistemas Linux incluyen un programador de tareas: cron
* Nos permite programar comandos que se ejecuten automáticamente
* Básicamente, se almacena en un fichero la información de programación y el comando a ejecutar
* Como máximo podemos ejecutar repetitivamente hasta una vez por minuto


**Programando tareas para mi usuario**

* **crontab -e** : 

---

![](img/5.png)

---

* **sudo nano /etc/crontab** : Programando tareas de sistema

---
![](img/6.png)

---


**Ejemplo crontab -e**

* `30 10 * * 1 /usr/bin/who >> /home/who.txt` : Todos los lunes a las 10:30
* `0,30 * * * 1 /usr/bin/who >> /home/who.txt`: Todos los lunes a en punto o a y media de todas las horas
* `*/15 * * * * /usr/bin/who >> /home/who.txt` : Cada 15 minutos
* `30 21 * * 6 /sbin/shutdown -h now` : Apaga el servidor los sábados a las 21:30. Sólo lo podría hacer root.

https://es.wikipedia.org/wiki/Cron_(Unix)

**Ejemplo /etc/crontab** 


* `30 10 * * 1 larry /usr/bin/who >> /home/who.txt` : Todos los lunes a las 10:30
* `0,30 * * * 1 steve /usr/bin/who >> /home/who.txt` : Todos los lunes a en punto o a y media de todas las horas
* `*/15 * * * * sergei /usr/bin/who >> /home/who.txt` : Cada 15 minutos
* `30 21 * * 6 root /sbin/shutdown -h now` : Apaga el servidor los sábados a las 21:30. Sólo lo podría hacer root.

# NGINX

El todo en uno : servidor web, proxy invers y balanceador de carga.

NGINX es un software de servidor web de alto rendimiento, conocido por su estabilidad, rico conjunto de características, configuración simple, y bajo consumo de recursos. Originalmente diseñado para servir contenido estático de manera eficiente, NGINX se ha expandido para ofrecer una solución de red completa, incluyendo capacidades de proxy inverso, proxy de correo electrónico (IMAP/POP3), y un balanceador de carga.

**Servidor Web**

Como servidor web, NGINX es conocido por su habilidad para manejar un gran número de conexiones simultáneas con un bajo uso de memoria y CPU. Esto lo hace ideal para sitios web con mucho tráfico y para servir archivos estáticos (como imágenes, CSS, y JavaScript), donde supera a otros servidores web como Apache en términos de eficiencia y velocidad.

**Proxy Inverso**

En su función de proxy inverso, NGINX actúa como intermediario para solicitudes de clientes, reenviándolas a servidores internos. Esto puede ser usado para distribuir la carga entre varios servidores, mejorar la seguridad ocultando la verdadera ubicación de los servidores internos, manejar el cifrado SSL/TLS, y servir contenido dinámico y estático de manera eficiente.

**Balanceador de Carga**

NGINX puede distribuir el tráfico entrante entre varios servidores traseros basándose en diferentes métodos de balanceo de carga, como round-robin, menos conexiones, y hash de IP. Esto mejora la disponibilidad y la redundancia de las aplicaciones web, permitiendo que los sitios web manejen volúmenes de tráfico más altos y proporcionen tiempos de respuesta más rápidos.

**Características Adicionales**

Alto rendimiento y manejo eficiente de conexiones: NGINX utiliza un modelo de eventos asincrónicos para manejar múltiples conexiones, lo que le permite manejar miles de conexiones simultáneas en una máquina con hardware modesto.

Configuración flexible: La configuración de NGINX es conocida por su potencia y flexibilidad, permitiendo a los usuarios ajustar el servidor para optimizar el rendimiento y la seguridad.

* Soporte para WebSocket: NGINX soporta el protocolo WebSocket, permitiendo aplicaciones web en tiempo real.

* Cifrado SSL/TLS: NGINX puede manejar la terminación SSL/TLS, descriptografía de solicitudes antes de pasarlas a los servidores de aplicación internos, y cifrando las respuestas antes de enviarlas a los clientes, mejorando así la seguridad.

* Caching: NGINX puede almacenar en caché contenido dinámico y estático, reduciendo la carga en los servidores de aplicación y mejorando el tiempo de respuesta para los usuarios finales.

Compresión: Reduce el tamaño de los datos enviados a los clientes, mejorando los tiempos de carga de las páginas.

**Uso**

NGINX se utiliza en una variedad de entornos, desde sitios web personales hasta algunas de las mayores propiedades de internet. Empresas como Netflix, Airbnb, y Dropbox usan NGINX para servir contenido de manera eficiente a millones de usuarios diariamente. Su capacidad para manejar un gran número de conexiones simultáneas con un uso eficiente de recursos lo hace ideal para sitios web de alto tráfico, aplicaciones web en tiempo real, y como parte de la infraestructura de microservicios.

```sh
➜  ~ sudo apt-get install nginx
```


```sh
# Conectando con AWS

➜  DESPLIEGUE cd Despliegue_AWS 
➜  Despliegue_AWS ssh -i web15.pem ubuntu@54.224.151.83
    Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 6.2.0-1017-aws x86_64)

    * Documentation:  https://help.ubuntu.com
    * Management:     https://landscape.canonical.com
    * Support:        https://ubuntu.com/advantage

    System information as of Wed Feb  7 13:03:41 UTC 2024

    System load:  0.0               Processes:             98
    Usage of /:   30.3% of 7.57GB   Users logged in:       0
    Memory usage: 24%               IPv4 address for eth0: 172.31.39.104
    Swap usage:   0%

    * Ubuntu Pro delivers the most comprehensive open source security and
    compliance features.

    https://ubuntu.com/aws/pro

    Expanded Security Maintenance for Applications is not enabled.

    25 updates can be applied immediately.
    To see these additional updates run: apt list --upgradable

    Enable ESM Apps to receive additional future security updates.
    See https://ubuntu.com/esm or run: sudo pro status


    *** System restart required ***
    Last login: Tue Feb  6 14:30:09 2024 from 77.243.86.2
    To run a command as administrator (user "root"), use "sudo <command>".
    See "man sudo_root" for details.

ubuntu@ip-172-31-39-104:~$ 

# instalando nginx
ubuntu@ip-172-31-39-104:~$ sudo apt-get install nginx
```

Te está diciendo que reinicará todos estos archivos, le das al tabulador para irte al ok y le das.

Ahora vamos a reinicar desde la consola de aws

---
![](/img/7.png)

---

o desde la consola 

> [!IMPORTANT]
> Acuerdate que antes de hacer esto en produccion deberías hacer una foto, `Snapshot` desde aws

```sh
# reinicio
ubuntu@ip-172-31-39-104:~$ sudo reboot

# vuelvo a conectar con el kernel nuevo
ubuntu@ip-172-31-39-104:~$ Connection to 54.224.151.83 closed by remote host.
Connection to 54.224.151.83 closed.
➜  Despliegue_AWS ssh -i web15.pem ubuntu@54.224.151.83
    Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 6.2.0-1018-aws x86_64)

    * Documentation:  https://help.ubuntu.com
    * Management:     https://landscape.canonical.com
    * Support:        https://ubuntu.com/advantage

    System information as of Wed Feb  7 13:03:41 UTC 2024

    System load:  0.0               Processes:             98
    Usage of /:   30.3% of 7.57GB   Users logged in:       0
    Memory usage: 24%               IPv4 address for eth0: 172.31.39.104
    Swap usage:   0%

    * Ubuntu Pro delivers the most comprehensive open source security and
    compliance features.

    https://ubuntu.com/aws/pro

    Expanded Security Maintenance for Applications is not enabled.

    25 updates can be applied immediately.
    To see these additional updates run: apt list --upgradable

    Enable ESM Apps to receive additional future security updates.
    See https://ubuntu.com/esm or run: sudo pro status


    Last login: Wed Feb  7 13:03:41 2024 from 77.243.86.7
ubuntu@ip-172-31-39-104:~$ 
```

Hemos de configurar el cortafuegos

---

![](/img/8.png)

---

![](/img/9.png)

---

Incluimos el puerto de acceso HTTP con dns 0.0.0.0. para que pueda acceder todo el mundo, si quieres puedes decirle que solo puede acceder una direccion particular.

---
![](/img/10.png)


---

Ahora si te vas al browser y navegas a la ip que te ha dado antes

```sh
http://54.224.151.83/
```

verás que entras en `Welcome to nginx!`

```json
Welcome to nginx!  
Si ve esta página, el servidor web nginx se instaló correctamente y funciona. 
Se requiere configuración adicional.
```


```sh
# paro el servidor nginx
sudo systemctl stop nginx

# arranco del nuevo
sudo systemctl start nginx

# puedes ver los procesos abiertos
ubuntu@ip-172-31-39-104:~$ ps aux | grep nginx

root         424  0.0  0.2  55224  2284 ?        Ss   13:21   0:00 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
www-data     428  0.0  0.6  55856  6124 ?        S    13:21   0:00 nginx: worker process
ubuntu       796  0.0  0.2   7008  2304 pts/0    S+   13:51   0:00 grep --color=auto nginx
ubuntu@ip-172-31-39-104:~$ 

```

```sh
# recargar sin que deje de funcionar el servidor
sudo systemctl reload nginx

# permite comprobar si lo que has escrito de configuracion no la has cagado
sudo nginx-t
```

**configuracino**

* El fichero de configuracion está en `etc/nginx/nginx.conf`
* En `etc/nginx/nginx.conf` podemos incluir configuracion personalizada que sobreescriba parámetros por defecto (si no queremos tocar `etc/nginx/nginx.conf`)

```sh
# leamos el fichero de configuracion
ubuntu@ip-172-31-39-104:~$ less /etc/nginx/nginx.conf

    user www-data;
    worker_processes auto;
    pid /run/nginx.pid;
    include /etc/nginx/modules-enabled/*.conf;

    events {
            worker_connections 768;
            # multi_accept on;
    }

    http {

            ##
            # Basic Settings
            ##

            sendfile on;
            tcp_nopush on;
            types_hash_max_size 2048;
            # server_tokens off;

            # server_names_hash_bucket_size 64;
            # server_name_in_redirect off;

            include /etc/nginx/mime.types;
            default_type application/octet-stream;

            ##
            # SSL Settings
            ##

            ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3; # Dropping SSLv3, ref: POODLE
            ssl_prefer_server_ciphers on;

            ##
            # Logging Settings
            ##

            access_log /var/log/nginx/access.log;
            error_log /var/log/nginx/error.log;

            ##
            # Gzip Settings
            ##

            gzip on;

            # gzip_vary on;
            # gzip_proxied any;
            # gzip_comp_level 6;
            # gzip_buffers 16 8k;
            # gzip_http_version 1.1;
            # gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

            ##
            # Virtual Host Configs
            ##

            include /etc/nginx/conf.d/*.conf;
            include /etc/nginx/sites-enabled/*;
    }

```

**Configuración de nuestros sitios web**

* Con una sola instalación, podemos dar servicio a varios dominios o subdominios.
* En `/etc/nginx/site-available/` podemos incluir congifuracion de otros sitios que queramos configurar.
* Una vez configurados, debemos hacer un **acceso directo** (ln -s) el archivo a `/etc/nginx/sites-enabled/` para que nginx los sirva


```sh
# veamos todos los archivos de configuracion de nginx
ubuntu@ip-172-31-39-104:~$ cd /etc/nginx/
ubuntu@ip-172-31-39-104:/etc/nginx$ ls -l

total 64
drwxr-xr-x 2 root root 4096 May 30  2023 conf.d
-rw-r--r-- 1 root root 1125 May 30  2023 fastcgi.conf
-rw-r--r-- 1 root root 1055 May 30  2023 fastcgi_params
-rw-r--r-- 1 root root 2837 May 30  2023 koi-utf
-rw-r--r-- 1 root root 2223 May 30  2023 koi-win
-rw-r--r-- 1 root root 3957 May 30  2023 mime.types
drwxr-xr-x 2 root root 4096 May 30  2023 modules-available
drwxr-xr-x 2 root root 4096 Feb  7 13:07 modules-enabled
-rw-r--r-- 1 root root 1447 May 30  2023 nginx.conf
-rw-r--r-- 1 root root  180 May 30  2023 proxy_params
-rw-r--r-- 1 root root  636 May 30  2023 scgi_params
drwxr-xr-x 2 root root 4096 Feb  7 13:07 sites-available
drwxr-xr-x 2 root root 4096 Feb  7 13:07 sites-enabled
drwxr-xr-x 2 root root 4096 Feb  7 13:07 snippets
-rw-r--r-- 1 root root  664 May 30  2023 uwsgi_params
-rw-r--r-- 1 root root 3071 May 30  2023 win-utf
```

```sh
ubuntu@ip-172-31-39-104:/etc/nginx$ cd sites-enabled/
ubuntu@ip-172-31-39-104:/etc/nginx/sites-enabled$ ls -l
total 0
lrwxrwxrwx 1 root root 34 Feb  7 13:07 default -> /etc/nginx/sites-available/default
ubuntu@ip-172-31-39-104:/etc/nginx/sites-enabled$ 
```

esto es un link `lrwxrwxrwx 1 root root 34 Feb  7 13:07 default -> /etc/nginx/sites-available/default` directo al archivo `sites-available`

```sh
# miramos que hay dentro
ubuntu@ip-172-31-39-104:/etc/nginx/sites-enabled$ less default

server {
        listen 80 default_server;
        listen [::]:80 default_server;

        # SSL configuration
        #
        # listen 443 ssl default_server;
        # listen [::]:443 ssl default_server;
        #
        # Note: You should disable gzip for SSL traffic.
        # See: https://bugs.debian.org/773332
        #
        # Read up on ssl_ciphers to ensure a secure configuration.
        # See: https://bugs.debian.org/765782
        #
        # Self signed certs generated by the ssl-cert package
        # Don't use them in a production server!
        #
        # include snippets/snakeoil.conf;

        root /var/www/html; # <----- FIJATE EL DIRECTORI A LA RAIZ

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                try_files $uri $uri/ =404;
        }

        # pass PHP scripts to FastCGI server
        #
        #location ~ \.php$ {
        #       include snippets/fastcgi-php.conf;
        #
        #       # With php-fpm (or other unix sockets):
        #       fastcgi_pass unix:/run/php/php7.4-fpm.sock;
        #       # With php-cgi (or other tcp sockets):
        #       fastcgi_pass 127.0.0.1:9000;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #       deny all;
        #}
}


# Virtual Host configuration for example.com
#
# You can move that to a different file under sites-available/ and symlink that
# to sites-enabled/ to enable it.
#
#server {
#       listen 80;
#       listen [::]:80;
#
#       server_name example.com;
#
#       root /var/www/example.com;
#       index index.html;
#
#       location / {
#               try_files $uri $uri/ =404;
#       }
#}
(END)
```

Fíjate lo que te ha dicho

```sh
        root /var/www/html; # <----- FIJATE EL DIRECTORI A LA RAIZ

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.nginx-debian.html;
```


La página de inicio que te muestra 

```json
Welcome to nginx!  
Si ve esta página, el servidor web nginx se instaló correctamente y funciona. 
Se requiere configuración adicional.
```

Te la muetra porque aquí `/var/www/html` debe haber algo

```sh
# miremos que hay dentro 
ubuntu@ip-172-31-39-104:/etc/nginx/sites-enabled$ cd /var/www/html
ubuntu@ip-172-31-39-104:/var/www/html$ ls 
index.nginx-debian.html
ubuntu@ip-172-31-39-104:/var/www/html$ cat index.nginx-debian.html 

    <!DOCTYPE html>
    <html>
    <head>
    <title>Welcome to nginx!</title>
    <style>
        body {
            width: 35em;
            margin: 0 auto;
            font-family: Tahoma, Verdana, Arial, sans-serif;
        }
    </style>
    </head>
    <body>
    <h1>Welcome to nginx!</h1>
    <p>If you see this page, the nginx web server is successfully installed and
    working. Further configuration is required.</p>

    <p>For online documentation and support please refer to
    <a href="http://nginx.org/">nginx.org</a>.<br/>
    Commercial support is available at
    <a href="http://nginx.com/">nginx.com</a>.</p>

    <p><em>Thank you for using nginx.</em></p>
    </body>
    </html>
```
 Es esta página

 
```json
Welcome to nginx!  
Si ve esta página, el servidor web nginx se instaló correctamente y funciona. 
Se requiere configuración adicional.
```

Como en las instrucciones del fichero nginx te decía que si no sabías que fichero ver, busca : `index index.html | index.htm | index.nginx-debian.html;`

por esto está cargando este archivo 

```sh
ubuntu@ip-172-31-39-104:/var/www/html$ ls -l
total 4
-rw-r--r-- 1 root root 612 Feb  7 13:07 index.nginx-debian.html
```

Vamos a ver el arhivo

```sh
ubuntu@ip-172-31-39-104:/var/www/html$ ls -l
    total 4
    -rw-r--r-- 1 root root 612 Feb  7 13:07 index.nginx-debian.html
ubuntu@ip-172-31-39-104:/var/www/html$ ls -l /var/www/
    total 4
    drwxr-xr-x 2 root root 4096 Feb  7 13:07 html

# abrimos el archivo
ubuntu@ip-172-31-39-104:/var/www/html$ sudo nano index.html
```

El archivo está vacío

pero lo escribimos un **hola mundo** y guardamos

---
![](/img/12.png)

---

Vamos a https://startbootstrap.com/
copiamos una plantilla

Abro nuevo consola en mi terminal local

```sh
➜  ~ cd /Users/alex/Desktop/KEEPKODING/Servidores_Despliegue_Aplicaciones/template
➜  template ls -l
total 296
-rw-rw-r--@ 1 alex  staff   2407 Mar 25  2023 401.html
-rw-rw-r--@ 1 alex  staff   2407 Mar 25  2023 404.html
-rw-rw-r--@ 1 alex  staff   2338 Mar 25  2023 500.html
drwxrwxr-x@ 4 alex  staff    128 Mar 25  2023 assets
-rw-rw-r--@ 1 alex  staff  11617 Mar 25  2023 charts.html
drwxrwxr-x@ 3 alex  staff     96 Mar 25  2023 css
-rw-rw-r--@ 1 alex  staff  41881 Mar 25  2023 index.html
drwxrwxr-x@ 4 alex  staff    128 Mar 25  2023 js
-rw-rw-r--@ 1 alex  staff   9559 Mar 25  2023 layout-sidenav-light.html
-rw-rw-r--@ 1 alex  staff   9791 Mar 25  2023 layout-static.html
-rw-rw-r--@ 1 alex  staff   4075 Mar 25  2023 login.html
-rw-rw-r--@ 1 alex  staff   3508 Mar 25  2023 password.html
-rw-rw-r--@ 1 alex  staff   5600 Mar 25  2023 register.html
-rw-rw-r--@ 1 alex  staff  38311 Mar 25  2023 tables.html
```

**¿cual es el origen?**


* ¿cual es el origen? mi carpeta entera --> `scp template`
* ¿cuál es el destimo? el servidor --> `ubuntu@54.224.151.83`
* ¿donde quieres que te deje la carpeta? --> `/home/ubuntu`
* qué contraseña tienes para acceder a ubuntu? --> tu archivo : `-i web15.pen`
* quiero subir de forma recursvo para todo lo que hay dentro : `-r`

```sh
# para cargar
$ scp -r -i ../Despliegue_AWS/web15.pem ../template ubuntu@54.224.151.83:/home/ubuntu


# para descargar sería al revés
```

Ahora si te vas a la termina del aws y buscas la carpeta

```sh
# estas en la carpeta /var/www/html con cd te vas a home
ubuntu@ip-172-31-39-104:/var/www/html$ cd
ubuntu@ip-172-31-39-104:~$ ls -l

    total 4
    -rw-rw-r-- 1 ubuntu ubuntu    0 Feb  6 14:33 hello
    drwxrwxr-x 5 ubuntu ubuntu 4096 Feb  7 15:31 template

ubuntu@ip-172-31-39-104:~$ ls -l template/
    total 160
    -rw-rw-r-- 1 ubuntu ubuntu  2407 Feb  7 15:31 401.html
    -rw-rw-r-- 1 ubuntu ubuntu  2407 Feb  7 15:31 404.html
    -rw-rw-r-- 1 ubuntu ubuntu  2338 Feb  7 15:31 500.html
    drwxrwxr-x 4 ubuntu ubuntu  4096 Feb  7 15:31 assets
    -rw-rw-r-- 1 ubuntu ubuntu 11617 Feb  7 15:31 charts.html
    drwxrwxr-x 2 ubuntu ubuntu  4096 Feb  7 15:31 css
    -rw-rw-r-- 1 ubuntu ubuntu 41881 Feb  7 15:31 index.html
    drwxrwxr-x 2 ubuntu ubuntu  4096 Feb  7 15:31 js
    -rw-rw-r-- 1 ubuntu ubuntu  9559 Feb  7 15:31 layout-sidenav-light.html
    -rw-rw-r-- 1 ubuntu ubuntu  9791 Feb  7 15:31 layout-static.html
    -rw-rw-r-- 1 ubuntu ubuntu  4075 Feb  7 15:31 login.html
    -rw-rw-r-- 1 ubuntu ubuntu  3508 Feb  7 15:31 password.html
    -rw-rw-r-- 1 ubuntu ubuntu  5600 Feb  7 15:31 register.html
    -rw-rw-r-- 1 ubuntu ubuntu 38311 Feb  7 15:31 tables.html
```

Ahora toca moverlo a la capeta **/var/www/html** que en esta carpeta solo puede acceder sudo

* copia de manera recursiva y forzada todos los archivos de template y los pegas en /var/...
```sh
# traslado archivos
ubuntu@ip-172-31-39-104:~$ sudo cp -r template/* /var/www/html

# compruebo
ubuntu@ip-172-31-39-104:~$ ls -l /var/www/html

    total 164
    -rw-r--r-- 1 root root  2407 Feb  7 15:39 401.html
    -rw-r--r-- 1 root root  2407 Feb  7 15:39 404.html
    -rw-r--r-- 1 root root  2338 Feb  7 15:39 500.html
    drwxr-xr-x 4 root root  4096 Feb  7 15:39 assets
    -rw-r--r-- 1 root root 11617 Feb  7 15:39 charts.html
    drwxr-xr-x 2 root root  4096 Feb  7 15:39 css
    -rw-r--r-- 1 root root 41881 Feb  7 15:39 index.html
    -rw-r--r-- 1 root root   612 Feb  7 13:07 index.nginx-debian.html
    drwxr-xr-x 2 root root  4096 Feb  7 15:39 js
    -rw-r--r-- 1 root root  9559 Feb  7 15:39 layout-sidenav-light.html
    -rw-r--r-- 1 root root  9791 Feb  7 15:39 layout-static.html
    -rw-r--r-- 1 root root  4075 Feb  7 15:39 login.html
    -rw-r--r-- 1 root root  3508 Feb  7 15:39 password.html
    -rw-r--r-- 1 root root  5600 Feb  7 15:39 register.html
    -rw-r--r-- 1 root root 38311 Feb  7 15:39 tables.html
```

**Hemos conseguido publicar una web estática vía aws**

Ahora vete al browser y recarga la página `https://54.224.151.83` la verás así `https://startbootstrap.com/template/sb-admin`

---

> [!NOTE] 
> Continuamos con la configuracion de nginx pâra entender como con una configuracion de nginx podemos dar servicio a todos los dominios que queramos , tantos como la capacidad de servidor admita en cuanto a las visitas.

**Vamos a desplegar una aplicacion de React**

Descargamos la librería Redux

https://github.com/mjbuckley/react-redux-todo-app

React sirve para hacer una SPA single page aplication. No hay gran diferencia entre una página hecha en React a una página estática como la que desplegamos el otro día. Lo que pasa es que cuendo usamoe el [Router en React](https://github.com/mjbuckley/react-redux-todo-app) , ahí ya si que tenemos que hacer algo especial.

Vamos a desplegar la típica aplicacion de to do

---
![](/img/13.png)

---

**Descargamos el código y compilamos la aplicacion de React**

* Clono en local este repositorio https://github.com/mjbuckley/react-redux-todo-app.git

```sh
# clonando proyecto app to do
➜  Servidores_Despliegue_Aplicaciones git clone https://github.com/mjbuckley/react-redux-todo-app.git
    Cloning into 'react-redux-todo-app'...
    remote: Enumerating objects: 320, done.
    remote: Counting objects: 100% (30/30), done.
    remote: Compressing objects: 100% (20/20), done.
    remote: Total 320 (delta 23), reused 10 (delta 10), pack-reused 290
    Receiving objects: 100% (320/320), 1.27 MiB | 3.60 MiB/s, done.
    Resolving deltas: 100% (180/180), done.

➜  Servidores_Despliegue_Aplicaciones ls -l
    total 128
    drwxr-xr-x   7 alex  staff    224 Feb  9 09:40 CLASES
    drwxr-xr-x   3 alex  staff     96 Feb  6 15:21 Despliegue_AWS
    drwxr-xr-x@ 13 alex  staff    416 Feb  9 10:05 FullStack15_Servidores_Despliegue_Aplicaciones
    drwxr-xr-x  11 alex  staff    352 Feb  9 10:24 react-redux-todo-app
    -rw-r--r--@  1 alex  staff  62219 Feb  7 16:02 startbootstrap-sb-admin-gh-pages.zip
    drwxrwxr-x@ 16 alex  staff    512 Mar 25  2023 template

# entramos en la carpeta
➜  Servidores_Despliegue_Aplicaciones cd react-redux-todo-app 

# instalamos dependencias
➜  react-redux-todo-app git:(master) ✗ npm install   

# buscamos el script para compilar ""build": "react-scripts build","
➜  react-redux-todo-app git:(master) ✗ cat package.json
{
  "name": "react-redux-todo-app",
  "version": "0.1.0",
  "private": true,
  "homepage": "https://mjbuckley.github.io/react-redux-todo-app",
  "dependencies": {
    "gh-pages": "^1.2.0",
    "lodash": "^4.17.11",
    "react": "^16.8.6",
    "react-dom": "16.3.3",
    "react-redux": "^5.1.1",
    "react-router-dom": "^4.3.1",
    "react-scripts": "1.1.5",
    "redux": "^3.7.2",
    "uuid": "^3.3.2"
  },
  "scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build",
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject"
  },
  "devDependencies": {
    "redux-devtools": "^3.5.0"
  }
}

# ejecuta el script build definido en el archivo package.json   
# compila y empaqueta el código fuente en archivos optimizados para producción
# seguro que te deja la aplicacin en una carpeta /dis o /build
➜  react-redux-todo-app git:(master) ✗ npm run build      

    > react-redux-todo-app@0.1.0 build
    > react-scripts build

    Creating an optimized production build...
    Compiled successfully.

    File sizes after gzip:

    56.71 KB  build/static/js/main.1795c7d6.js
    621 B     build/static/css/main.1af68ee8.css

    The project was built assuming it is hosted at /react-redux-todo-app/.
    You can control this with the homepage field in your package.json.

    The build folder is ready to be deployed.
    To publish it at https://mjbuckley.github.io/react-redux-todo-app, run:

    npm run deploy

    Find out more about deployment here:

    http://bit.ly/2vY88Kr

➜  react-redux-todo-app git:(master) ✗ 
```

--- 

Lo que acabamos de hacer para construir la aplicacion de react es lo mismo que haríamos si lo hiciéramos con VSC. Es decir, abrimos la carpeta clonada desde VSC y veremos el archivo `packaje.json` que dentro tenemos el `script` para construir la aplicacion react y lo ejecutamos `npm run build `

```json
  "scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build",
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject"
  },
```

Te ha construido una carpeta `build`

---
![](/img/14.png)

---

> [!IMPORTANT]
> Truco impresionante, hace poco que funciona, crearás un contendor Docker rápido

---

Creo archivo `.devcontainer.json` 

`.devcontainer.json`

```js
{
    "image": "node:latest"
}
```

Hacer esto te permite que el entorno de desarrollo sea consistente y reproducible, independientemente del sistema operativo o de la configuración de la máquina host. Es decir, estas desarrollando dentro de un contenedor de Docker. Si tu aplicación luego se va a ejecutar dentro de un contenedor de Docker, tu podrías utilizar una imagen de Docker sobre la que se va a subir al servidor; es decir, desarrollar en el mismo entorno en la que se va a desarrollar la aplicación.

Estamos en el caso más simple y es son muy amplias las posibilidades, pero también podríamos decirle que cree el `.devcontainer` en base a un archivo de `Docker compoust` y eso te cree todo el entorno de desarrollo.

El archivo `.devcontainer.json` es una parte clave de la configuración de los Contenedores de Desarrollo en Visual Studio Code. Se utiliza para definir y configurar un entorno de desarrollo contenerizado que puede incluir herramientas, extensiones de VS Code, y configuraciones personalizadas necesarias para un proyecto específico. 

Por ejemplo, en el curso de backend avanzado, teníamos que tener instalado `node, mongoDB, react, etc` por así decirlo yo te podría dar dos archivos `.devcontainer.json, docker-compose.yml` de manera que automáticamente con esto nos configurara todo el entorno sin hacer nada. Te acorta todo el tiempo de hacerte el setup del entorno. Te permite desarrollar exactamente en el mismo entorno que se desarrolla la app.

Nosotros ahora mismo solo te estamos diciendo que quiero que mi entorno de desarrollo se base en node y que sea la última `"image": "node:latest"`.

Entonces, instalada la extensión `Dev Containers` de VSC y también tener instalado `Docker` en local  abierto, le das al boton verde


![](/img/16.png)


Cuando le indicas reopen container te reinicia el VSC y te monta el contenedor. Cuando termine realmente estarás dentro de un contenedor de docker, puedes comprovarlo si abres la terminal y ves la direccion del contenedor

```sh
root@8d39e94b8d3d:/workspaces/react-redux-todo-app# 
```

Ahora puedes cargar las dependencias y compilamos la aplicacion de React

```sh
root@8d39e94b8d3d:/workspaces/react-redux-todo-app# npm i  

        added 1344 packages, and audited 1345 packages in 1m

        161 vulnerabilities (13 low, 73 moderate, 57 high, 18 critical)

        To address issues that do not require attention, run:
        npm audit fix

        To address all issues (including breaking changes), run:
        npm audit fix --force

        Run `npm audit` for details.
        npm notice 
        npm notice New minor version of npm available! 10.2.4 -> 10.4.0
        npm notice Changelog: https://github.com/npm/cli/releases/tag/v10.4.0
        npm notice Run npm install -g npm@10.4.0 to update!
        npm notice 

root@8d39e94b8d3d:/workspaces/react-redux-todo-app# npm run build

        > react-redux-todo-app@0.1.0 build
        > react-scripts build

        Creating an optimized production build...
        (node:1290) [DEP0040] DeprecationWarning: The `punycode` module is deprecated. Please use a userland alternative instead.
        (Use `node --trace-deprecation ...` to show where the warning was created)
        Compiled successfully.

        File sizes after gzip:

        56.77 KB  build/static/js/main.1795c7d6.js
        621 B     build/static/css/main.1af68ee8.css

        The project was built assuming it is hosted at /react-redux-todo-app/.
        You can control this with the homepage field in your package.json.

        The build folder is ready to be deployed.
        To publish it at https://mjbuckley.github.io/react-redux-todo-app, run:

        npm run deploy

        Find out more about deployment here:

        http://bit.ly/2vY88Kr

root@8d39e94b8d3d:/workspaces/react-redux-todo-app# 
```

Puedes ver que te ha creado igual la carpeta `build` que es donde se forma la app, además si te vas a local, aunque estés dentro del contenedor, verás que se crea la carpeta porque está mapeando en el local.

---

El término "build" se refiere al proceso de transformar el código fuente de tu aplicación en un conjunto de archivos ejecutables o distribuibles que pueden ser desplegados en un servidor o entregados a los usuarios. En el contexto de aplicaciones web como una hecha con React.

El resultado de este proceso es una carpeta (comúnmente denominada build, dist, o similar), que contiene todos los archivos optimizados y listos para ser desplegados en un servidor web. Esta carpeta incluye:

* Archivos JavaScript empaquetados y minificados.
* Archivos CSS optimizados.
* Archivos de imágenes y otros activos estáticos.
* Archivos HTML, en el caso de aplicaciones que generan vistas estáticas o utilizan SSR.

El propósito de este proceso es asegurar que la aplicación sea lo más eficiente posible en términos de velocidad de carga y rendimiento en el navegador del usuario final. También ayuda a asegurar la compatibilidad con diferentes navegadores y dispositivos al transpilar y polifillar características modernas de JavaScript y CSS a versiones que sean soportadas universalmente.

---

Ahora el siguiente paso sería llevarme la app al servidor ¿podríamos hacerlo de otra manera que nos ahorrara trabajo?
* Si lo hacer directamente el build en el servidor has de instalar node, **No es buena idea instalar cosas**, cuanto menos cosas hayas de mantener mejor. Todo esto consume un pico de momeria y cpu que nos puede dar problmeas.
* Nunca se hace un `build` de ningún tipo en un servidor de producción.


**Voy a conectar con aws** & **Quiero subir la carpeta `build` y sus archivos al servidor**

```sh
➜  Servidores_Despliegue_Aplicaciones ls -l
        total 128
        drwxr-xr-x   7 alex  staff    224 Feb  9 09:40 CLASES
        drwxr-xr-x   3 alex  staff     96 Feb  6 15:21 Despliegue_AWS
        drwxr-xr-x@ 13 alex  staff    416 Feb  9 10:25 FullStack15_Servidores_Despliegue_Aplicaciones
        drwxr-xr-x@ 14 alex  staff    448 Feb  9 12:25 react-redux-todo-app
        -rw-r--r--@  1 alex  staff  62219 Feb  7 16:02 startbootstrap-sb-admin-gh-pages.zip
        drwxrwxr-x@ 16 alex  staff    512 Mar 25  2023 template

➜  Servidores_Despliegue_Aplicaciones cd react-redux-todo-app 

# acuerdate que tienes este comando para buscar "Ctrl + r"
bck-i-search: scp_
➜  react-redux-todo-app git:(master) ✗ scp -r -i ../Despliegue_AWS/web15.pem ../template ubuntu@54.224.151.83:/home/ubuntu

# OJO : --> has de subir otra carpeta que se llama  
➜  react-redux-todo-app git:(master) ✗ scp -r -i ../Despliegue_AWS/web15.pem ../react-redux-todo-app/build ubuntu@54.224.151.83:/home/ubuntu
        favicon.ico            100% 3870    35.5KB/s   00:00    
        index.html             100%  903     8.3KB/s   00:00    
        404.html               100% 1851    17.1KB/s   00:00    
        asset-manifest.json    1.8KB/s   00:00    
        main.1af68ee8.css.map  2KB/s   00:00    
        main.1af68ee8.css      13.5KB/s   00:00    
        main.1795c7d6.js       450.4KB/s   00:00    
        main.1795c7d6.js.map   9MB/s   00:00    
        service-worker.js      30.0KB/s   00:00
```

**Me conecto al servidor**

```sh
# acuerdate que tienes este comando para buscar "Ctrl + r"
bck-i-search: ssh
➜  react-redux-todo-app git:(master) ✗ ssh -i ../Despliegue_AWS/web15.pem ubuntu@54.224.151.83 

ubuntu@ip-172-31-39-104:~$ 
ubuntu@ip-172-31-39-104:~$ ls -l
        total 8
        drwxr-xr-x 3 ubuntu ubuntu 4096 Feb  9 12:45 build
        -rw-rw-r-- 1 ubuntu ubuntu    0 Feb  6 14:33 hello
        drwxrwxr-x 5 ubuntu ubuntu 4096 Feb  7 15:31 template

# elimino carpetas  archivos que no quiero
ubuntu@ip-172-31-39-104:~$ 
ubuntu@ip-172-31-39-104:~$ rm -rf hello template/
ubuntu@ip-172-31-39-104:~$ ls -l
        total 4
        drwxr-xr-x 3 ubuntu ubuntu 4096 Feb  9 12:45 build

# renombro el nombre de la carpeta build
ubuntu@ip-172-31-39-104:~$ mv build react-todo
ubuntu@ip-172-31-39-104:~$ ls -l
total 4
drwxr-xr-x 3 ubuntu ubuntu 4096 Feb  9 12:45 react-todo
```

**Quiero :** 

**- Que la IP del servidor cargue una página.** 172.31.39.104  
**- Que las DNS del servidor cargue otra página.** ec2-54-224-151-83.compute-1.amazonaws.com

si haces un ping a la DNS

```sh
ubuntu@ip-172-31-39-104:~$ ping ec2-54-224-151-83.compute-1.amazonaws.com

    PING ec2-54-224-151-83.compute-1.amazonaws.com (172.31.39.104) 56(84) bytes of data.
    64 bytes from ip-172-31-39-104.ec2.internal (172.31.39.104): icmp_seq=1 ttl=64 time=0.012 ms
```

si te vas al Browser y cargas IP o DNS te cargará la misma página de la template

puedes ver que de hecho es la misma IP a la que hace el ping.  
Yo lo que quiero es que 
* cuiando entres por IP carges la plantilla que ya teníamos
* cuando entres por DNS carge la aplicacion de React

---
![](/img/17.png)

---

Lo hacemos porque si, peor fíjate que de esta forma, si tienes un dominio en propiedad, tu puedes generarte tantos subdominios como quieras y en cada subdominio mostrar una cosa diferente.

**Una vez subido el codigo de la app al servidor, ¿qué hacemos?** 

Algo tendremos que tocas en la configuracion de `nginx`

```sh
ubuntu@ip-172-31-39-104:~$ cd /etc/nginx/
ubuntu@ip-172-31-39-104:/etc/nginx$ ls -l
        total 64
        drwxr-xr-x 2 root root 4096 May 30  2023 conf.d
        -rw-r--r-- 1 root root 1125 May 30  2023 fastcgi.conf
        -rw-r--r-- 1 root root 1055 May 30  2023 fastcgi_params
        -rw-r--r-- 1 root root 2837 May 30  2023 koi-utf
        -rw-r--r-- 1 root root 2223 May 30  2023 koi-win
        -rw-r--r-- 1 root root 3957 May 30  2023 mime.types
        drwxr-xr-x 2 root root 4096 May 30  2023 modules-available
        drwxr-xr-x 2 root root 4096 Feb  7 13:07 modules-enabled
        -rw-r--r-- 1 root root 1447 May 30  2023 nginx.conf
        -rw-r--r-- 1 root root  180 May 30  2023 proxy_params
        -rw-r--r-- 1 root root  636 May 30  2023 scgi_params
        drwxr-xr-x 2 root root 4096 Feb  7 13:07 sites-available
        drwxr-xr-x 2 root root 4096 Feb  7 13:07 sites-enabled
        drwxr-xr-x 2 root root 4096 Feb  7 13:07 snippets
        -rw-r--r-- 1 root root  664 May 30  2023 uwsgi_params
        -rw-r--r-- 1 root root 3071 May 30  2023 win-utf
ubuntu@ip-172-31-39-104:/etc/nginx$ 
```

En estas dos carpetas hay casi lo mismo

```sh
drwxr-xr-x 2 root root 4096 Feb  7 13:07 sites-available
drwxr-xr-x 2 root root 4096 Feb  7 13:07 sites-enabled
```

En `sites-available` vamos a encontrar ficheros de configuración de páginas webs, que pueden ser servidas o no con mi `nginx` y en esa carpeta es donde me voy a crear mi fichero de configuración de las páginas que voy a servir.

En `sites-enabled` vamos a encontrar ficheros de configuración de las páginas web que `nginx` está sirviendo.

Por una parte en sites-available tenemos el archivo default

```sh
ubuntu@ip-172-31-39-104:/etc/nginx$ ls -l sites-available/
        total 4
        -rw-r--r-- 1 root root 2412 May 30  2023 default
```

Por otra parte en sites-enabled tenemos 

```sh
ubuntu@ip-172-31-39-104:/etc/nginx$ ls -l sites-enabled/
    total 0
    lrwxrwxrwx 1 root root 34 Feb  7 13:07 default -> /etc/nginx/sites-available/default
```

fíjate que comienza con una `l` --> `lrwxrwxrwx` yesto nos dice que verdaderamente no es un archivo, es un acceso directo.

> [!NOTE]
> El archivo de configuración de mi sitio web, siempre lo voy a crear en `/etc/nginx/sites-available/default`
> 
> De esta manera puedo tener 15 páginas web configuradas, e imagina que estas 15 son de 15 clientes, imaginate que uno no me paga, pues lo que no haré será eliminar todo el proyecto del servidor porque si el mes que viene me paga yo puedo activar de nuevo desde este archivo y dar servicio de nuevo al impagado. Esto lo harías borrando el acceso directo y cuando te vuelva a pagar escribes el acceso directo.

```sh
ubuntu@ip-172-31-39-104:/etc/nginx$ cd sites-available/
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo nano react-todo

# #######  NANO EJEJMPLO ########
server {
        listen 80;
        server_name <PON AQUI TU DNS DE AWS>; # 
        root <TU RUTA A LA APP DE REACT>;
        index index.html;
        location / {
                try_files $uri $uri/ =404;
        }
}

# ##########  NANO  #############
server {
        # quiero que esta web esté disponible a través del puerto 80, pon el que quieras
        listen 80; 
        # cuando la petición sea de este dominio, este servidor tiene que responder, no la IP, si no este DNS
        server_name ec2-54-224-151-83.compute-1.amazonaws.com;
        # la carpeta donde están los archivos 
        root /home/ubuntu/react-todo;
        # cuadno no te pidan una ruta o un archivo intenta buscar este archivo "/home/ubuntu/react-todo/index.html"
        index index.html;
        # importa el orden; permite aplicar configuraciones diferentes en función de la ruta que pida el usuario
        # si pones location /hola sólo aplicaría si la url que pide el usuario empieza por /hola
        location / {                            # nosotros ahora ponemos / así es cualquier url,la raiz
                try_files $uri $uri/ =404;      # quiera que haga nginx que sirva los archivos que estñan en esta ruta
        }
}

```
---
> [!IMPORTANT]
>* `try_files` : nginx intentará servir los archivos que están en root `/home/ubuntu/react-todo`
>* `$uri` : usando como ruta la uri que te está pidiendo el usuario 
>* `$uri/` : si la ruta no existe como un archivo, intenta buscarla como carpeta
>* `=404`: pues le dices que no existe;
--- 


**Sguiente paso**


Esto anterior lo hemos creado en `sites-available`  pero todavía `nginx` no lo estaría usando para qdecorle que tiene que usarlo lo hemos de poner en la carpeta `sites-enabled`.

Las buenas prácticas dicen que has de crear un acceso directo. Como 

`drwxr-xr-x 2 root root 4096 Feb  7 13:07 sites-enabled`

pertenece a root tendremos que usar sudo  

¿qué es ls -s? https://medium.com/@307/hard-links-and-symbolic-links-a-comparison-7f2b56864cdd

```sh
# ls -s
# /etc/nginx/sites-available/react-todo : ruta del fichero original
# /etc/nginx/sites-enabled/react : destino donde quiero el acceso directo (react es un nombre inventado)
sudo ln -s /etc/nginx/sites-available/react-todo /etc/nginx/sites-enabled/react

# si haces un cat puedes ver el fichero creado 
ubuntu@ip-172-31-39-104:/etc/nginx$ cat /etc/nginx/sites-enabled/react
        server {
                listen 80;
                server_name ec2-54-224-151-83.compute-1.amazonaws.com;;
                root /home/ubuntu/react-todo;
                index index.html;
                location / {
                        try_files $uri $uri/ =404;
                }
        }
```

importante, has de recargar el servidor

```sh
# recargo nginx
ubuntu@ip-172-31-39-104:/etc/nginx$ sudo systemctl reload nginx

# compruebo que haya cargado bien
ubuntu@ip-172-31-39-104:/etc/nginx$ sudo systemctl status nginx.service

    ● nginx.service - A high performance web server and a reverse proxy server
        Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
        Active: active (running) since Wed 2024-02-07 13:21:46 UTC; 2 days ago
        Docs: man:nginx(8)
        Process: 357 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
        Process: 414 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
        Process: 4366 ExecReload=/usr/sbin/nginx -g daemon on; master_process on; -s reload (code=exited, status=0/SUCCESS)
    Main PID: 424 (nginx)
        Tasks: 2 (limit: 1121)
        Memory: 12.1M
            CPU: 199ms
        CGroup: /system.slice/nginx.service
                ├─ 424 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
                └─4367 "nginx: worker process" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" ""

    Feb 07 13:21:45 ip-172-31-39-104 systemd[1]: Starting A high performance web server and a reverse proxy server...
    Feb 07 13:21:46 ip-172-31-39-104 systemd[1]: Started A high performance web server and a reverse proxy server.
    Feb 09 13:54:48 ip-172-31-39-104 systemd[1]: Reloading A high performance web server and a reverse proxy server...
    Feb 09 13:54:48 ip-172-31-39-104 systemd[1]: Reloaded A high performance web server and a reverse proxy server.
```

Ahora si pones las dns y luego la ip en el browser debería funcionar,  
si no funciona puedes mirar en los archivos logs

```sh
ubuntu@ip-172-31-39-104:/etc/nginx$ cd /var/log
ubuntu@ip-172-31-39-104:/var/log$ ls -l
        total 1692
        -rw-r--r--  1 root      root              7820 Feb  7 06:35 alternatives.log
        drwx------  3 root      root              4096 Feb  6 12:31 amazon
        drwxr-xr-x  2 root      root              4096 Feb  7 13:07 apt
        -rw-r-----  1 syslog    adm             219265 Feb  9 13:55 auth.log
        -rw-rw----  1 root      utmp            218496 Feb  9 13:12 btmp
        drwxr-x---  2 _chrony   _chrony           4096 Feb  6 12:31 chrony
        -rw-r-----  1 root      adm               7619 Feb  7 13:21 cloud-init-output.log
        -rw-r-----  1 syslog    adm             258592 Feb  7 13:21 cloud-init.log
        drwxr-xr-x  2 root      root              4096 Aug  2  2023 dist-upgrade
        -rw-r-----  1 root      adm              41516 Feb  7 13:21 dmesg
        -rw-r-----  1 root      adm              41434 Feb  6 12:31 dmesg.0
        -rw-r--r--  1 root      root             68743 Feb  7 13:07 dpkg.log
        drwxr-sr-x+ 3 root      systemd-journal   4096 Feb  6 12:31 journal
        -rw-r-----  1 syslog    adm             114114 Feb  7 13:21 kern.log
        drwxr-xr-x  2 landscape landscape         4096 Feb  6 14:30 landscape
        -rw-rw-r--  1 root      utmp            292292 Feb  9 12:49 lastlog
        drwxr-xr-x  2 root      adm               4096 Feb  9 00:00 nginx
        drwx------  2 root      root              4096 Feb  6 12:31 private
        -rw-r-----  1 syslog    adm             645547 Feb  9 13:55 syslog
        -rw-r--r--  1 root      root             18375 Feb  9 01:41 ubuntu-advantage.log
        drwxr-x---  2 root      adm               4096 Feb  6 22:38 unattended-upgrades
        -rw-rw-r--  1 root      utmp              9984 Feb  9 12:49 wtmp
ubuntu@ip-172-31-39-104:/var/log$ cd nginx/
ubuntu@ip-172-31-39-104:/var/log/nginx$ ls -l
        total 104
        -rw-r----- 1 www-data adm 21807 Feb  9 13:58 access.log
        -rw-r----- 1 www-data adm 65394 Feb  8 23:44 access.log.1
        -rw-r----- 1 www-data adm   705 Feb  9 13:58 error.log
        -rw-r----- 1 www-data adm    78 Feb  7 13:07 error.log.1
ubuntu@ip-172-31-39-104:/var/log/nginx$ tail error.log
    2024/02/09 13:51:38 [emerg] 4346#4346: unexpected ";" in /etc/nginx/sites-enabled/react:3
    2024/02/09 13:54:48 [notice] 4366#4366: signal process started
    2024/02/09 13:58:03 [crit] 4367#4367: *440 stat() "/home/ubuntu/react-todo/cart.json" failed (13: Permission denied), client: 85.87.66.72, server: ec2-54-224-151-83.compute-1.amazonaws.com, request: "GET /cart.json HTTP/1.1", host: "ec2-54-224-151-83.compute-1.amazonaws.com"
    2024/02/09 13:58:03 [crit] 4367#4367: *440 stat() "/home/ubuntu/react-todo/cart.json" failed (13: Permission denied), client: 85.87.66.72, server: ec2-54-224-151-83.compute-1.amazonaws.com, request: "GET /cart.json HTTP/1.1", host: "ec2-54-224-151-83.compute-1.amazonaws.com"
    ubuntu@ip-172-31-39-104:/var/log/nginx$ 

```

**(13: Permission denied)**

¿pero como saber que eres tu y no es un bot? Imaginate que es el servidor del log de google que hay millones por segundo?

te vas a "cuál es mi ip" cuando la tienes 85.87.66.72

```sh
ubuntu@ip-172-31-39-104:/var/log/nginx$ tail -f error.log | grep 85.87.66.72
2024/02/09 13:58:03 [crit] 4367#4367: *440 stat() "/home/ubuntu/react-todo/cart.json" failed (13: Permission denied), client: 85.87.66.72, server: ec2-54-224-151-83.compute-1.amazonaws.com, request: "GET /cart.json HTTP/1.1", host: "ec2-54-224-151-83.compute-1.amazonaws.com"
2024/02/09 13:58:03 [crit] 4367#4367: *440 stat() "/home/ubuntu/react-todo/cart.json" failed (13: Permission denied), client: 85.87.66.72, server: ec2-54-224-151-83.compute-1.amazonaws.com, request: "GET /cart.json HTTP/1.1", host: "ec2-54-224-151-83.compute-1.amazonaws.com"
2024/02/09 14:07:47 [crit] 4367#4367: *444 stat() "/home/ubuntu/react-todo/cart.json" failed (13: Permission denied), client: 85.87.66.72, server: ec2-54-224-151-83.compute-1.amazonaws.com, request: "GET /cart.json HTTP/1.1", host: "ec2-54-224-151-83.compute-1.amazonaws.com"
```

fíjate que ahora ha filtrado solo las de mi ip, que son las mismas que antes porque no tenemos entradas desde el exterior a la app, pero google tiene millones por segundo, sólo así sabes tus fallos. Cada vez que intentes entrar a `http://ec2-54-224-151-83.compute-1.amazonaws.com/` te da error porque no tienes permisos .


```sh
ubuntu@ip-172-31-39-104:/var/log/nginx$ cd
ubuntu@ip-172-31-39-104:~$ ls -l
total 4
drwxr-xr-x 3 ubuntu ubuntu 4096 Feb  9 12:45 react-todo # tiene permisos para todo el mundo de lectura y ejecucion
```

Si te vas a la carpeta superior

```sh
ubuntu@ip-172-31-39-104:/home$ ls -l
total 4
drwxr-x--- 5 ubuntu ubuntu 4096 Feb  9 12:51 ubuntu # sólo tiene permisos para ubuntu
```

**Cómo podemos saber qué usuario está usando ubunto**

```sh
ubuntu@ip-172-31-39-104:/home$ ps aux | grep nginx
root     424  0.0  0.5  55368  5764 ?        Ss   Feb07   0:00 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
www-data 4367  0.0  0.6  56000  6264 ?        S    13:54   0:00 nginx: worker process
ubuntu   4395  0.0  0.2   7008  2304 pts/0    S+   14:12   0:00 grep --color=auto nginx
```
el que está intentando acceder es `nginx: worker process` porque siempre es el que trabaja, el master solo escucha el puerto. ¿qué usuario ejecuta el proceso ? -> `www-data`

Como el usuario `www-data` no es ubuntu, te deniega el permiso.

Podríamos mover el `www-data` y meterlo dentro de ubuntu (pero no tiene porque ser así, podríamos solucionalo como queramos). Si movemos la carpeta a `www-data` tendríamos que modificar el fichero de configuración porque le hemos dicho que la ruta estaba en `root /home/ubuntu/react-todo;` 

**Movemos la carpeta a `www-data`**


```sh
ubuntu@ip-172-31-39-104:~$ sudo mv /home/ubuntu/react-todo /var/www/
ubuntu@ip-172-31-39-104:~$ ls -l /var/www
        total 8
        drwxr-xr-x 5 root   root   4096 Feb  7 15:39 html
        drwxr-xr-x 3 ubuntu ubuntu 4096 Feb  9 12:45 react-todo
```

Hemos movido la carpeta y ahora pertenece a ubuntu y con estos permisos funcionaría `drwxr-xr-x 3 ubuntu ubuntu 4096 Feb  9 12:45 react-todo`.

**Modificar el fichero de configuración de nginx**

```sh   
ubuntu@ip-172-31-39-104:~$ sudo nano /etc/nginx/sites-available/react-todo

##### NANO #######
server {
        listen 80;
        server_name ec2-54-224-151-83.compute-1.amazonaws.com;
        root /var/www/react-todo;
        index index.html;
        location / {
                try_files $uri $uri/ =404;
        }
}
```

```sh
# comando para ver si hemos hecho bien las cosas
ubuntu@ip-172-31-39-104:~$ sudo nginx -t
    nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
    nginx: configuration file /etc/nginx/nginx.conf test is successful # nos dice que está bien


# recargar el servicio
ubuntu@ip-172-31-39-104:~$ sudo systemctl reload nginx # recargamos el servicio
```

Ahora voy al browser y recargo la app con las dns : **Public IPv4 DNS ec2-54-224-151-83.compute-1.amazonaws.com**

---
![](/img/18.png)

---

Me está dando problemas al recargar los archivos de .css y .js ¿este problmea es de nginx o de la aplicación?

Pues si `nginx` el archivo `index` lo carga, index es el primero que se ha cargado, esto quiere decir que gninx es capaz de cargar el archivo que tiene que encontrar; pero por algún motivo la aplicación le está diciendo que no cargue los archivos desde la raiz 

Si tu copias la url del archivo de JS que falla 

---
![](/img/19.png)

---

No te carga

---
![](/img/20.png)

---
 pero si le quitas de la direccion en `/react-redux-todo-app/` si que te carga

---
![](/img/21.png)

---


Entonces por algún motivo la aplicación cuando carga los archivos te está metido este `/react-redux-todo-app/`. El problmea está que cuando te vas al codigo de la app en VSC al `package.josin` existe un atributo que se llama `homepage`

```json
{
  "name": "react-redux-todo-app",
  "version": "0.1.0",
  "private": true,
  "homepage": "https://mjbuckley.github.io/react-redux-todo-app",
  "dependencies": {

```

y este atributo, con las app´s que se ha creado generalmente con react app o un proyecto de react , todo lo que intenta cargr te pone la ruta que le pongas aquí delante https://mjbuckley.github.io/`react-redux-todo-app`

Es  un error de cuando se ha hecho el kit de la aplicacion. Entonces...
* Borramos esta linea del paqkete
* hemos de volver hacer el/bin de la app
* volver a subirlo al servidor
* volver a mover la carpeta

**1º borrar la carpeta `bin/` que existe ahora mismo** (creará otro diferente)

**2º eliminar la linea que nos da problemas**

```sh
{
  "name": "react-redux-todo-app",
  "version": "0.1.0",
  "private": true,
  # "homepage": "https://mjbuckley.github.io/react-redux-todo-app",
  "dependencies": {

```

**3º construir la aplicció**

```sh
root@8d39e94b8d3d:/workspaces/react-redux-todo-app# rm -rf build/
root@8d39e94b8d3d:/workspaces/react-redux-todo-app# npm run build

        > react-redux-todo-app@0.1.0 build
        > react-scripts build

        Creating an optimized production build...
        (node:12529) [DEP0040] DeprecationWarning: The `punycode` module is deprecated. Please use a userland alternative instead.
        (Use `node --trace-deprecation ...` to show where the warning was created)
        Compiled successfully.

        File sizes after gzip:

        56.76 KB  build/static/js/main.0c247a1d.js
        621 B     build/static/css/main.1af68ee8.css

        The project was built assuming it is hosted at the server root.
        You can control this with the homepage field in your package.json.
        For example, add this to build it for GitHub Pages:

        "homepage" : "http://myname.github.io/myapp",

        The build folder is ready to be deployed.
        You may serve it with a static server:

        npm install -g serve
        serve -s build

        Find out more about deployment here:

        http://bit.ly/2vY88Kr
```


**4º crear e servidor**

```sh
➜  react-redux-todo-app git:(master) ✗ scp -r -i ../Despliegue_AWS/web15.pem ../react-redux-todo-app/build ubuntu@54.224.151.83:/home/ubuntu             
        favicon.ico            100% 3870    35.5KB/s   00:00    
        index.html             100%  903     8.3KB/s   00:00    
        404.html               100% 1851    17.1KB/s   00:00    
        asset-manifest.json    1.8KB/s   00:00    
        main.1af68ee8.css.map  2KB/s   00:00    
        main.1af68ee8.css      13.5KB/s   00:00    
        main.1795c7d6.js       450.4KB/s   00:00    
        main.1795c7d6.js.map   9MB/s   00:00    
        service-worker.js      30.0KB/s   00:00
```

Puedes ver en el servidor que la carpeta está creada

```sh
ubuntu@ip-172-31-39-104:~$ cd
ubuntu@ip-172-31-39-104:~$ ls -l
        total 4
        drwxr-xr-x 3 ubuntu ubuntu 4096 Feb 11 14:36 build
```

Ahora en el servidor todo lo que hay en la carpeta `build` hay que moverlo a la carpeta `react-todo`

```sh
ubuntu@ip-172-31-39-104:~$ sudo rm -rf /var/www/react-todo/ # elimino la carpeta react-todo
ubuntu@ip-172-31-39-104:~$ sudo mv build /var/www/react-todo # creo la carpeta react-todo con build
```

Ahora ya funciona la app

---

![](/img/22.png)

---

**FASE 1 COMPLETADA**

Fíjate que si tecleeas algún link, si te fijas, la dirección web cambia como sicambiasen las páginas pero sabemos que página solo hay una que no está navegando por el servidor todo ocurre por la single page.

* `http://ec2-54-224-151-83.compute-1.amazonaws.com/SHOW_COMPLETED`
* `http://ec2-54-224-151-83.compute-1.amazonaws.com/SHOW_ACTIVE`
* `...`

Si tu ahora copias las direcciones y las pegas para navegar verás que te da error, esto es porque le habíamos dicho a `nginxs` qie entrara por `/` y si no encontrara el archivo específico que cargara el 404

```sh
ubuntu@ip-172-31-39-104:~$ cat /etc/nginx/sites-enabled/react
        server {
                listen 80;
                server_name ec2-54-224-151-83.compute-1.amazonaws.com;
                root /var/www/react-todo;
                index index.html;
                location / {
                        try_files $uri $uri/ =404;
                }
        }
```

Fíjate que el la carpeta `/var/www/react-todo` que es donde yo le he dicho que busque los archivos ¿hay un archivo `index.html`?

```sh
ubuntu@ip-172-31-39-104:/var/www/react-todo$ ls -l
    total 24
    -rw-r--r-- 1 ubuntu ubuntu 1851 Feb 11 14:36 404.html
    -rw-r--r-- 1 ubuntu ubuntu  196 Feb 11 14:36 asset-manifest.json
    -rw-r--r-- 1 ubuntu ubuntu 3870 Feb 11 14:36 favicon.ico
    -rw-r--r-- 1 ubuntu ubuntu  840 Feb 11 14:36 index.html
    -rw-r--r-- 1 ubuntu ubuntu 3164 Feb 11 14:36 service-worker.js
    drwxr-xr-x 4 ubuntu ubuntu 4096 Feb 11 14:36 static
```

si tu le dices que cargue en el browser `http://ec2-54-224-151-83.compute-1.amazonaws.com/asset-manifest.json` te lo va a cargar. Esto es porque `nginx` dice : 
* de este dominio : `ec2-54-224-151-83.compute-1.amazonaws.com`
* tengo que ir a esta carpeta : `/var/www/react-todo`
* de esta carpeta está el archivo `asset-manifest.json` pues lo cargo.

Cuando le digo que cargue el archivo `http://ec2-54-224-151-83.compute-1.amazonaws.com/SHOW_COMPLETED` no lo encuentra ¿cómo lo solucionamos?

Esta instruccion `location / { try_files` decía :
* intenta servor los archivos que te dicen en la `$uri`"
* si no lo encuentras, intenta servir la carpeta `$uri/`
* y si no hay carpeta `404`

en tonces le vamos a decir que ni no encuentra ni esta `$uri` ni esta `$uri/` que devuelva el index y como el index arracan la app de react pues ya se ocupará react de hacerlo. ¿siempre vas a servir el index? no, eso sería si colocas el index el primero, pero estamos diciendo que si no encuentra `$uri` ni `$uri/`, en ese caso que sirva el index.

> [!NOTE] 
> Entonces estamos y queremos que React gestione cuando pase ese caso

**Modifquemos el archivo de configuración de configuración de nginx**

```sh
ubuntu@ip-172-31-39-104:/var/www/react-todo$ sudo nano /etc/nginx/sites-available/react-todo 
```

```sh
        server {
                listen 80;
                server_name ec2-54-224-151-83.compute-1.amazonaws.com;
                root /var/www/react-todo;
                index index.html;
                location / {
                        try_files $uri $uri/ /index.html;
                }
        }
```


```sh
ubuntu@ip-172-31-39-104:/var/www/react-todo$ sudo nginx -t # compruebo que todo esté bien
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

```sh
ubuntu@ip-172-31-39-104:/var/www/react-todo$ sudo systemctl reload nginx # recargo el sistema
```



# Desplegando dos aplicaciones con node


* CASO 1 sin base de datos, va a ser un chat
* CASO 2 con base de datos, necesitamos instalar mongoDB


## CASO 1 sin base de datos, va a ser un chat
---

> [!IMPORTANT]
> ### 1er paso del CASO 1, instalo la app y compruebo que funciona
>
> Comenzamos...
--- 

**NODE**

* Node funciona “tal cual” desarrollamos en producción
* Lo que debemos hacer es que arranque cuando el servidor se inicie (por si hubiera un reinicio del servidor inesperado)
* Para ello, podemos usar supervisor: un gestor de procesos para apps Node
* Reinicia las apps si se caen o son matadas : para hacer eso necesitaremos un `gestor de procesos`
* Es más sencillo que crear un script para rc.d o systemd

**1º Crear un usuario para la aplicación**

```sh
sudo adduser <app>
```

Crearemos app que hemos hecho nosotros o mi equipo, esto significa que nos podemos preparar un sudo install y que todo eso funcione pero es muy complejo, lo subiremos al servidor y que funciones.

Cualquier preoceso corre con un usuario. Actualemente tenemos un usuario `ubuntu` que puede adquirir provilegio de superadministrador, es bueno que no lo uses así por los hackers.

Cualquier app que está en internet tiene que correr con un usuario que no tenga privilegios de gran cosa. Lo ideal es un usuario por aplicacion.

**2º Bloquear la cuenta del usuario de la app**

Nunca pueda autenticarse nadie desde fuera

```sh
passwd -l <app>
```

**3º Convertirnos en de la aplicación**

nos vamos a comvertir en ese usuario

```sh
sudo -u <app> -i
```

--- 

> [!NOTE]
> Comenzamos ... 

**1º Crear un usuario para la aplicación**

```sh
ubuntu@ip-172-31-39-104:~$ sudo adduser pepe
    Adding user `pepe' ...
    Adding new group `pepe' (1001) ...
    Adding new user `pepe' (1001) with group `pepe' ...
    Creating home directory `/home/pepe' ...
    Copying files from `/etc/skel' ...
    New password: 
    Retype new password: 
    passwd: password updated successfully
    Changing the user information for pepe
    Enter the new value, or press ENTER for the default
        Full Name []: 
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
    Is the information correct? [Y/n] 

ubuntu@ip-172-31-39-104:~$ 
```


**2º Bloquear la cuenta del usuario de la app**

```sh
ubuntu@ip-172-31-39-104:~$ sudo passwd -l pepe
    passwd: password expiry information changed.
```

Voy a comprovar que no puedo entrar desde otra terminal

```sh
➜  ~ ssh pepe@54.224.151.83  
pepe@54.224.151.83: Permission denied (publickey).
➜  ~ ssh pepe@54.224.151.83 
pepe@54.224.151.83: Permission denied (publickey).
➜  ~ 
```


**3º Convertirnos en de la aplicación**

```sh
ubuntu@ip-172-31-39-104:~$ sudo -u pepe -i
pepe@ip-172-31-39-104:~$ whoami
pepe
pepe@ip-172-31-39-104:~$ 
```

Se ha convertido en `pepe` pero la sesion de ubunto sigue activa

```sh
pepe@ip-172-31-39-104:~$ logout
ubuntu@ip-172-31-39-104:~$ 
```

---

### Queremos instalar una aplicacion NODE

¿Qué necesito tener? NODE instalado. pero su haces `sudo apt install node` se instalará la que tenga node específica y estaría diciendo que si quiero despelgar varias app tengan que trabajar todas con la misma versión de node. Para eso tenemos **Node Version Manager** y es lo que vamos a instalar primero.

https://github.com/creationix/nvm 

**Nos comvertimos en pepe para despligar las aplicacoines**

```sh
sudo -u pepe -i
```

**Installing and Updating**

https://github.com/creationix/nvm 

`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash` descarga n script y lo ejecuta. No es buena idea que lo descargue en nuestro servidor directamente. Nos vamos a fiar porque es nvm.

```sh
pepe@ip-172-31-39-104:~$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
        % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                        Dload  Upload   Total   Spent    Left  Speed
        100 16555  100 16555    0     0   187k      0 --:--:-- --:--:-- --:--:--  190k
        => Downloading nvm from git to '/home/pepe/.nvm'
        => Cloning into '/home/pepe/.nvm'...
        remote: Enumerating objects: 365, done.
        remote: Counting objects: 100% (365/365), done.
        remote: Compressing objects: 100% (314/314), done.
        remote: Total 365 (delta 43), reused 156 (delta 25), pack-reused 0
        Receiving objects: 100% (365/365), 365.11 KiB | 13.04 MiB/s, done.
        Resolving deltas: 100% (43/43), done.
        * (HEAD detached at FETCH_HEAD)
        master
        => Compressing and cleaning up git repository

        => Appending nvm source string to /home/pepe/.bashrc
        => Appending bash_completion source string to /home/pepe/.bashrc
        => Close and reopen your terminal to start using nvm or run the following to use it now:

        export NVM_DIR="$HOME/.nvm"
        [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
        [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
pepe@ip-172-31-39-104:~$ 
```

Si lees bien te está diciendo que reinicies la terminal

```sh
pepe@ip-172-31-39-104:~$ logout # salimos
ubuntu@ip-172-31-39-104:~$ sudo -u pepe -i # entramos
pepe@ip-172-31-39-104:~$ nvm
        Node Version Manager (v0.39.7)

        Note: <version> refers to any version-like string nvm understands. This includes:
        - full or partial version numbers, starting with an optional "v" (0.10, v0.1.2, v1)
        - default (built-in) aliases: node, stable, unstable, iojs, system
        - custom aliases you define with `nvm alias foo`

        Any options that produce colorized output should respect the `--no-colors` option.
pepe@ip-172-31-39-104:~$
```

**Instalmos la version node que necesitamos para el chat**

https://github.com/igorantun/node-chat 

Es un chat hecho no node.

Tienes que hacer un fork en tu cuenta de github.

Acabo de hacerun frok a guthub de este proyecto, entonces vamos a simular que es nuestra app que la hemos hecho nosotros.
Descargamos el codigo para que en el servidor esté el codigo de alguna manera


```sh
pepe@ip-172-31-39-104:~$ git clone https://github.com/alexjust-data/node-chat.git
    Cloning into 'node-chat'...
    remote: Enumerating objects: 565, done.
    remote: Counting objects: 100% (155/155), done.
    remote: Compressing objects: 100% (16/16), done.
    remote: Total 565 (delta 144), reused 139 (delta 139), pack-reused 410
    Receiving objects: 100% (565/565), 757.35 KiB | 12.84 MiB/s, done.
    Resolving deltas: 100% (310/310), done.

pepe@ip-172-31-39-104:~$ ls -l
total 4
drwxrwxr-x 6 pepe pepe 4096 Feb 11 16:06 node-chat
```

Este chat sólo funciona con node16, como ya tenemos nvm instalado 

```sh
pepe@ip-172-31-39-104:~$ nvm install 16
Downloading and installing node v16.20.2...
Downloading https://nodejs.org/dist/v16.20.2/node-v16.20.2-linux-x64.tar.xz...
######################################################################################################################## 100.0%
Computing checksum with sha256sum
Checksums matched!
Now using node v16.20.2 (npm v8.19.4)
Creating default alias: default -> 16 (-> v16.20.2)

pepe@ip-172-31-39-104:~$ node --version
v16.20.2
```

Para si te pica hacer con Docker 

Si lo hicieras con docker, en docker siempre has de partir de una imagen de docker para cear mi contenedor. Lo más facil es partir de una imagen de un Linux (Ubuntu, Debian, etc). Yo para este caso del chat, tiraría de una imagen de docker que tenga node 16; la que me da oficialmente docker y listo. Yhe de tirar de python 3.7 pues lo mismo.


**Instalamos dependencias**

```sh
pepe@ip-172-31-39-104:~$ cd node-chat/
pepe@ip-172-31-39-104:~/node-chat$ npm i
        npm WARN deprecated ejs@2.3.4: Critical security bugs fixed in 2.5.5

        added 62 packages, and audited 63 packages in 4s

        1 package is looking for funding
        run `npm fund` for details

        14 vulnerabilities (1 moderate, 12 high, 1 critical)

        To address all issues (including breaking changes), run:
        npm audit fix --force

        Run `npm audit` for details.
        npm notice 
        npm notice New major version of npm available! 8.19.4 -> 10.4.0
        npm notice Changelog: https://github.com/npm/cli/releases/tag/v10.4.0
        npm notice Run npm install -g npm@10.4.0 to update!
        npm notice 
```

segú la documentación de la página clonada


```sh
pepe@ip-172-31-39-104:~/node-chat$ npm start

> node-chat@1.0.7 start
> node app.js

[--:--:--][CONSOLE] [16:14:20] [Start] Listening at port 3000
```

arracado en el puerta 3000. Desberías arracar en `http://54.224.151.83:3000/` y te da error porque en las reglas del cortafuegos del otro día dijimos y abrimmos el uerto `80` y ahora hemos de abrir el puerto 3000


![](/img/24.png)

Recargas y ya tienes el chat. De hecho si comparte la direccion `http://54.224.151.83:3000/` a otra persona podrá chater contigo


```sh
pepe@ip-172-31-39-104:~/node-chat$ npm start

> node-chat@1.0.7 start
> node app.js

[--:--:--][CONSOLE] [17:08:23] [Start] Listening at port 3000
(node:9312) [DEP0066] DeprecationWarning: OutgoingMessage.prototype._headers is deprecated
(Use `node --trace-deprecation ...` to show where the warning was created)

        [17:08:37] [Socket] d5de2eb8-b4fa-4dc6-ad31-09d5e681f059: connected (undefined)
        [17:08:48] [Message] [Message] Hola: Hola cimo estas?
        [17:08:55] [Message] [Message] Hola: Muy bien y tu?
```

Hasta ahora estamos comprovando que la aplicación funciona conectándonos directamente a la aplicación del servidor. No hay ningún intermediario entre el servidor y no. Este es el paso primero que he de hacer cuando despliego una app:

* La cargo al servidor y doy los pasos necesario para ver que todo funciona bien en el servidor.
* si todo va bien, primer paso conseguido
* a partir de ahora pondremos intermediarios entre el servidor y yo. Por ejemplo querremos que alguien esté pendiente de que no se apague nunca la app; y este es al caso del `gestor de procesos` con https://pm2.io/


---
> [!IMPORTANT]
> 
> ## 2do paso del CASO 1, meto un intermediario
---


**Usamos PM2 como gestor de procesos**

https://pm2.io/docs/plus/overview/

```sh
npm install pm2 -g # l -g es para que lo instale global
```

```sh
pepe@ip-172-31-39-104:~$ npm install pm2 -g
        npm WARN deprecated uuid@3.4.0: Please upgrade  to version 7 or higher.  Older versions may use Math.random() in certain circumstances, which is known to be problematic.  See https://v8.dev/blog/math-random for details.

        added 163 packages, and audited 164 packages in 8s

        13 packages are looking for funding
        run `npm fund` for details

        5 high severity vulnerabilities

        To address all issues (including breaking changes), run:
        npm audit fix --force

        Run `npm audit` for details.


pepe@ip-172-31-39-104:~$ pm2 -version

                        -------------

__/\\\\\\\\\\\\\____/\\\\____________/\\\\____/\\\\\\\\\_____
 _\/\\\/////////\\\_\/\\\\\\________/\\\\\\__/\\\///////\\\___
  _\/\\\_______\/\\\_\/\\\//\\\____/\\\//\\\_\///______\//\\\__
   _\/\\\\\\\\\\\\\/__\/\\\\///\\\/\\\/_\/\\\___________/\\\/___
    _\/\\\/////////____\/\\\__\///\\\/___\/\\\________/\\\//_____
     _\/\\\_____________\/\\\____\///_____\/\\\_____/\\\//________
      _\/\\\_____________\/\\\_____________\/\\\___/\\\/___________
       _\/\\\_____________\/\\\_____________\/\\\__/\\\\\\\\\\\\\\\_
        _\///______________\///______________\///__\///////////////__


                          Runtime Edition

        PM2 is a Production Process Manager for Node.js applications
                     with a built-in Load Balancer.

                Start and Daemonize any application:
                $ pm2 start app.js

                Load Balance 4 instances of api.js:
                $ pm2 start api.js -i 4

                Monitor in production:
                $ pm2 monitor

                Make pm2 auto-boot at server restart:
                $ pm2 startup

                To go further checkout:
                http://pm2.io/


                        -------------

[PM2] Spawning PM2 daemon with pm2_home=/home/pepe/.pm2
[PM2] PM2 Successfully daemonized
5.3.1
```

Se ha arrancado pome demonizado


```sh
pepe@ip-172-31-39-104:~$ ps aux | grep pm2
    pepe       11005  0.6  4.8 628376 46720 ?        Ssl  07:00   0:00 PM2 v5.3.1: God Daemon (/home/pepe/.pm2)
    pepe       11017  0.0  0.2   7008  2304 pts/1    S+   07:00   0:00 grep --color=auto pm2
```

¿Cómo le decimos que vigile esta app? https://pm2.keymetrics.io/docs/usage/pm2-doc-single-page/

* diciéndole el archivo js que quiero que arranque ¿como ued saber qué archivo arranca el chat?
* 
```sh
pepe@ip-172-31-39-104:~$ ls -l
total 36
        -rw------- 1 pepe pepe  214 Feb 11 19:28 .bash_history
        -rw-r--r-- 1 pepe pepe  220 Feb 11 15:32 .bash_logout
        -rw-r--r-- 1 pepe pepe 3968 Feb 11 15:51 .bashrc
        drwx------ 3 pepe pepe 4096 Feb 11 15:39 .config
        drwxrwxr-x 4 pepe pepe 4096 Feb 11 16:12 .npm
        drwxrwxr-x 8 pepe pepe 4096 Feb 11 16:07 .nvm
        drwxrwxr-x 5 pepe pepe 4096 Feb 12 07:00 .pm2
        -rw-r--r-- 1 pepe pepe  807 Feb 11 15:32 .profile
        drwxrwxr-x 7 pepe pepe 4096 Feb 11 16:12 node-chat
pepe@ip-172-31-39-104:~$ cd node-chat/
pepe@ip-172-31-39-104:~/node-chat$ cat package.json
        {
        "name": "node-chat",
        "version": "1.0.7",
        "private": true,
        "scripts": {
            "start": "node app.js" # <----------- NOS LO DICE
        },
        "dependencies": {
            "debug": "~2.1.1",
            "ejs": "~2.3.1",
            "express": "~4.12.2",
            "readline": "0.0.7",
            "serve-favicon": "~2.2.0",
            "sockjs": "~0.3.15",
            "chalk": "~1.0.0",
            "underscore.string": "~3.0.3"
        }
        }
```

instalamos con el archivo

```sh
pepe@ip-172-31-39-104:~/node-chat$ pm2 start app.js  # estando en la carpeta que toca
            [PM2] Starting /home/pepe/node-chat/app.js in fork_mode (1 instance)
            [PM2] Done.
            ┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
            │ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
            ├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
            │ 0  │ app                │ fork     │ 0    │ online    │ 0%       │ 31.9mb   │
            └────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
```

```sh
pepe@ip-172-31-39-104:~/node-chat$ pm2 list # me dice qué está cuidando
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ app                │ fork     │ 0    │ online    │ 0%       │ 50.4mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
```

Si quieres ver todos los datos del proceso que está cuidando

```sh
pm2 show 0 # este cero es el id

        Describing process with id 0 - name app 
        ┌───────────────────┬────────────────────────────────────┐
        │ status            │ online                             │
        │ name              │ app                                │
        │ namespace         │ default                            │
        │ version           │ 1.0.7                              │
        │ restarts          │ 0                                  │
        │ uptime            │ 5m                                 │
        │ script path       │ /home/pepe/node-chat/app.js        │
        │ script args       │ N/A                                │
        │ error log path    │ /home/pepe/.pm2/logs/app-error.log │
        │ out log path      │ /home/pepe/.pm2/logs/app-out.log   │
        │ pid path          │ /home/pepe/.pm2/pids/app-0.pid     │
        │ interpreter       │ node                               │
        │ interpreter args  │ N/A                                │
        │ script id         │ 0                                  │
        │ exec cwd          │ /home/pepe/node-chat               │
        │ exec mode         │ fork_mode                          │
        │ node.js version   │ 16.20.2                            │
        │ node env          │ N/A                                │
        │ watch & reload    │ ✘                                  │
        │ unstable restarts │ 0                                  │
        │ created at        │ 2024-02-12T07:06:46.497Z           │
        └───────────────────┴────────────────────────────────────┘
        Revision control metadata 
        ┌──────────────────┬────────────────────────────────────────────────────┐
        │ revision control │ git                                                │
        │ remote url       │ https://github.com/alexjust-data/node-chat.git     │
        │ repository root  │ /home/pepe/node-chat                               │
        │ last update      │ 2024-02-12T07:06:46.749Z                           │
        │ revision         │ 69bc2974b4ec937e43e88f82519f909ae12315c2           │
        │ comment          │ Merge pull request #51 from victoriaquasar/patch-1 │
        │ branch           │ master                                             │
        └──────────────────┴────────────────────────────────────────────────────┘
        Actions available 
        ┌────────────────────────┐
        │ km:heapdump            │
        │ km:cpu:profiling:start │
        │ km:cpu:profiling:stop  │
        │ km:heap:sampling:start │
        │ km:heap:sampling:stop  │
        └────────────────────────┘
        Trigger via: pm2 trigger app <action_name>

        Code metrics value 
        ┌────────────────────────┬───────────┐
        │ Used Heap Size         │ 9.98 MiB  │
        │ Heap Usage             │ 83.92 %   │
        │ Heap Size              │ 11.89 MiB │
        │ Event Loop Latency p95 │ 1.18 ms   │
        │ Event Loop Latency     │ 0.33 ms   │
        │ Active handles         │ 5         │
        │ Active requests        │ 0         │
        └────────────────────────┴───────────┘
        Divergent env variables from local env 


        Add your own code metrics: http://bit.ly/code-metrics
        Use `pm2 logs app [--lines 1000]` to display logs
        Use `pm2 env 0` to display environment variables
        Use `pm2 monit` to monitor CPU and Memory usage app
``` 

También puedes verlo a través de 

```sh
pepe@ip-172-31-39-104:~/node-chat$ ps aux | grep chat
    pepe       11034  0.5  5.3 631784 52172 ?        Ssl  07:06   0:00 node /home/pepe/node-chat/app.js # aquí también
    pepe       11062  0.0  0.2   7008  2304 pts/1    S+   07:08   0:00 grep --color=auto chat
```
¿qué pid tiene el proceso? `11034`
¿quien ejecuta este proceso? `pepe`     

¿Cual es la razon de exister este gestor de procesos? una de ellas que nunca miriera la app. Matemos la aplicacion.

```sh
kill 11034
``` 

si te vas a chatear `http://54.224.151.83:3000/`, la app sigue funcionando.

```sh
pepe@ip-172-31-39-104:~/node-chat$ ps aux | grep chat
    pepe       11124  0.5  5.5 633196 53952 ?        Ssl  07:20   0:00 node /home/pepe/node-chat/app.js
    pepe       11140  0.0  0.2   7008  2304 pts/1    S+   07:21   0:00 grep --color=auto chat
```

Sigue con otra `pid:11124` lo han resucitado

```sh
pepe@ip-172-31-39-104:~/node-chat$ pm2 list
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ app                │ fork     │ 1    │ online    │ 0%       │ 52.7mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
```

Esto `↺ : 1` significa que lo han patado una vez, y así sucesibamente.

Imagínate que cuaquier día por lanoche el servidor se reconfigura solo y se reinicia ¿seguirá el chat?

```sh
pepe@ip-172-31-39-104:~/node-chat$ logout
ubuntu@ip-172-31-39-104:~$ sudo reboot
ubuntu@ip-172-31-39-104:~$ Connection to 54.224.151.83 closed by remote host.
        Connection to 54.224.151.83 closed.
```

Cuando tu arrancas algo generalmente no se arrranca solo.

Si te vas a la IP funciona nginx

![](img/25.png)

Si te vas a las DNS funciona nginx

![](img/26.png)

No está funcionando el puerto 3000

![](img/27.png)


conectamos con el servidor y miramos si hay algún proceso abierto de `pm2` y no hay ninguno

```sh
ubuntu@ip-172-31-39-104:~$ ps aux | grep pm2
ubuntu       793  0.0  0.2   7008  2304 pts/0    S+   07:30   0:00 grep --color=auto pm2
``` 

Algo hemos de hacer para que se arranque con el servidor.


https://www.digitalocean.com/community/tutorials

La gúia está muy bien para configurar servidores y cositas


https://www.digitalocean.com/community/tutorials/how-to-use-pm2-to-setup-a-node-js-production-environment-on-an-ubuntu-vps#run-your-app-using-pm2-and-ensure-that-your-node-js-application-starts-automatically-when-your-server-restarts

Run this command to run your application as a service by typing the following:

```sh

```

No puedo ejecutar ``pm2` con usuario ubuntu

```sh
ubuntu@ip-172-31-39-104:~$ pm2
        Command 'pm2' not found, did you mean:
        command 'pmi' from deb powermanagement-interface (0.3.21)
        command 'gm2' from deb gm2 (4:11.2.0-1ubuntu1)
        command 'wm2' from deb wm2 (4+svn20090216-4build1)
        command 'pmw' from deb pmw (1:4.50-1)
        command 'pms' from deb pms (0.42-1build4)
        command 'tpm2' from deb tpm2-tools (5.2-1build1)
        command 'pmg' from deb python3-pymatgen (2022.0.17+dfsg1-1build1)
        command 'pom2' from deb libpod-pom-perl (2.01-3)
        command 'pmc' from deb linuxptp (3.1.1-3)
        command 'pm' from deb powerman (2.3.5-1build2)
        Try: sudo apt install <deb name>

pepe@ip-172-31-39-104:~$ pm2
        usage: pm2 [options] <command>

        pm2 -h, --help             all available commands and options
        pm2 examples               display pm2 usage examples
        pm2 <command> -h           help on a specific command

        Access pm2 files in ~/.pm2
```

Estamos instalando nvm sólo para el usuario `pepe` como hemos instaldo `pm2`? ` npm install pm2 -g` entonces, si sólo `npm` está instalado en el usuario `pepe` entonces `pm2` solo se ha instaldo para `pepe`

De ehcho fíjate donde está instalado `/home/pepe/`
```sh
pepe@ip-172-31-39-104:~$ which pm2
        /home/pepe/.nvm/versions/node/v16.20.2/bin/pm2

pepe@ip-172-31-39-104:~$ which nginx
        /usr/sbin/nginx

pepe@ip-172-31-39-104:~$ which node
        /home/pepe/.nvm/versions/node/v16.20.2/bin/node
```

Entonces para que `pm2` arranque cuando cae el servidor

```sh
pepe@ip-172-31-39-104:~$ pm2 startup
    [PM2] Init System found: systemd
    [PM2] To setup the Startup Script, copy/paste the following command:
sudo env PATH=$PATH:/home/pepe/.nvm/versions/node/v16.20.2/bin /home/pepe/.nvm/versions/node/v16.20.2/lib/node_modules/pm2/bin/pm2 startup systemd -u pepe --hp /home/pepe
```

> [!NOTE]
> esto es lo más jodido de entender de pm2

Si leemos dice:

* [PM2] Init System found: systemd
* [PM2] To setup the Startup Script, copy/paste the following command:

Copia y pega el comando

¿Qué hace `pm2 startup`? analiza el ecosistema para ver como se tiene que instalar; y en una de las fases descubre que el sistema de inicio es `systemd` porque los nuevo linux utilizan para la gestion de los servicios.
Como ahora que está instalado dentro del usuario `pepe` te genera este comando desglosado para entender mejor cada parte:

* `sudo`: Ejecuta el comando que sigue con privilegios de superusuario ubuntu, lo que es necesario para realizar cambios en los servicios de inicio del sistema.

* `env PATH=$PATH:/home/pepe/.nvm/versions/node/v16.20.2/bin`: Establece una variable de entorno PATH que se utiliza para determinar dónde buscar los ejecutables. Aquí, está añadiendo el directorio binario de la versión específica de Node.js instalada a través de nvm (Node Version Manager) al PATH actual.

* `/home/pepe/.nvm/versions/node/v16.20.2/lib/node_modules/pm2/bin/pm2`: Es el camino al ejecutable pm2 que se quiere utilizar.

* `startup systemd`: Este es el comando de pm2 que configura el sistema para arrancar pm2 al inicio. systemd es el sistema de inicio y gestión de servicios utilizado por muchas distribuciones de Linux modernas.

* `-u pepe`: Especifica bajo qué usuario se debe ejecutar el servicio pm2 al inicio. En este caso, se está configurando para que se ejecute como el usuario pepe.

* `--hp /home/pepe`: Establece el directorio home del usuario con el que se ejecutará el servicio pm2. Es una abreviatura de --home-path.

Esto te configura todo para que arranque cuando se cae el sistema con el usuario `pepe`


```sh
pepe@ip-172-31-39-104:~$ logout
ubuntu@ip-172-31-39-104:~$ sudo env PATH=$PATH:/home/pepe/.nvm/versions/node/v16.20.2/bin /home/pepe/.nvm/versions/node/v16.20.2/lib/node_modules/pm2/bin/pm2 startup systemd -u pepe --hp /home/pepe

                        -------------

__/\\\\\\\\\\\\\____/\\\\____________/\\\\____/\\\\\\\\\_____
 _\/\\\/////////\\\_\/\\\\\\________/\\\\\\__/\\\///////\\\___
  _\/\\\_______\/\\\_\/\\\//\\\____/\\\//\\\_\///______\//\\\__
   _\/\\\\\\\\\\\\\/__\/\\\\///\\\/\\\/_\/\\\___________/\\\/___
    _\/\\\/////////____\/\\\__\///\\\/___\/\\\________/\\\//_____
     _\/\\\_____________\/\\\____\///_____\/\\\_____/\\\//________
      _\/\\\_____________\/\\\_____________\/\\\___/\\\/___________
       _\/\\\_____________\/\\\_____________\/\\\__/\\\\\\\\\\\\\\\_
        _\///______________\///______________\///__\///////////////__


                          Runtime Edition

        PM2 is a Production Process Manager for Node.js applications
                     with a built-in Load Balancer.

                Start and Daemonize any application:
                $ pm2 start app.js

                Load Balance 4 instances of api.js:
                $ pm2 start api.js -i 4

                Monitor in production:
                $ pm2 monitor

                Make pm2 auto-boot at server restart:
                $ pm2 startup

                To go further checkout:
                http://pm2.io/


                        -------------

[PM2] Init System found: systemd
```

Reiniciamos el ordenador 

```sh
ubuntu@ip-172-31-39-104:~$ sudo reboot
ubuntu@ip-172-31-39-104:~$ Connection to 54.224.151.83 closed by remote host.
        Connection to 54.224.151.83 closed.


➜  react-redux-todo-app git:(master) ✗ ssh -i ../Despliegue_AWS/web15.pem ubuntu@54.224.151.83
        Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 6.2.0-1018-aws x86_64)

        * Documentation:  https://help.ubuntu.com
        * Management:     https://landscape.canonical.com
        * Support:        https://ubuntu.com/advantage

        System information as of Mon Feb 12 07:55:37 UTC 2024

        System load:  0.66845703125     Processes:             104
        Usage of /:   34.3% of 7.57GB   Users logged in:       0
        Memory usage: 24%               IPv4 address for eth0: 172.31.39.104
        Swap usage:   0%

        * Ubuntu Pro delivers the most comprehensive open source security and
        compliance features.

        https://ubuntu.com/aws/pro

        Expanded Security Maintenance for Applications is not enabled.

        26 updates can be applied immediately.
        To see these additional updates run: apt list --upgradable

        Enable ESM Apps to receive additional future security updates.
        See https://ubuntu.com/esm or run: sudo pro status


        Last login: Mon Feb 12 07:30:26 2024 from 85.87.66.72

```

```sh
ubuntu@ip-172-31-39-104:~$ ps aux | grep pm2
pepe         573  0.5  5.2 828784 51200 ?        Ssl  07:54   0:00 PM2 v5.3.1: God Daemon (/home/pepe/.pm2)
ubuntu       820  0.0  0.2   7008  2304 pts/0    S+   07:56   0:00 grep --color=auto pm2
```

El chat está funcionando `http://54.224.151.83:3000/`

`pm2` cuando arrancas varias aplicacon es con `pm2`

Si ne te funciona has de saber que antes se hacía `pm2 save` en este punto para que funcionara.

---
> [!IMPORTANT]
> 
> ## 3do paso del CASO 1, Nhinx como proxy inverso**
>
> ¿quien es el responsable de arrancar la aplicación? ahora nosotros ya no ejecutamos el `npm start`, ahora es pm2.  
> Funciona, entonces ... ¿que falta ahora?
>
> Mira tu dirección de browser del chat ... `http://54.224.151.83:3000/` quitemos ese `:3000`
---

¿Como acceder al chat sin la necesidad de acceder al 3000?   

**Solucion** 

Pues lo ejecuto en el puerto 80.


```sh
ubuntu@ip-172-31-39-104:~$ sudo -u pepe -i
pepe@ip-172-31-39-104:~$ cd node-chat/
pepe@ip-172-31-39-104:~/node-chat$ ls -l
        total 92
        -rw-rw-r--  1 pepe pepe  1079 Feb 11 16:06 LICENSE
        -rw-rw-r--  1 pepe pepe  2691 Feb 11 16:06 README.md
        -rw-rw-r--  1 pepe pepe 14805 Feb 11 16:06 app.js
        -rw-rw-r--  1 pepe pepe   234 Feb 11 16:06 config.json
        drwxrwxr-x  2 pepe pepe  4096 Feb 11 16:06 lib
        drwxrwxr-x 58 pepe pepe  4096 Feb 11 16:12 node_modules
        -rw-rw-r--  1 pepe pepe 41017 Feb 11 16:12 package-lock.json
        -rw-rw-r--  1 pepe pepe   347 Feb 11 16:06 package.json
        drwxrwxr-x  7 pepe pepe  4096 Feb 11 16:06 public
        drwxrwxr-x  2 pepe pepe  4096 Feb 11 16:06 views

pepe@ip-172-31-39-104:~/node-chat$ cat config.json
        {
            "log": true,
            "port": 3000,
            "url": "/",
            "ssl": {
                "use": false,
                "key": "/path/to/your/ssl.key",
                "cert": "/path/to/your/ssl.crt"	
            },
                "readline": {
                    "use": true,
                "prompt": "[--:--:--][CONSOLE] "
                }
        }
```
Sería una tentación combiarlo ahí, pero no funcionará.  

**Problema** 

Cualquier proceso por debajo de un 1024 tiene que ser root.  
Yo quiero que el chat se ejecute en el puerto 80.  
Pero no quiero que la app la ejecute un usuario administrador por problmeas de seguridad.  

Además el 80 soportaba nginx con mucho trafico. Pues vamos a usar nginx para solucionar ese problmea.

![](/img/28.png)

Cada aplicacion (chatapp.com, gitlab.chat, app.com, ci.chatapp.com, blog.chatapp.com) usa una technología diferente (node, ...). Cada uno de estos sistemas se ejecuta en un puerto por encima del 1024 porque así se ejecutan con usuario que tiene provilegio normales; y nginx está en el puerto 80 escuchando; entonces ngins hará de intermediario entre peticiones y le pasará de uno y a otro 

Entonces esto es un **proxy inverso** y ¿como es uno normal? pues hace un trabajo precido pero al revés cuando tienes un proxy te adstrae de lo que hay por detrás.

**Fichero de configuración de sitios**

ejemplo

```sh
    # cualquier cosa que no sea estático, se lo pasamos a node
    location / {
        proxy_set_header Host $http_host;
        proxy_pass http://127.0.0.1:3000; # pasamos a node la petición, en este caso al chat nuestro
        proxy_redirect off; # no redirigimos
}
```

qué pasa si está corriendo en otro servidor? tendrás que poner la ip del otro servidor, lo enviará al otro ordenador.
El problema está si sacrificas la ip o la dns, hemos de elegir. Nuestro caso vamos a desactivar el template de la dns y el chat seguirá por la ip

**desactivamos el template** 

está cargando en defoult

```sh
ubuntu@ip-172-31-39-104:~$ sudo rm /etc/nginx/sites-enabled/default
```

**Configuramos en nuevo sitio del chat**

```sh
ubuntu@ip-172-31-39-104:~$ cd /etc/nginx/
ubuntu@ip-172-31-39-104:/etc/nginx$ cd sites-available/
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo nano chat

        server {
                listen 80 default; # este responde la llamada.
                location / {       # cuando la peticion comienza por barra (cualquir peticion)
                        proxy_pass http://127.0.0.1:3000; # se la pasas a este
                        proxy_redirect off; # no quiero que hagas ninguna redirección.
                }
        }
```

Los dominios en qué se transofrman, que hay detrás, cuado haces un ping a esos dominio se tranforma en una `ip`, la ip de una máquina.
Cuando te hacen una llamada alguien va a responder, en este caso responde el que está por defecto `listen 80 default;`  
Si accedes al servidor por la ip alguien ha de responder a esa petición, el que está por defecto `listen 80 default;`  

NO es o habitual, yo el servidor que monto lo redirijo a google, porque no quiero que nadie me llame por ip. Entonces si quieres sólo tener peticiones por dominio será de otra forma porque cuando pones el default solo es pare recibir las peticiones por ip.

**Activar configuración ~ acceso directo**

```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo ln -s /etc/nginx/sites-available/chat /etc/nginx/sites-enabled/chat
```

**Comprobar que la sintaxi es correcta**

```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

**Recargamos**

```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo systemctl reload nginx
```

si está todo bien debería funcionar el chat por la ip `54.224.151.83`

---

![](/img/29.png)

---

Ahora hay dos intermediario entre el chat y yo, `pm2` y ahora se conecta primero a `nginx` y este te envía a pm2.

**Problema** : lapágina carga pero no chatea. Fíjate que si pones puerte `:3000` funciona pero su lo pasas primero por nginx no chatea. ¿ como solucionamos, qué miramos?   la app va bien porque chatea por el puerto 3000, pero algo ocurre. Nginx carga el chat en el puerto 80 es decir que va bien, pero algo ocurre, nginx y node hablan.

---

![](/img/29.png)

---

no están funcionando los `Websocker` de node.   

**Solucion** 

https://www.nginx.com/blog/websocket-nginx/

```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo nano chat

server {
    listen 80 default; # Escucha en el puerto 80, que es el puerto estándar para HTTP. 
    location / { # Este bloque maneja todas las peticiones que llegan a la raíz del dominio ('/').
        proxy_pass http://127.0.0.1:3000; # Redirecciona las peticiones a la aplicación que se ejecuta en localhost en el puerto 3000.
        proxy_redirect off; # Deshabilita la modificación de las cabeceras de respuesta 'Location' y 'Refresh' por parte de Nginx.
        proxy_http_version 1.1; # Utiliza HTTP/1.1 en la conexión al servidor proxy.
        proxy_set_header Upgrade $http_upgrade; # Establece la cabecera 'Upgrade' par permitir comunicación del protocolo WebSocket.
        proxy_set_header Connection "Upgrade"; # Establece la cabecera 'Connection' par permitir comunicación del protocolo WebSocket.
        proxy_set_header Host $host; # Establece la cabecera 'Host' para pasar el host original solicitado por el cliente.
    }
}

ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo nginx -t
    nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
    nginx: configuration file /etc/nginx/nginx.conf test is successful

ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo systemctl reload nginx
```

> [!NOTE]
> El mejor dato es el que no guardas...
> El mejor paquete es el que no instalas...
> El mejor puerto es que no tienes abierto...
>
> ¿El puerto :3000 hace falta tenerlo abierto? este te ayudó a permitir que 
>* la app conectándote directamente a ella funciona.
>* que la app haciendo que la gestione pm2 funciona también
>* y ya he conseguido que poniendo por delante la aplicacion nginx funcione correctmente.

Borrando ...

---

![](/img/31.png)

---

![](/img/32.png)

---

![](/img/33.png)

---




## CASO 2 con base de datos, necesitamos instalar mongoDB
---

https://parseplatform.org/


Parse es el anterior Firebase. Ponte en la piel de que eres un desarollador mobil que no tienes ni idea de backen ni base de datos y has aprendido hacer app para IOS y Android y necesitas una app que tenga persistencia entre dispositivos. 

Apareció Parse (Sparrest pero bien montado). Te creas una cuenta en Parse y llamas a las Apis para guardar objetos y te da una serie de apis para más cosas
gistionar usiarios, logins, gestionar envío de notificaciones, etc. Lo compró Facebook y como no daba dinero lo cerró. Muchos desarrolladores adquirieron una `deuda técnica` con parse y lo usaban como backen, cuando cerró se quedaron colgados. Facebook liberó el codigo fuente.


> [!NOTE]  
> Vamos a desplegar  
>  **Parse Server and Dashboard**  The REST server and dashboard to manage your data.   
>  https://github.com/parse-community/parse-server-example

¿como funciona? Parecido a Sparrest . PARSE básicamente tiene una REST API

REST API

Save object:
```sh
curl -X POST \ 
  -H "X-Parse-Application-Id: YOUR_APP_ID" \
  -H "Content-Type: application/json" \
  -d '{"score":1337}' \
  http://localhost:1337/parse/classes/GameScore
```

* curl -X POST \  # peticion post
* -H "X-Parse-Application-Id: YOUR_APP_ID" \  # le pasas una cabecera personalizada
* -H "Content-Type: application/json" \
* -d '{"score":1337}' \ # mandas un json
* http://localhost:1337/parse/classes/GameScore # lo envias a la url esta


**INSTALANDO MONGOBD en el servidor**

https://hub.docker.com/_/mongo/tags


Mongo tiene una forma muy sencilla de elegir la version que quieras 

---
![](/img/34.png)

---

Pero nosotros ahora vamos a la pagina oficial 

**Install MongoDB Community Edition**

https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/#install-mongodb-community-edition

---
![](/img/35.png)

---

Como cuando yo hago un `sudo apt install mongo` ubuntu no me da la versión que yo quiero, lo que hará es darle la capacidad a `apt` para que de los paquetes que yo pueda instalar, me instale directamente lo que me da MongoBd. Para hacer esto lo primero es descargarme la clave pública; y [en este caso](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/#install-mongodb-community-edition) MongoBd te está dando su caja con el cerrojo abierto para que te comuniques con él:

```sh
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor
```

**1er paso : [Import the public key used by the package management system](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/#import-the-public-key-used-by-the-package-management-system)**

```sh
# conecto con el servidor
➜  react-redux-todo-app git:(master) ✗ ssh -i ../Despliegue_AWS/web15.pem ubuntu@54.224.151.83

# instalo según instrucciones mongo
ubuntu@ip-172-31-39-104:~$ sudo apt-get install gnupg curl

# importo clave pública
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor
```

**2º paso : [Create a list file for MongoDB](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/#create-a-list-file-for-mongodb)**

```sh
# copiando los paquetes de mongo en el archivo para instalarlo
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
```

**3º paso : [Reload local package database](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/#reload-local-package-database)**

```sh
# recarga base de datos del paquete, actualiza
sudo apt-get update
```

**4to paso : [Install the MongoDB packages](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/#install-the-mongodb-packages)**

```sh
# instalando mongo
sudo apt-get install -y mongodb-org
```

**Run MongoDB** Nos leeríamos [lo siguiente](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/#run-mongodb-community-edition)

**1º Start MongoDB**

```sh
ubuntu@ip-172-31-39-104:~$ sudo systemctl start mongod
```

**2º Verify that MongoDB has started successfully.**

```sh
ubuntu@ip-172-31-39-104:~$ sudo systemctl status mongod # para saber si está trabajando
● mongod.service - MongoDB Database Server
     Loaded: loaded (/lib/systemd/system/mongod.service; disabled; vendor preset: enabled)
     Active: active (running) since Tue 2024-02-13 15:16:08 UTC; 28s ago
       Docs: https://docs.mongodb.org/manual
   Main PID: 3755 (mongod)
     Memory: 156.9M
        CPU: 976ms
     CGroup: /system.slice/mongod.service
             └─3755 /usr/bin/mongod --config /etc/mongod.conf

Feb 13 15:16:08 ip-172-31-39-104 systemd[1]: Started MongoDB Database Server.
Feb 13 15:16:09 ip-172-31-39-104 mongod[3755]: {"t":{"$date":"2024-02-13T15:16:09.773Z"},"s":"I",  "c":"CONTROL",  "id":7484500, ">
lines 1-12/12 (END)
```

```sh
# podemos ver si corre por aquí también
ubuntu@ip-172-31-39-104:~$ ps aux |grep mongo
mongodb     3755  1.8 15.4 2632072 150528 ?      Ssl  15:16   0:01 /usr/bin/mongod --config /etc/mongod.conf
ubuntu      3801  0.0  0.2   7008  2304 pts/0    S+   15:17   0:00 grep --color=auto mongo
```

**Evita la configuración relajada** (lo instalas funciona y te olvidas)


```sh
# este comando nos permite trabajar en mongo
ubuntu@ip-172-31-39-104:~$ mongosh

Current Mongosh Log ID:	65cb8902e04615ce7e952fce
Connecting to:		mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.1.4
Using MongoDB:		7.0.5
Using Mongosh:		2.1.4

For mongosh info see: https://docs.mongodb.com/mongodb-shell/


To help improve our products, anonymous usage data is collected and sent to MongoDB periodically (https://www.mongodb.com/legal/privacy-policy).
You can opt-out by running the disableTelemetry() command.

------
   The server generated these startup warnings when booting
   2024-02-13T15:16:10.099+00:00: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine. See http://dochub.mongodb.org/core/prodnotes-filesystem
   2024-02-13T15:16:10.904+00:00: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
   2024-02-13T15:16:10.904+00:00: vm.max_map_count is too low
------

# trabajando en mongo

test> show databases

        admin   40.00 KiB
        config  12.00 KiB
        local   40.00 KiB

test> exit
```

**Instalando PARSE**

**1º descargando el repo**

```sh
# cambiamos usuario
ubuntu@ip-172-31-39-104:~$ sudo -u pepe -i
# la letra parse final es para que se llame así la carpeta
pepe@ip-172-31-39-104:~$ git clone https://github.com/parse-community/parse-server-example.git parse
        Cloning into 'parse'...
        remote: Enumerating objects: 542, done.
        remote: Counting objects: 100% (83/83), done.
        remote: Compressing objects: 100% (52/52), done.
        remote: Total 542 (delta 46), reused 62 (delta 27), pack-reused 459
        Receiving objects: 100% (542/542), 537.39 KiB | 12.50 MiB/s, done.
        Resolving deltas: 100% (234/234), done.
# viendo la descarga
pepe@ip-172-31-39-104:~$ ls -l
        total 8
        drwxrwxr-x 7 pepe pepe 4096 Feb 11 16:12 node-chat
        drwxrwxr-x 9 pepe pepe 4096 Feb 13 15:26 parse
```

Parse funciona con la versión 8 de node, es decir que hemos de instalar 

```sh
pepe@ip-172-31-39-104:~/parse$ nvm install 18
        Downloading and installing node v18.19.0...
        Downloading https://nodejs.org/dist/v18.19.0/node-v18.19.0-linux-x64.tar.xz...
        ############################################################################################################################ 100.0%
        Computing checksum with sha256sum
        Checksums matched!
        Now using node v18.19.0 (npm v10.2.3)
pepe@ip-172-31-39-104:~/parse$ node --version
v18.19.0
```

**Instalamos dependecias para Parse**

```sh
# instalamos dependencias
pepe@ip-172-31-39-104:~/parse$ npm install

        added 1133 packages, and audited 1396 packages in 25s
        139 packages are looking for funding
        run `npm fund` for details
        34 vulnerabilities (1 low, 20 moderate, 8 high, 5 critical)
        To address issues that do not require attention, run:
        npm audit fix
        To address all issues (including breaking changes), run:
        npm audit fix --force
        Run `npm audit` for details.


# arrancamos
pepe@ip-172-31-39-104:~/parse$ npm start

> parse-server-example@1.2.3 start
> node index.js

warn: DeprecationWarning: The Parse Server option 'allowClientClassCreation' default will change to 'false' in a future version.
warn: DeprecationWarning: The Parse Server option 'allowExpiredAuthDataToken' default will change to 'false' in a future version.
warn: DeprecationWarning: The Parse Server option 'encodeParseObjectInCloudFunction' default will change to 'true' in a future version.

parse-server-example running on port 1337. # fíjate en que puerto , ábrelo
info: Parse LiveQuery Server started running
```
---


> [!NOTE] 
> Como cliente REST vamos a utilizar una extensión de VSC que se llama **Thunder Client** pero vamos es como POSTMAN o otro cualquiera
> Instala la extensión y has una petición `GET`

---

Si llamas al puerto te dará error porque no hemos puesto las cabeceras

--
![](/img/37.png)
--

Las cabeceras que comienzn con `X` son personalizadas puedes poner despues lo que te de la gana

Acuérdate de la docuemntación de Parse que te decía
```sh
curl -X POST \ 
  -H "X-Parse-Application-Id: YOUR_APP_ID" \
  -H "Content-Type: application/json" \
  -d '{"score":1337}' \
  http://localhost:1337/parse/classes/GameScore
```

* -H "X-Parse-Application-Id: YOUR_APP_ID" \  # le pasas una cabecera personalizada

Ahora e da un 404 poruqe haces petición de algo que no existe

---
![](/img/38.png)

---
¿de qué quieres la app, de cervezas???

---
![](/img/39.png)

--- 

NO hay cerveces, vamos crearlas

---
![](/img/40.png)

--- 

Hacemos un GET (acuerdate de quitar los json del body)


---
![](/img/41.png)

--- 

Coje el id de la cerveza alhambra y cambia la nota

---
![](/img/42.png)

--- 

---
![](/img/43.png)

--- 


**¿Y todo esto donde se está guardando?**

Vayamos a mongo a mirar

```sh
pepe@ip-172-31-39-104:~/parse$ mongosh
Current Mongosh Log ID:	65cb9d55e9696be5a60e84aa
Connecting to:		mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.1.4
Using MongoDB:		7.0.5
Using Mongosh:		2.1.4

For mongosh info see: https://docs.mongodb.com/mongodb-shell/


To help improve our products, anonymous usage data is collected and sent to MongoDB periodically (https://www.mongodb.com/legal/privacy-policy).
You can opt-out by running the disableTelemetry() command.

------
   The server generated these startup warnings when booting
   2024-02-13T15:16:10.099+00:00: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine. See http://dochub.mongodb.org/core/prodnotes-filesystem
   2024-02-13T15:16:10.904+00:00: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
   2024-02-13T15:16:10.904+00:00: vm.max_map_count is too low
------

test> show databases
admin    40.00 KiB
config  108.00 KiB
dev     196.00 KiB
local    40.00 KiB

test> use dev
switched to db dev

dev> show collections
_Idempotency
_Role
_SCHEMA
_User
Cervezas
dev> db.Cervezas.find({})
[
  {
    _id: 'ceqNIgCA5M',
    nombre: 'Estrella Galicia',
    puntuacion: 9.5,
    _created_at: ISODate('2024-02-13T16:40:19.365Z'),
    _updated_at: ISODate('2024-02-13T16:40:19.365Z')
  },
  {
    _id: 'E09UEHNE1t',
    nombre: 'Mahou',
    puntuacion: 9,
    _created_at: ISODate('2024-02-13T16:41:16.231Z'),
    _updated_at: ISODate('2024-02-13T16:41:16.231Z')
  },
  {
    _id: '7P1HmwAXHy',
    nombre: 'Alhambra',
    puntuacion: 10,
    _created_at: ISODate('2024-02-13T16:41:28.820Z'),
    _updated_at: ISODate('2024-02-13T16:45:36.992Z')
  }
]
dev> 
```
---
> [!IMPORTANT]
> Todo va bien.... peligro.... qué huele mal?
> Con el usuario Pepe para ver lo que hay dentro de la base de datos de PArse ¿Hemos puesto alguna contraseña?  
> Todo ha funcionado automágicamente. Si alguien entra en el servidor puede acceder a los datos de ala pp perfectamente.
---


Hemos instalado un **configuración relajada**.  Peligro. Problemas de seguridad
Entonces, si nos hubieramos dado cuenta antes de esto ¿cuál era el paso anterior? 
* usar pm2 
* nginx por delante

---
> [!IMPORTANT]
> Siempre la BBDD debe tener ocntraseña y usuario
--- 

**Mongo [Security Checklist](https://www.mongodb.com/docs/manual/administration/security-checklist/#security-checklist)**


---
![](/img/44.png)

--- 

  

https://www.mongodb.com/docs/manual/tutorial/configure-scram-client-authentication/
  

**[3. Create the user administrator](https://www.mongodb.com/docs/manual/tutorial/configure-scram-client-authentication/#create-the-user-administrator)**

```sh
use admin
db.createUser(
  {
    user: "batman",
    pwd: "6y1axb",
    roles: [
      { role: "userAdminAnyDatabase", db: "admin" },
      { role: "readWriteAnyDatabase", db: "admin" }
    ]
  }
)
```

Me conecto a mongo y le doy los datos

```sh
pepe@ip-172-31-39-104:~/parse$ mongosh

Current Mongosh Log ID:	65cba2159a21efaa89194355
Connecting to:		mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.1.4
Using MongoDB:		7.0.5
Using Mongosh:		2.1.4

For mongosh info see: https://docs.mongodb.com/mongodb-shell/

------
   The server generated these startup warnings when booting
   2024-02-13T15:16:10.099+00:00: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine. See http://dochub.mongodb.org/core/prodnotes-filesystem
   2024-02-13T15:16:10.904+00:00: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
   2024-02-13T15:16:10.904+00:00: vm.max_map_count is too low
------

test> use admin
switched to db admin
admin> db.createUser(
...   {
...     user: "batman",
...     pwd: "6y1axb",
...     roles: [
...       { role: "userAdminAnyDatabase", db: "admin" },
...       { role: "readWriteAnyDatabase", db: "admin" }
...     ]
...   }
... )
{ ok: 1 }
admin> 
```

**[4. Re-start the MongoDB instance with access control](https://www.mongodb.com/docs/manual/tutorial/configure-scram-client-authentication/#re-start-the-mongodb-instance-with-access-control)**

```sh
# hemos de añadir al fichero de configuracin esta linea
 security:
    authorization: enabled
```

¿donde crees que stará en el fichero de configuracion de mongo?

```sh
pepe@ip-172-31-39-104:~/parse$ logout
ubuntu@ip-172-31-39-104:~$ sudo nano /etc/mongod.conf


# mongod.conf
# for documentation of all options, see:
#   http://docs.mongodb.org/manual/reference/configuration-options/
# Where and how to store data.
storage:
  dbPath: /var/lib/mongodb
#  engine:
#  wiredTiger:
# where to write logging data.
systemLog:
  destination: file
  logAppend: true
  path: /var/log/mongodb/mongod.log
# network interfaces
net:
  port: 27017
  bindIp: 127.0.0.1
# how the process runs
processManagement:
  timeZoneInfo: /usr/share/zoneinfo

#security:
security:
    authorization: enabled

#operationProfiling:
#replication:
#sharding:
## Enterprise-Only Options:
#auditLog:
```

**Reiniciamos mongo y confirmamos**

```sh
ubuntu@ip-172-31-39-104:~$ sudo systemctl restart mongod
ubuntu@ip-172-31-39-104:~$ sudo systemctl status mongod

● mongod.service - MongoDB Database Server
     Loaded: loaded (/lib/systemd/system/mongod.service; disabled; vendor preset: enabled)
     Active: active (running) since Tue 2024-02-13 17:15:27 UTC; 11s ago
       Docs: https://docs.mongodb.org/manual
   Main PID: 5989 (mongod)
     Memory: 200.1M
        CPU: 1.239s
     CGroup: /system.slice/mongod.service
             └─5989 /usr/bin/mongod --config /etc/mongod.conf

Feb 13 17:15:27 ip-172-31-39-104 systemd[1]: Stopped MongoDB Database Server.
Feb 13 17:15:27 ip-172-31-39-104 systemd[1]: mongod.service: Consumed 33.067s CPU time.
Feb 13 17:15:27 ip-172-31-39-104 systemd[1]: Started MongoDB Database Server.
Feb 13 17:15:28 ip-172-31-39-104 mongod[5989]: {"t":{"$date":"2024-02-13T17:15:28.101Z"},"s":"I",  "c":"CONTROL",  "id":7484500, ">
lines 1-14/14 (END)
```

**[5. Connect and authenticate as the user administrator](https://www.mongodb.com/docs/manual/tutorial/configure-scram-client-authentication/#connect-and-authenticate-as-the-user-administrator)**

Autentíficate como admin

```sh
mongosh --port 27017  --authenticationDatabase \
    "admin" -u "myUserAdmin" -p
```

vamos a ello...


```sh
ubuntu@ip-172-31-39-104:~$ mongosh --authenticationDatabase admin -u batman -p
Enter password: ******

Current Mongosh Log ID:	65cba48af7e9e6ce1b279ca0
Connecting to:		mongodb://<credentials>@127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&authSource=admin&appName=mongosh+2.1.4
Using MongoDB:		7.0.5
Using Mongosh:		2.1.4

For mongosh info see: https://docs.mongodb.com/mongodb-shell/

test> show databases
admin   132.00 KiB
config  108.00 KiB
dev     196.00 KiB
local    72.00 KiB
test> 
```

**Cada app debe tener acceso a su base de datos de mongo**

puedo tener 15 apps y cada una ha de acceder a su base de datos dentro de mongo.

> [!IMPORTANT]
> Cada app debe tener 
> * su propia base de datos
> * su propio usuario de la BBDD
> Cada una un usuario independiente.
--- 

**Creando usuario para Parse ~ [Users](https://www.mongodb.com/docs/manual/tutorial/create-users/#configure-users-for-self-hosted-deployments)**

**[1 Connect and authenticate](https://www.mongodb.com/docs/manual/tutorial/create-users/#connect-and-authenticate)**

```sh
mongosh --port 27017  --authenticationDatabase \
    "admin" -u "myUserAdmin" -p
```

**[2 Create additional users for your deployment](https://www.mongodb.com/docs/manual/tutorial/create-users/#create-additional-users-for-your-deployment)** 

```sh
# plantilla
use test
db.createUser(
  {
    user: "myTester",
    pwd:  passwordPrompt(),   // or cleartext password
    roles: [ { role: "readWrite", db: "test" },
             { role: "read", db: "reporting" } ]
  }
)
```

```sh
# en el servidor
use parsedb
db.createUser(
  {
    user: "axempleparse",
    pwd:  "axempleparse",
    roles: [ { role: "readWrite", db: "parsedb" }]
  }
)
```

```sh
# me conecto como admin
ubuntu@ip-172-31-39-104:~$ mongosh --authenticationDatabase admin -u batman -p
Enter password: ******
Current Mongosh Log ID:	65cba7587a97ad3102dda205
Connecting to:		mongodb://<credentials>@127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&authSource=admin&appName=mongosh+2.1.4
Using MongoDB:		7.0.5
Using Mongosh:		2.1.4

For mongosh info see: https://docs.mongodb.com/mongodb-shell/

# muestro bases de datos existentes
test> show databases
admin   132.00 KiB
config  108.00 KiB
dev     196.00 KiB
local    72.00 KiB

# creo BBDD de parse
test> use parsedb

# creo contraseñas y user para parse
parsedb> db.createUser(
...   {
...     user: "axempleparse",
...     pwd:  "axempleparse",
...    roles: [ { role: "readWrite", db: "parsedb" }]
...   }
... )
{ ok: 1 }
parsedb> 

parsedb> exit
ubuntu@ip-172-31-39-104:~$ 
```
---
> [!IMPORTANT]
> Has creado credenciales  
> Prueba que funciona antes de configurar cualquier cosa en Parse
--- 

```sh
# comprobando autentificacion
ubuntu@ip-172-31-39-104:~$ mongosh --authenticationDatabase parsedb -u axempleparse -p
Enter password: ************
Current Mongosh Log ID:	65cba8e65a3940b28780b644
Connecting to:		mongodb://<credentials>@127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&authSource=parsedb&appName=mongosh+2.1.4
Using MongoDB:		7.0.5
Using Mongosh:		2.1.4

For mongosh info see: https://docs.mongodb.com/mongodb-shell/

# compruebo si tiene acceso a cosas
test> show databases

# en dev teníamos las bbdd de las cervezas
test> use dev
switched to db dev
dev> show collections
MongoServerError[Unauthorized]: not authorized on dev to execute command { listCollections: 1, filter: {}, cursor: {}, nameOnly: true, authorizedCollections: false, lsid: { id: UUID("8777c6a7-cebe-4934-8968-589e1a495803") }, $db: "dev", $readPreference: { mode: "primaryPreferred" } }
dev> 

# yo sabía que había una bbdd de Cervezas
dev> db.Cervezas.find()
MongoServerError[Unauthorized]: not authorized on dev to execute command { find: "Cervezas", filter: {}, lsid: { id: UUID("8777c6a7-cebe-4934-8968-589e1a495803") }, $db: "dev" }
dev> 


switched to db parsedb
parsedb> show collections # no me da error para ver las collections del parsedb

parsedb> 
```

**Hay que decirle a la app Parse que utilice ess datos**

Parse en su doc no nos dice gran cosa https://github.com/parse-community/parse-server-example

Pero como sabemos un poco, el archivo `package.json`

```json
  "scripts": {
    "coverage": "TESTING=true nyc jasmine",
    "lint": "eslint --cache ./cloud && eslint --cache index.js && eslint --cache ./spec",
    "lint-fix": "eslint --cache --fix ./cloud && eslint --cache --fix index.js && eslint --cache --fix ./spec",
    "prettier": "prettier --write '{cloud,spec}/{**/*,*}.js' 'index.js'",
    "start": "node index.js",
```
arranca por aquí `"start": "node index.js",`

podemos ver esto

```js
export const config = {
  databaseURI:
    process.env.DATABASE_URI || process.env.MONGODB_URI || 'mongodb://localhost:27017/dev',
  cloud: process.env.CLOUD_CODE_MAIN || __dirname + '/cloud/main.js',
  appId: process.env.APP_ID || 'myAppId',
  masterKey: process.env.MASTER_KEY || '', //Add your master key here. Keep it secret!
  serverURL: process.env.SERVER_URL || 'http://localhost:1337/parse', // Don't forget to change to https if needed
  liveQuery: {
    classNames: ['Posts', 'Comments'], // List of classes to support for query subscriptions
  },
};
```

```js
export const config = {
  databaseURI:
    process.env.DATABASE_URI || process.env.MONGODB_URI || 'mongodb://localhost:27017/dev',
```

Ya sabemos porque nos ha funcionado antes a la primera, si no existe las dos primeras toma la configuracion 'mongodb://localhost:27017/dev'.

Este es el valor que le pusimos en el Header : `appId: process.env.APP_ID || 'myAppId',`

---
> [!IMPORTANT]
> NUNCA JAMAS EN LA VIDA SE TOCA EN PRODUCCIÓN EL CODIGO DE LA APLICACION
> Si estás tentado de colocar ahí la direccion de mongoDB y listo ..... error
> process.env.DATABASE_URI || process.env.MONGODB_URI || `'mongodb://localhost:27017/dev'`,
> 
> Si lo hces estás generando una versioni diferente de codigo
---

Fíjate que Parse te permite configurar la aplicación a través de variables de entorno

```js
process.`env.DATABASE_URI` || process.`env.MONGODB_URI` || 'mongodb://localhost:27017/dev',
```

Hemos de usar la versión correcta para la apicacion

```sh
ubuntu@ip-172-31-39-104:~$ sudo -u pepe -i
pepe@ip-172-31-39-104:~$ cd parse/
pepe@ip-172-31-39-104:~/parse$ nvm ls
        v8.17.0
       v10.24.1
->     v16.20.2
       v18.19.0
pepe@ip-172-31-39-104:~/parse$ nvm uninstall 8
        Uninstalled node v8.17.0
pepe@ip-172-31-39-104:~/parse$ nvm uninstall 10
        Uninstalled node v10.24.1
pepe@ip-172-31-39-104:~/parse$ nvm ls
->     v16.20.2
       v18.19.0
pepe@ip-172-31-39-104:~/parse$ nvm use 18
        Now using node v18.19.0 (npm v10.2.3)
```

Variabes de entorno ¿como puedo ver las variables de entonrno definidas en mi servidor?

```sh
pepe@ip-172-31-39-104:~/parse$ env
        SHELL=/bin/bash
        NVM_INC=/home/pepe/.nvm/versions/node/v18.19.0/include/node
        SUDO_GID=1000
        SUDO_COMMAND=/bin/bash
        SUDO_USER=ubuntu
        PWD=/home/pepe/parse
        LOGNAME=pepe
        HOME=/home/pepe
```

¿como definimos una variable de entorno?

```sh
# como es una uri hemos de usar un protocolo de conexion (puerto de mongo 27017)
export DATABASE_URI=mongodb://axempleparse:axempleparse@127.0.0.1:27017/parsedb
```

* axempleparse:axempleparse@ -> usuario y contraseña creados antes
* 127.0.0.1:27017/ -> localhost con puerto de mongo
* parsedb -> base de datos que queremos conectar

```sh
pepe@ip-172-31-39-104:~/parse$ env
        SHELL=/bin/bash
        NVM_INC=/home/pepe/.nvm/versions/node/v18.19.0/include/node
        SUDO_GID=1000
        DATABASE_URI=mongodb://axempleparse:axempleparse@127.0.0.1:27017/parsedb
```

Arrancamos y debería funcionar

```sh
pepe@ip-172-31-39-104:~/parse$ npm start

> parse-server-example@1.2.3 start
> node index.js

warn: DeprecationWarning: The Parse Server option 'allowClientClassCreation' default will change to 'false' in a future version.
warn: DeprecationWarning: The Parse Server option 'allowExpiredAuthDataToken' default will change to 'false' in a future version.
warn: DeprecationWarning: The Parse Server option 'encodeParseObjectInCloudFunction' default will change to 'true' in a future version.
        parse-server-example running on port 1337.
        info: Parse LiveQuery Server started running
```

Me conecto al puerto 1337

---
![](/img/37.png)

---

Se conecta y es normal que esté vacía porque lo habíamos llenado en otra base de datos, ahora es **parsedb** pero puedes crear todo de nuevo y funcionará
Repite la creacion de cervezas como has hecho antes.

**CHEKING**

**1º probar la aplicacion directamente conectandome a ella en su puerto**
* la app la he arrancado en su puerto y parece que funcona bien
  
**Hacer que la app funcione sola con pm2**

> [!WARNING]
> Si ahora te desconectas del servidor y te vuelver a conectar verás que al haver un 

```sh
ubuntu@ip-172-31-39-104:~$ sudo -u pepe -i
pepe@ip-172-31-39-104:~$ env
        SHELL=/bin/bash
        NVM_INC=/home/pepe/.nvm/versions/node/v16.20.2/include/node
        SUDO_GID=1000
        SUDO_COMMAND=/bin/bash
        SUDO_USER=ubuntu
        PWD=/home/pepe
        LOGNAME=pepe
        HOME=/home/pepe
        LANG=C.UTF-8
```

A crear una sesion nuevo las variables de entorno no se persisten, esto es un problema con `pm2`. Pero `pm2` lo tiene en cuenta ...

La app si la ejecuto yo funciona...
Ahora vamos a que pm2 lo haga por mi, pero como Parse el fichero .env no lo soporte hemos de meter variables de entorno. 

--- 
> [!NOTE]
> Conjunto de buenas practicas https://12factor.net/
> https://www.redhat.com/architect/12-factor-app 
> Léete esto
--- 

**Configuration File**

https://pm2.keymetrics.io/docs/usage/application-declaration/

hemos de definir una lista de aplicacines para definir el script que se tiene que ejecutar

- Generate configuration
- Acting on Configuration File
- Switching environments


```sh
pepe@ip-172-31-39-104:~$ ls -l
total 8
drwxrwxr-x  7 pepe pepe 4096 Feb 11 16:12 node-chat
drwxrwxr-x 11 pepe pepe 4096 Feb 13 16:02 parse
```

```sh
# Configuration File -> Generate configuration
# genera un archivo nuevo
pepe@ip-172-31-39-104:~$ pm2 init simple
        File /home/pepe/ecosystem.config.js generated


pepe@ip-172-31-39-104:~$ ls -l
        total 12
        -rw-rw-r--  1 pepe pepe   83 Feb 13 19:21 ecosystem.config.js
        drwxrwxr-x  7 pepe pepe 4096 Feb 11 16:12 node-chat
        drwxrwxr-x 11 pepe pepe 4096 Feb 13 16:02 parse
```

**CAMBIANDO EN EL CHAT**


Tenemos el chat corriendo en pm2

```sh
# aplicacion es arrancadas con pm2
pepe@ip-172-31-39-104:~$ pm2 list
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ app                │ fork     │ 0    │ online    │ 0%       │ 40.1mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
# parando pm2 para app
pepe@ip-172-31-39-104:~$ pm2 stop app
[PM2] Applying action stopProcessId on app [app](ids: [ 0 ])
[PM2] [app](0) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ app                │ fork     │ 0    │ stopped   │ 0%       │ 0b       │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
# eliminando pm2 de app
pepe@ip-172-31-39-104:~$ pm2 delete app
[PM2] Applying action deleteProcessId on app [app](ids: [ 0 ])
[PM2] [app](0) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.

```
Esto es muy importante:
`[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.`

Esa lista de aplicaciones guardadas son las que pm2 va a arrancar si quieres ejecutar esa lista has de actualizarla. Si vulever arrancer pm2 arrancará ala app eliminada porque no la has sincronizado.

```sh
pepe@ip-172-31-39-104:~$ cat node-chat/package.json
{
  "name": "node-chat",
  "version": "1.0.7",
  "private": true,
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {
    "debug": "~2.1.1",
    "ejs": "~2.3.1",
    "express": "~4.12.2",
    "readline": "0.0.7",
    "serve-favicon": "~2.2.0",
    "sockjs": "~0.3.15",
    "chalk": "~1.0.0",
    "underscore.string": "~3.0.3"
  }
}
```

```sh
pepe@ip-172-31-39-104:~$ pwd
        /home/pepe
```

```sh
pepe@ip-172-31-39-104:~$ nano ecosystem.config.js

# esto hay dentro
# ANTES
module.exports = {
  apps : [{
    name   : "app1",
    script : "./app.js"
  }]
}


# DESPUES (pinesa que estás en /home/pepe entonces has de poner la ruta crrecta "./node-chat/app.js")
module.exports = {
  apps : [{
    name   : "chat",
    script : "./node-chat/app.js"
  }]
}
```

```sh
pepe@ip-172-31-39-104:~$ pm2 start ecosystem.config.js 
[PM2][WARN] Applications chat not running, starting...
[PM2] App [chat] launched (1 instances)
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ chat               │ fork     │ 0    │ online    │ 0%       │ 15.9mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.

pepe@ip-172-31-39-104:~$ pm2 list
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ chat               │ fork     │ 0    │ online    │ 0%       │ 57.5mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
pepe@ip-172-31-39-104:~$ 
```

parece que arranca bien, vamos a comprobar que funciona el chat por el prouser `http://54.224.151.83/` vía ip. **¡y.. funciona!** Pero no me gusta

Yo le estoy diciendo la carpeta de ejecucion de esto es el home del usuario y realmente la carpeta de ejecución debe´ria ser la carpeta de node-chat/ . Par decir cuál es la carpeta de ejecución fuerzaas en su carpeta con **cwd**

[Attributes available]([Attributes available](https://pm2.keymetrics.io/docs/usage/application-declaration/)) : `cwd	(string)	“/var/www/”	the directory from which your app will be launched`


```sh
pepe@ip-172-31-39-104:~$ nano ecosystem.config.js

# combio path
module.exports = {
  apps : [{
    name   : "chat",
    cwd    : "/home/pepe/node-chat",
    script : "app.js"
  }]
}

pepe@ip-172-31-39-104:~$ pm2 start ecosystem.config.js 
[PM2] Applying action restartProcessId on app [chat](ids: [ 0 ])
[PM2] [chat](0) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ chat               │ fork     │ 1    │ online    │ 0%       │ 16.0mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
```


**CAMBIANDO EN PARSE**

```sh
pepe@ip-172-31-39-104:~$ ls -l
        total 12
        -rw-rw-r--  1 pepe pepe  208 Feb 13 19:45 ecosystem.config.js
        drwxrwxr-x  7 pepe pepe 4096 Feb 11 16:12 node-chat
        drwxrwxr-x 11 pepe pepe 4096 Feb 13 16:02 parse
```

```sh
pepe@ip-172-31-39-104:~$ cat parse/package.json
{
  "name": "parse-server-example",
  "version": "1.2.3",
  "description": "An example Parse API server using the parse-server module",
  "repository": {
    "type": "git",
    "url": "https://github.com/ParsePlatform/parse-server-example"
  },
  "license": "MIT",
  "main": "index.js",
  "scripts": {
    "coverage": "TESTING=true nyc jasmine",
    "lint": "eslint --cache ./cloud && eslint --cache index.js && eslint --cache ./spec",
    "lint-fix": "eslint --cache --fix ./cloud && eslint --cache --fix index.js && eslint --cache --fix ./spec",
    "prettier": "prettier --write '{cloud,spec}/{**/*,*}.js' 'index.js'",
    "start": "node index.js", # PUEDES VERLO AQUÍ
    "test": "mongodb-runner start && TESTING=true jasmine",
    "watch": "nodemon index.js"
  },
```


```sh
pepe@ip-172-31-39-104:~$ nano ecosystem.config.js

# cambiando el archivo
module.exports = {
  apps : [{
    name   : "chat",
    cwd    : "/home/pepe/node-chat",
    script : "app.js"
  },    
  {
    name   : "parse",
    cwd    : "/home/pepe/parse",
    script : "index.js"
  }  
 ]
}
```

```sh
pepe@ip-172-31-39-104:~$ pm2 start ecosystem.config.js 
[PM2] Applying action restartProcessId on app [chat](ids: [ 0 ])
[PM2] Applying action restartProcessId on app [parse](ids: [ 1 ])
[PM2] [chat](0) ✓
[PM2] [parse](1) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ chat               │ fork     │ 5    │ online    │ 0%       │ 20.6mb   │
│ 1  │ parse              │ fork     │ 1    │ online    │ 0%       │ 16.0mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
```

Dice que funciona pero voy a comprobarlo desde el browser o VSC

![](/img/46.png)

Cuando algo no funciona y no sabemos porqué miramos los logs. En est caso están aquí

```sh
# aquí eston los logs para /pepe/.pm2/logs y esto es un problema
pepe@ip-172-31-39-104:~$ la /home/pepe/.pm2/logs
app-error.log  app-out.log  chat-error.log  chat-out.log  parse-error.log  parse-out.log
```

```sh
pepe@ip-172-31-39-104:~$ pm2 logs parse
[TAILING] Tailing last 15 lines for [parse] process (change the value with --lines option)
/home/pepe/.pm2/logs/parse-out.log last 15 lines:
1|parse    | warn: DeprecationWarning: The Parse Server option 'allowClientClassCreation' default will change to 'false' in a future version.
1|parse    | warn: DeprecationWarning: The Parse Server option 'allowExpiredAuthDataToken' default will change to 'false' in a future version.
1|parse    | warn: DeprecationWarning: The Parse Server option 'encodeParseObjectInCloudFunction' default will change to 'true' in a future version.
1|parse    | error: Received unauthorized error {"error":{"code":13,"codeName":"Unauthorized","ok":0}}
1|parse    | warn: DeprecationWarning: The Parse Server option 'allowClientClassCreation' default will change to 'false' in a future version.
1|parse    | warn: DeprecationWarning: The Parse Server option 'allowExpiredAuthDataToken' default will change to 'false' in a future version.
1|parse    | warn: DeprecationWarning: The Parse Server option 'encodeParseObjectInCloudFunction' default will change to 'true' in a future version.
1|parse    | error: Received unauthorized error {"error":{"code":13,"codeName":"Unauthorized","ok":0}}

/home/pepe/.pm2/logs/parse-error.log last 15 lines:
1|parse    |     at Connection.onMessage (/home/pepe/parse/node_modules/parse-server/node_modules/mongodb/lib/cmap/connection.js:207:30)
1|parse    |     at MessageStream.<anonymous> (/home/pepe/parse/node_modules/parse-server/node_modules/mongodb/lib/cmap/connection.js:60:60)
1|parse    |     at MessageStream.emit (node:events:513:28)
1|parse    |     at processIncomingData (/home/pepe/parse/node_modules/parse-server/node_modules/mongodb/lib/cmap/message_stream.js:132:20)
1|parse    |     at MessageStream._write (/home/pepe/parse/node_modules/parse-server/node_modules/mongodb/lib/cmap/message_stream.js:33:9)
1|parse    |     at writeOrBuffer (node:internal/streams/writable:391:12)
1|parse    |     at _write (node:internal/streams/writable:332:10)
1|parse    |     at MessageStream.Writable.write (node:internal/streams/writable:336:10)
1|parse    |     at Socket.ondata (node:internal/streams/readable:754:22)
1|parse    |     at Socket.emit (node:events:513:28) {
1|parse    |   ok: 0,
1|parse    |   code: 13,
1|parse    |   codeName: 'Unauthorized', # <----------
1|parse    |   [Symbol(errorLabels)]: Set(0) {}
1|parse    | }
```

En ningún momento hemos creado una varibale de entorno para configurar. [Aquí](https://pm2.keymetrics.io/docs/usage/application-declaration/) te explica como hacerlo 

```sh
pepe@ip-172-31-39-104:~$ nano ecosystem.config.js

# añadiendo la variable de entorno
module.exports = {
  apps : [
 {
    name   : "chat",
    cwd    : "/home/pepe/node-chat",
    script : "app.js"
  },
  {
    name   : "parse",
    cwd    : "/home/pepe/parse",
    script : "index.js",
    env    : {"DATABASE_URI": "mongodb://axempleparse:axempleparse@127.0.0.1:27017/parsedb"}
  }
 ]
}
```

```sh
pepe@ip-172-31-39-104:~$ pm2 start ecosystem.config.js 
[PM2] Applying action restartProcessId on app [chat](ids: [ 0 ])
[PM2] Applying action restartProcessId on app [parse](ids: [ 1 ])
[PM2] [chat](0) ✓
[PM2] [parse](1) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ chat               │ fork     │ 7    │ online    │ 0%       │ 20.8mb   │
│ 1  │ parse              │ fork     │ 3    │ online    │ 0%       │ 16.0mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
```

![](/img/46.png)

Sigue sin funcionar 

```sh
pepe@ip-172-31-39-104:~$ pm2 logs parse


/home/pepe/.pm2/logs/parse-error.log last 15 lines:
1|parse    | 
1|parse    |     at Module.Hook._require.Module.require (/home/pepe/.nvm/versions/node/v16.20.2/lib/node_modules/pm2/node_modules/require-in-the-middle/index.js:101:39)
1|parse    |     at ParseServer.start (/home/pepe/parse/node_modules/parse-server/lib/ParseServer.js:144:13)
1|parse    |     at async file:///home/pepe/parse/index.js:34:3 {
1|parse    |   code: 'ERR_REQUIRE_ESM'
1|parse    | }
1|parse    | Error [ERR_REQUIRE_ESM]: require() of ES Module /home/pepe/parse/cloud/main.js from /home/pepe/parse/node_modules/parse-server/lib/ParseServer.js not supported.
1|parse    | main.js is treated as an ES module file as it is a .js file whose nearest parent package.json contains "type": "module" which declares all .js files in that package scope as ES modules.
1|parse    | Instead rename main.js to end in .cjs, change the requiring code to use dynamic import() which is available in all CommonJS modules, or change "type": "module" to "type": "commonjs" in /home/pepe/parse/package.json to treat all .js files as CommonJS (using .mjs for all ES modules instead).
1|parse    | 
1|parse    |     at Module.Hook._require.Module.require (/home/pepe/.nvm/versions/node/v16.20.2/lib/node_modules/pm2/node_modules/require-in-the-middle/index.js:101:39)
1|parse    |     at ParseServer.start (/home/pepe/parse/node_modules/parse-server/lib/ParseServer.js:144:13)
1|parse    |     at async file:///home/pepe/parse/index.js:34:3 {
1|parse    |   code: 'ERR_REQUIRE_ESM'
1|parse    | }
```

Estamos usando versión `node/v16.20.2` pero mi app necesita node 18

```sh
pepe@ip-172-31-39-104:~$ node --version
v16.20.2
```

El chat necesitava node 16, Parse necesita node 18. Podemos decirle a `pm2` con este comando :

`interpreter	(string)	“/usr/bin/python”	interpreter absolute path (default to node)`

Le podremos decir que cada uno lo haga por cada node

**Buscando donde está node 18**

```sh
# le digo que ejecute la 18
pepe@ip-172-31-39-104:~$ nvm use 18
Now using node v18.19.0 (npm v10.2.3)

# le pido la path
pepe@ip-172-31-39-104:~$ which node
/home/pepe/.nvm/versions/node/v18.19.0/bin/node
```

Imagínate que no has activado la 18

```sh
pepe@ip-172-31-39-104:~$ logout
ubuntu@ip-172-31-39-104:~$ sudo -u pepe -i
pepe@ip-172-31-39-104:~$ node --version
v16.20.2
```

¿como adivinas la path de node 18?

```sh
pepe@ip-172-31-39-104:~$ nvm which 18
/home/pepe/.nvm/versions/node/v18.19.0/bin/node

pepe@ip-172-31-39-104:~$ node --version
v16.20.2
```

copio `/home/pepe/.nvm/versions/node/v18.19.0/bin/node`

```sh
pepe@ip-172-31-39-104:~$ nano ecosystem.config.js


module.exports = {
  apps : [
 {
    name   : "chat",
    cwd    : "/home/pepe/node-chat",
    script : "app.js"
  },
  {
    name   : "parse",
    cwd    : "/home/pepe/parse",
    script : "index.js",
    interpreter: "/home/pepe/.nvm/versions/node/v18.19.0/bin/node",
    env    : {"DATABASE_URI": "mongodb://axempleparse:axempleparse@127.0.0.1:27017/parsedb"} 
  }
 ]
}
```

![](/img/46.png)

Sigue sin funcionar . Nos hemos aquivocado, teníamos que haber instalado `pm2` en la última versión de node.

```sh
pepe@ip-172-31-39-104:~$ pm2 logs parse


/home/pepe/.pm2/logs/parse-error.log last 15 lines:
1|parse    | 
1|parse    |     at Hook._require.Module.require (/home/pepe/.nvm/versions/node/v16.20.2/lib/node_modules/pm2/node_modules/require-in-the-middle/index.js:101:39)
1|parse    |     at ParseServer.start (/home/pepe/parse/node_modules/parse-server/lib/ParseServer.js:144:13)
1|parse    |     at async file:///home/pepe/parse/index.js:34:3 {
1|parse    |   code: 'ERR_REQUIRE_ESM'
1|parse    | }
1|parse    | Error [ERR_REQUIRE_ESM]: require() of ES Module /home/pepe/parse/cloud/main.js from /home/pepe/parse/node_modules/parse-server/lib/ParseServer.js not supported.
1|parse    | main.js is treated as an ES module file as it is a .js file whose nearest parent package.json contains "type": "module" which declares all .js files in that package scope as ES modules.
1|parse    | Instead either rename main.js to end in .cjs, change the requiring code to use dynamic import() which is available in all CommonJS modules, or change "type": "module" to "type": "commonjs" in /home/pepe/parse/package.json to treat all .js files as CommonJS (using .mjs for all ES modules instead).
1|parse    | 
1|parse    |     at Hook._require.Module.require (/home/pepe/.nvm/versions/node/v16.20.2/lib/node_modules/pm2/node_modules/require-in-the-middle/index.js:101:39)
1|parse    |     at ParseServer.start (/home/pepe/parse/node_modules/parse-server/lib/ParseServer.js:144:13)
1|parse    |     at async file:///home/pepe/parse/index.js:34:3 {
1|parse    |   code: 'ERR_REQUIRE_ESM'
1|parse    | }
```

`1|parse    | Error [ERR_REQUIRE_ESM]: require() of ES Module /home/pepe/parse/cloud/main.js from /home/pepe/parse/node_modules/parse-server/lib/ParseServer.js not supported.`

Hemos de arrancar pm2 con node 18

**Ojo reconfiguramos pm2 con node 21**
```sh
# instalndo la ultima version de node
pepe@ip-172-31-39-104:~$ nvm install node
Downloading and installing node v21.6.1...
Downloading https://nodejs.org/dist/v21.6.1/node-v21.6.1-linux-x64.tar.xz...
#########################################################################  100.0%
Computing checksum with sha256sum
Checksums matched!
Now using node v21.6.1 (npm v10.2.4)

# la version por defecto siempre la 21
pepe@ip-172-31-39-104:~$ nvm alias default 21
default -> 21 (-> v21.6.1)

# instalando globa pm2
pepe@ip-172-31-39-104:~$ npm i -g pm2
npm WARN deprecated uuid@3.4.0: Please upgrade  to version 7 or higher.  Older versions may use Math.random() in certain circumstances, which is known to be problematic.  See https://v8.dev/blog/math-random for details.

added 162 packages in 8s

13 packages are looking for funding
  run `npm fund` for details


# mirando el sistema para ejecutar has de copiarlo
pepe@ip-172-31-39-104:~$ pm2 startup
        [PM2] Init System found: systemd
        [PM2] To setup the Startup Script, copy/paste the following command:
        sudo env PATH=$PATH:/home/pepe/.nvm/versions/node/v21.6.1/bin /home/pepe/.nvm/versions/node/v21.6.1/lib/node_modules/pm2/bin/pm2 startup systemd -u pepe --hp /home/pepe
```

```sh
pepe@ip-172-31-39-104:~$ logout

ubuntu@ip-172-31-39-104:~$ sudo env PATH=$PATH:/home/pepe/.nvm/versions/node/v21.6.1/bin /home/pepe/.nvm/versions/node/v21.6.1/lib/node_modules/pm2/bin/pm2 startup systemd -u pepe --hp /home/pepe
```

```sh
# recargo el servidor
ubuntu@ip-172-31-39-104:~$ sudo reboot

# me conecto
➜  react-redux-todo-app git:(master) ✗ ssh -i ../Despliegue_AWS/web15.pem ubuntu@54.224.151.83
        Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 6.2.0-1018-aws x86_64)


ubuntu@ip-172-31-39-104:~$ sudo systemctl status pm2-pepe.service

● pm2-pepe.service - PM2 process manager
     Loaded: loaded (/etc/systemd/system/pm2-pepe.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2024-02-13 20:57:37 UTC; 2min 20s ago
       Docs: https://pm2.keymetrics.io/
    Process: 364 ExecStart=/home/pepe/.nvm/versions/node/v21.6.1/lib/node_modules/pm2/bin/pm2 resurrect (code=exited, status=0/SUC>
   Main PID: 576 (PM2 v5.3.1: God)
      Tasks: 26 (limit: 1121)
     Memory: 128.6M
        CPU: 1.910s
     CGroup: /system.slice/pm2-pepe.service
             ├─576 "PM2 v5.3.1: God Daemon (/home/pepe/.pm2)" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "">
             └─679 "node /home/pepe/node-chat/app.js" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" ">

Feb 13 20:57:36 ip-172-31-39-104 pm2[364]: [PM2] PM2 Successfully daemonized
Feb 13 20:57:36 ip-172-31-39-104 pm2[364]: [PM2] Resurrecting
Feb 13 20:57:36 ip-172-31-39-104 pm2[364]: [PM2] Restoring processes located in /home/pepe/.pm2/dump.pm2
Feb 13 20:57:37 ip-172-31-39-104 pm2[364]: [PM2] Process /home/pepe/node-chat/app.js restored
Feb 13 20:57:37 ip-172-31-39-104 pm2[364]: ┌────┬────────┬─────────────┬─────────┬─────────┬──────────┬────────┬──────┬───────────>
Feb 13 20:57:37 ip-172-31-39-104 pm2[364]: │ id │ name   │ namespace   │ version │ mode    │ pid      │ uptime │ ↺    │ status    >
Feb 13 20:57:37 ip-172-31-39-104 pm2[364]: ├────┼────────┼─────────────┼─────────┼─────────┼──────────┼────────┼──────┼───────────>
Feb 13 20:57:37 ip-172-31-39-104 pm2[364]: │ 0  │ app    │ default     │ 1.0.7   │ fork    │ 679      │ 0s     │ 0    │ online    >
Feb 13 20:57:37 ip-172-31-39-104 pm2[364]: └────┴────────┴─────────────┴─────────┴─────────┴──────────┴────────┴──────┴───────────>
Feb 13 20:57:37 ip-172-31-39-104 systemd[1]: Started PM2 process manager.
lines 1-23/23 (END)
```


```sh
ubuntu@ip-172-31-39-104:~$ sudo -u pepe -i

pepe@ip-172-31-39-104:~$ node --version
v21.6.1

pepe@ip-172-31-39-104:~$ pm2 start ecosystem.config.js 
[PM2][WARN] Applications chat, parse not running, starting...
[PM2] App [chat] launched (1 instances)
[PM2] App [parse] launched (1 instances)
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ app                │ fork     │ 0    │ online    │ 0%       │ 50.2mb   │
│ 1  │ chat               │ fork     │ 0    │ online    │ 0%       │ 25.9mb   │
│ 2  │ parse              │ fork     │ 0    │ online    │ 0%       │ 256.0kb  │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. Type 'pm2 save' to synchronize.
pepe@ip-172-31-39-104:~$ pm2 delete app
[PM2] Applying action deleteProcessId on app [app](ids: [ 0 ])
[PM2] [app](0) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 1  │ chat               │ fork     │ 16   │ errored   │ 0%       │ 0b       │
│ 2  │ parse              │ fork     │ 0    │ online    │ 0%       │ 119.9mb  │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.

```

![](/img/46.png)

Sigue sin funcionar 

```sh
pepe@ip-172-31-39-104:~$ pm2 log parse


/home/pepe/.pm2/logs/parse-error.log last 15 lines:
2|parse    |     type: 'Unknown',
2|parse    |     servers: Map(1) { '127.0.0.1:27017' => [ServerDescription] },
2|parse    |     stale: false,
2|parse    |     compatible: true,
2|parse    |     heartbeatFrequencyMS: 10000,
2|parse    |     localThresholdMS: 15,
2|parse    |     setName: null,
2|parse    |     maxElectionId: null,
2|parse    |     maxSetVersion: null,
2|parse    |     commonWireVersion: 0,
2|parse    |     logicalSessionTimeoutMinutes: null
2|parse    |   },
2|parse    |   code: undefined,
2|parse    |   [Symbol(errorLabels)]: Set(0) {}
2|parse    | }

2|parse  | MongoServerSelectionError: connect ECONNREFUSED 127.0.0.1:27017
2|parse  |     at Timeout._onTimeout (/home/pepe/parse/node_modules/parse-server/node_modules/mongodb/lib/sdam/topology.js:291:38)
2|parse  |     at listOnTimeout (node:internal/timers:569:17)
2|parse  |     at process.processTimers (node:internal/timers:512:7) {
2|parse  |   reason: TopologyDescription {
2|parse  |     type: 'Unknown',
2|parse  |     servers: Map(1) { '127.0.0.1:27017' => [ServerDescription] },
2|parse  |     stale: false,
2|parse  |     compatible: true,
2|parse  |     heartbeatFrequencyMS: 10000,
2|parse  |     localThresholdMS: 15,
2|parse  |     setName: null,
2|parse  |     maxElectionId: null,
2|parse  |     maxSetVersion: null,
2|parse  |     commonWireVersion: 0,
2|parse  |     logicalSessionTimeoutMinutes: null
2|parse  |   },
2|parse  |   code: undefined,
2|parse  |   [Symbol(errorLabels)]: Set(0) {}
2|parse  | }
2|parse  | MongoServerSelectionError: connect ECONNREFUSED 127.0.0.1:27017
2|parse  |     at Timeout._onTimeout (/home/pepe/parse/node_modules/parse-server/node_modules/mongodb/lib/sdam/topology.js:291:38)
2|parse  |     at listOnTimeout (node:internal/timers:569:17)
2|parse  |     at process.processTimers (node:internal/timers:512:7) {
2|parse  |   reason: TopologyDescription {
2|parse  |     type: 'Unknown',
2|parse  |     servers: Map(1) { '127.0.0.1:27017' => [ServerDescription] },
2|parse  |     stale: false,
2|parse  |     compatible: true,
2|parse  |     heartbeatFrequencyMS: 10000,
2|parse  |     localThresholdMS: 15,
2|parse  |     setName: null,
2|parse  |     maxElectionId: null,
2|parse  |     maxSetVersion: null,
2|parse  |     commonWireVersion: 0,
2|parse  |     logicalSessionTimeoutMinutes: null
2|parse  |   },
2|parse  |   code: undefined,
2|parse  |   [Symbol(errorLabels)]: Set(0) {}
2|parse  | }
```

```sh
# mogo inactivo
pepe@ip-172-31-39-104:~$ systemctl status mongod.service

○ mongod.service - MongoDB Database Server
     Loaded: loaded (/lib/systemd/system/mongod.service; disabled; vendor preset: enabled)
     Active: inactive (dead)
       Docs: https://docs.mongodb.org/manual
```

Cuando instaas u servicio si ne¡o se arranca automaticamente es que no se arranca nunca automaticamente. Mongo por defecto no se inicia.

En el manual de mongo te lo explica.

```sh
# al realizar un servicio, queda registrado, le dices que mongo ha de arrancar con el sistema operativo
ubuntu@ip-172-31-39-104:~$ sudo systemctl enable mongod

Created symlink /etc/systemd/system/multi-user.target.wants/mongod.service → /lib/systemd/system/mongod.service.
```


```sh
ubuntu@ip-172-31-39-104:~$ sudo systemctl start mongod # arrancamos
ubuntu@ip-172-31-39-104:~$ sudo systemctl status mongod
● mongod.service - MongoDB Database Server
     Loaded: loaded (/lib/systemd/system/mongod.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2024-02-13 21:08:20 UTC; 6s ago
       Docs: https://docs.mongodb.org/manual
   Main PID: 1572 (mongod)
     Memory: 227.1M
        CPU: 1.300s
     CGroup: /system.slice/mongod.service
             └─1572 /usr/bin/mongod --config /etc/mongod.conf

Feb 13 21:08:20 ip-172-31-39-104 systemd[1]: Started MongoDB Database Server.
Feb 13 21:08:21 ip-172-31-39-104 mongod[1572]: {"t":{"$date":"2024-02-13T21:08:21.595Z"},"s":"I",  "c":"CONTROL",  "id":7484500, ">
lines 1-12/12 (END)
```



```sh
ubuntu@ip-172-31-39-104:~$ sudo -u pepe -i
pepe@ip-172-31-39-104:~$ pm2 list
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 1  │ chat               │ fork     │ 16   │ errored   │ 0%       │ 0b       │
│ 2  │ parse              │ fork     │ 12   │ online    │ 0%       │ 114.3mb  │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
pepe@ip-172-31-39-104:~$ pm2 restart parse
Use --update-env to update environment variables
[PM2] Applying action restartProcessId on app [parse](ids: [ 2 ])
[PM2] [parse](2) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 1  │ chat               │ fork     │ 16   │ errored   │ 0%       │ 0b       │
│ 2  │ parse              │ fork     │ 13   │ online    │ 0%       │ 15.6mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
pepe@ip-172-31-39-104:~$ pm2 restart chat
Use --update-env to update environment variables
[PM2] Applying action restartProcessId on app [chat](ids: [ 1 ])
[PM2] [chat](1) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 1  │ chat               │ fork     │ 16   │ online    │ 0%       │ 19.6mb   │
│ 2  │ parse              │ fork     │ 13   │ online    │ 0%       │ 114.7mb  │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
```

![](/img/46.png)

Sigue sin funcionar 


```sh
/home/pepe/.pm2/logs/parse-error.log last 15 lines:
2|parse    | 
2|parse    |     at Hook._require.Module.require (/home/pepe/.nvm/versions/node/v21.6.1/lib/node_modules/pm2/node_modules/require-in-the-middle/index.js:101:39)
2|parse    |     at ParseServer.start (/home/pepe/parse/node_modules/parse-server/lib/ParseServer.js:144:13)
2|parse    |     at async file:///home/pepe/parse/index.js:34:3 {
2|parse    |   code: 'ERR_REQUIRE_ESM'
2|parse    | }
2|parse    | Error [ERR_REQUIRE_ESM]: require() of ES Module /home/pepe/parse/cloud/main.js from /home/pepe/parse/node_modules/parse-server/lib/ParseServer.js not supported.
2|parse    | main.js is treated as an ES module file as it is a .js file whose nearest parent package.json contains "type": "module" which declares all .js files in that package scope as ES modules.
2|parse    | Instead either rename main.js to end in .cjs, change the requiring code to use dynamic import() which is available in all CommonJS modules, or change "type": "module" to "type": "commonjs" in /home/pepe/parse/package.json to treat all .js files as CommonJS (using .mjs for all ES modules instead).
2|parse    | 
2|parse    |     at Hook._require.Module.require (/home/pepe/.nvm/versions/node/v21.6.1/lib/node_modules/pm2/node_modules/require-in-the-middle/index.js:101:39)
2|parse    |     at ParseServer.start (/home/pepe/parse/node_modules/parse-server/lib/ParseServer.js:144:13)
2|parse    |     at async file:///home/pepe/parse/index.js:34:3 {
2|parse    |   code: 'ERR_REQUIRE_ESM'
2|parse    | }
```

---
> [!IMPORTANT]
> cambiamos todo. Vamos a usar `supervisor` en vez de `pm2`. Lo tienes en los slides
---

```sh
pepe@ip-172-31-39-104:~$ pm2 stop all
[PM2] Applying action stopProcessId on app [all](ids: [ 1, 2 ])
[PM2] [chat](1) ✓
[PM2] [parse](2) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 1  │ chat               │ fork     │ 16   │ stopped   │ 0%       │ 0b       │
│ 2  │ parse              │ fork     │ 13   │ stopped   │ 0%       │ 0b       │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
pepe@ip-172-31-39-104:~$ pm2 delete all
[PM2] Applying action deleteProcessId on app [all](ids: [ 1, 2 ])
[PM2] [chat](1) ✓
[PM2] [parse](2) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
pepe@ip-172-31-39-104:~$ 
```

```sh
pepe@ip-172-31-39-104:~$ logout
ubuntu@ip-172-31-39-104:~$ suno apt install supervisor
        Command 'suno' not found, did you mean:
        command 'sudo' from deb sudo (1.9.9-1ubuntu2.4)
        command 'sudo' from deb sudo-ldap (1.9.9-1ubuntu2.4)
        command 'sumo' from deb sumo (1.12.0+dfsg1-1)
        Try: sudo apt install <deb name>
ubuntu@ip-172-31-39-104:~$ sudo apt install supervisor
        Reading package lists... Done
        Building dependency tree... Done
        Reading state information... Done
        Suggested packages:
        supervisor-doc
        The following NEW packages will be installed:
        supervisor
        0 upgraded, 1 newly installed, 0 to remove and 31 not upgraded.
        Need to get 278 kB of archives.
        After this operation, 1684 kB of additional disk space will be used.
        Get:1 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/universe amd64 supervisor all 4.2.1-1ubuntu1 [278 kB]
        Fetched 278 kB in 0s (9265 kB/s)
        Selecting previously unselected package supervisor.
        (Reading database ... 94865 files and directories currently installed.)
        Preparing to unpack .../supervisor_4.2.1-1ubuntu1_all.deb ...
        Unpacking supervisor (4.2.1-1ubuntu1) ...
        Setting up supervisor (4.2.1-1ubuntu1) ...
        Created symlink /etc/systemd/system/multi-user.target.wants/supervisor.service → /lib/systemd/system/supervisor.service.
        Processing triggers for man-db (2.10.2-1) ...
        Scanning processes...                                                                                                              
        Scanning linux images...                                                                                                           

        Running kernel seems to be up-to-date.

        No services need to be restarted.

        No containers need to be restarted.

        No user sessions are running outdated binaries.

        No VM guests are running outdated hypervisor (qemu) binaries on this host.

```

```sh
ubuntu@ip-172-31-39-104:~$ sudo systemctl status supervisor
● supervisor.service - Supervisor process control system for UNIX
     Loaded: loaded (/lib/systemd/system/supervisor.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2024-02-13 21:21:46 UTC; 1min 5s ago
       Docs: http://supervisord.org
   Main PID: 2145 (supervisord)
      Tasks: 1 (limit: 1121)
     Memory: 19.3M
        CPU: 242ms
     CGroup: /system.slice/supervisor.service
             └─2145 /usr/bin/python3 /usr/bin/supervisord -n -c /etc/supervisor/supervisord.conf

Feb 13 21:21:46 ip-172-31-39-104 systemd[1]: Started Supervisor process control system for UNIX.
Feb 13 21:21:47 ip-172-31-39-104 supervisord[2145]: 2024-02-13 21:21:47,340 CRIT Supervisor is running as root.  Privileges were n>
Feb 13 21:21:47 ip-172-31-39-104 supervisord[2145]: 2024-02-13 21:21:47,341 WARN No file matches via include "/etc/supervisor/conf>
Feb 13 21:21:47 ip-172-31-39-104 supervisord[2145]: 2024-02-13 21:21:47,345 INFO RPC interface 'supervisor' initialized
Feb 13 21:21:47 ip-172-31-39-104 supervisord[2145]: 2024-02-13 21:21:47,345 CRIT Server 'unix_http_server' running without any HTT>
Feb 13 21:21:47 ip-172-31-39-104 supervisord[2145]: 2024-02-13 21:21:47,345 INFO supervisord started with pid 2145
lines 1-17/17 (END)
```

¿como configuramos? cada aplicacion la hemos de crear en ` "/etc/supervisor/conf>`

```sh
ubuntu@ip-172-31-39-104:~$ cd /etc/supervisor/conf.d/
```

```sh
# notas propias que tienes en los slides de node
[program:app_name] # comando con el nombre de la app
command=/path/to/node/version index.js  # ruta apsoluta de la pp
user=node # usarui
directory=/path/to/source/code/folder #  donde queremos que se ejecute la app
autostart=true # para que se inicie automaticamente
autorestart=true # para que se reinicie automaticamente

# todo esto para donde queresmoq eu estenlos archivos de logs
stdout_logfile=/var/log/start.out.log  
stdout_logfile_maxbytes=10MB 
stdout_logfile_backups=3 
stderr_logfile=/var/log/start.err.log 
stderr_logfile_maxbytes=10MB 
stdout_logfile_backups=3 

environment=KEY="val",KEY2="val2"     # definir variables de entonro
```

> [!NOTE]
> Comenzamos

```sh
ubuntu@ip-172-31-39-104:~$ cd /etc/supervisor/conf.d/
ubuntu@ip-172-31-39-104:/etc/supervisor/conf.d$ sudo nano parse.conf

#### NANO ####
[program:parse]
user=pepe
command=RUTA_NODE index.js
directory=/home/pepe/parse
autostart=true 
autorestart=true 
environment=DATABASE_URI="mongodb://axempleparse:axempleparse@127.0.0.1:27017/parsedb"
```


```sh
# buscando la ruta de node
ubuntu@ip-172-31-39-104:/etc/supervisor/conf.d$ sudo nano parse.conf
ubuntu@ip-172-31-39-104:/etc/supervisor/conf.d$ sudo -u pepe -i
pepe@ip-172-31-39-104:~$ nvm which 18
/home/pepe/.nvm/versions/node/v18.19.0/bin/node
```

```sh
# cambiando ruta a nano
pepe@ip-172-31-39-104:/etc/supervisor/conf.d$ logout
ubuntu@ip-172-31-39-104:/etc/supervisor/conf.d$ sudo nano parse.conf

#### NANO ####
[program:parse]
user=pepe
command=/home/pepe/.nvm/versions/node/v18.19.0/bin/node index.js
directory=/home/pepe/parse
autostart=true 
autorestart=true
environment=DATABASE_URI="mongodb://axempleparse:axempleparse@127.0.0.1:27017/parsedb"
```

```sh
ubuntu@ip-172-31-39-104:/etc/supervisor/conf.d$ sudo systemctl restart supervisor
ubuntu@ip-172-31-39-104:/etc/supervisor/conf.d$ sudo systemctl status supervisor
● supervisor.service - Supervisor process control system for UNIX
     Loaded: loaded (/lib/systemd/system/supervisor.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2024-02-14 08:13:23 UTC; 47s ago
       Docs: http://supervisord.org
   Main PID: 3082 (supervisord)
      Tasks: 1 (limit: 1121)
     Memory: 45.8M
        CPU: 24.038s
     CGroup: /system.slice/supervisor.service
             └─3082 /usr/bin/python3 /usr/bin/supervisord -n -c /etc/supervisor/supervisord.conf

Feb 14 08:13:57 ip-172-31-39-104 supervisord[3082]: 2024-02-14 08:13:57,275 INFO exited: parse (exit status 1; not expected)
Feb 14 08:13:58 ip-172-31-39-104 supervisord[3082]: 2024-02-14 08:13:58,278 INFO spawned: 'parse' with pid 3191
Feb 14 08:13:59 ip-172-31-39-104 supervisord[3082]: 2024-02-14 08:13:59,280 INFO success: parse entered RUNNING state, process has>
Feb 14 08:14:01 ip-172-31-39-104 supervisord[3082]: 2024-02-14 08:14:01,691 INFO exited: parse (exit status 1; not expected)
Feb 14 08:14:02 ip-172-31-39-104 supervisord[3082]: 2024-02-14 08:14:02,694 INFO spawned: 'parse' with pid 3206
Feb 14 08:14:03 ip-172-31-39-104 supervisord[3082]: 2024-02-14 08:14:03,696 INFO success: parse entered RUNNING state, process has>
Feb 14 08:14:06 ip-172-31-39-104 supervisord[3082]: 2024-02-14 08:14:06,071 INFO exited: parse (exit status 1; not expected)
Feb 14 08:14:07 ip-172-31-39-104 supervisord[3082]: 2024-02-14 08:14:07,075 INFO spawned: 'parse' with pid 3221
Feb 14 08:14:08 ip-172-31-39-104 supervisord[3082]: 2024-02-14 08:14:08,076 INFO success: parse entered RUNNING state, process has>
Feb 14 08:14:10 ip-172-31-39-104 supervisord[3082]: 2024-02-14 08:14:10,401 INFO exited: parse (exit status 1; not expected)
lines 1-21/21 (END)
```

Arranca pero no funciona

![](/img/46.png)

Sigue sin funcionar , voy a mirar los logs

```sh
# fíjate donde están los logs
ubuntu@ip-172-31-39-104:/etc/supervisor/conf.d$ cd /var/log/supervisor/
ubuntu@ip-172-31-39-104:/var/log/supervisor$ ls -l
        total 100
        -rw------- 1 root root 66674 Feb 14 08:16 parse-stderr---supervisor-oazfk6fa.log
        -rw------- 1 root root 14615 Feb 14 08:16 parse-stdout---supervisor-wou1_3de.log
        -rw-r--r-- 1 root root 10560 Feb 14 08:16 supervisord.log
ubuntu@ip-172-31-39-104:/var/log/supervisor$ cat parse-stderr---supervisor-oazfk6fa.log
        cat: parse-stderr---supervisor-oazfk6fa.log: Permission denied
ubuntu@ip-172-31-39-104:/var/log/supervisor$ sudo !!

...
/home/pepe/parse/node_modules/parse-server/lib/ParseServer.js:144
            require(path.resolve(process.cwd(), cloud));
            ^

Error [ERR_REQUIRE_ESM]: require() of ES Module /home/pepe/parse/cloud/main.js from /home/pepe/parse/node_modules/parse-server/lib/ParseServer.js not supported.
main.js is treated as an ES module file as it is a .js file whose nearest parent package.json contains "type": "module" which declares all .js files in that package scope as ES modules.
Instead either rename main.js to end in .cjs, change the requiring code to use dynamic import() which is available in all CommonJS modules, or change "type": "module" to "type": "commonjs" in /home/pepe/parse/package.json to treat all .js files as CommonJS (using .mjs for all ES modules instead).

    at ParseServer.start (/home/pepe/parse/node_modules/parse-server/lib/ParseServer.js:144:13)
    at async file:///home/pepe/parse/index.js:34:3 {
  code: 'ERR_REQUIRE_ESM'
}

Node.js v18.19.0
```

Está dando el iso error de antes. Fíjate que te está diciendo `or change "type": "module" to "type": "commonjs" in /home/pepe/parse/package.json to treat all .js files as CommonJS`

El problmea está en que si yo ejecuto con node.js la app arranca , es cierto que da un error por el tema de mongo 
```sh
# con esto si que arranca
npm start

# pero con node index.js no
node index.js

# estamos de acuerdo que 
pepe@ip-172-31-39-104:~/parse$ cat package.json

        {
        "name": "parse-server-example",
        "version": "1.2.3",
        "description": "An example Parse API server using the parse-server module",
        "repository": {
        "type": "git",
        "url": "https://github.com/ParsePlatform/parse-server-example"
        },
        "license": "MIT",
        "main": "index.js",
        "scripts": {
        "coverage": "TESTING=true nyc jasmine",
        "lint": "eslint --cache ./cloud && eslint --cache index.js && eslint --cache ./spec",
        "lint-fix": "eslint --cache --fix ./cloud && eslint --cache --fix index.js && eslint --cache --fix ./spec",
        "prettier": "prettier --write '{cloud,spec}/{**/*,*}.js' 'index.js'",
        "start": "node index.js",
# estamos de acuerdo que si ejecuto "node index.js" es lo mismo que ""start": "node index.js" del json
```

Pues fíajte que con uno no va y el otro si

![](/img/47.png)

así que la configuración con pm2 para que funcione sería la siguiente (con pm2):

```sh
module.exports = {
  apps : [
    {
      name   : "chat",
      cwd    : "/home/pepe/node-chat",
      script : "npm",
      args   : "start",
      env    : { PATH: "/home/pepe/.nvm/versions/node/v16.20.2/bin:/usr/bin" }
   },
    {
      name   : "parse",
      cwd    : "/home/pepe/parse",
      script : "npm",
      args   : "start",
      env    : {
        PATH: "/home/pepe/.nvm/versions/node/v18.19.0/bin:/usr/bin",
        DATABASE_URI: "mongodb://axempleparse:axempleparse@127.0.0.1:27017/parsedb"
      }
    }
  ]
}
```

 Al especificar `"script": "npm"` y `"args": "start"`, le estás diciendo a PM2 que ejecute el comando npm start para iniciar tu aplicación. 

con `supervisor` sería:

```sh
[program:parse]
user=pepe
command=npm start
directory=/home/pepe/parse
autostart=true
autorestart=true
environment=DATABASE_URI="mongodb://axempleparse:axempleparse@127.0.0.1:27017/parsedb",PATH="/home/apps/.nvm/versions/node/v18.19.0/bin:/usr/bin"

[program:chat]
user=pepe
command=npm start
directory=/home/pepe/node-chat
autostart=true
autorestart=true
environment=PATH="/home/pepe/.nvm/versions/node/v16.20.2/bin:/usr/bin"
```

peeeeeeeeeeeeeeeeeeeeero con supervisor no hace bien el stop de las apps cuando arrancan por NPM, así que usemos PM2.


**Desinstalar Supervisor**

```sh
ubuntu@ip-172-31-39-104:~$ sudo apt purge supervisor
        Reading package lists... Done
        Building dependency tree... Done
        Reading state information... Done
        The following packages will be REMOVED:
        supervisor*
        0 upgraded, 0 newly installed, 1 to remove and 36 not upgraded.
        After this operation, 1684 kB disk space will be freed.
        Do you want to continue? [Y/n] Y
        (Reading database ... 95001 files and directories currently installed.)
        Removing supervisor (4.2.1-1ubuntu1) ...
        Processing triggers for man-db (2.10.2-1) ...
        (Reading database ... 94870 files and directories currently installed.)
        Purging configuration files for supervisor (4.2.1-1ubuntu1) ...
        dpkg: warning: while removing supervisor, directory '/var/log/supervisor' not empty so not removed
        dpkg: warning: while removing supervisor, directory '/etc/supervisor/conf.d' not empty so not removed
```

```sh
ubuntu@ip-172-31-39-104:~$ sudo -u pepe -i
pepe@ip-172-31-39-104:~$ cat ecosystem.config.js 
module.exports = {
  apps : [
    {
      name   : "chat",
      cwd    : "/home/pepe/node-chat",
      script : "npm",
      args   : "start",
      env    : { PATH: "/home/pepe/.nvm/versions/node/v16.20.2/bin:/usr/bin" }
   },
    {
      name   : "parse",
      cwd    : "/home/pepe/parse",
      script : "npm",
      args   : "start",
      env    : {
        PATH: "/home/pepe/.nvm/versions/node/v18.19.0/bin:/usr/bin",
        DATABASE_URI: "mongodb://axempleparse:axempleparse@127.0.0.1:27017/parsedb"
      }
    }
  ]
}
pepe@ip-172-31-39-104:~$ mv ecosystem.config.js ecosystem.config.js.backup 
```

```sh
pepe@ip-172-31-39-104:~$ pm2 list
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ chat               │ fork     │ 0    │ online    │ 0%       │ 32.0mb   │
│ 1  │ parse              │ fork     │ 39   │ online    │ 0%       │ 72.5mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
pepe@ip-172-31-39-104:~$ pm2 stop all
p[PM2] Applying action stopProcessId on app [all](ids: [ 0, 1 ])
m2[PM2] [chat](0) ✓
 dele[PM2] [parse](1) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ chat               │ fork     │ 0    │ stopped   │ 0%       │ 0b       │
│ 1  │ parse              │ fork     │ 39   │ stopped   │ 0%       │ 0b       │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
tpepe@ip-172-31-39-104:~$ pm2 delete all
[PM2] Applying action deleteProcessId on app [all](ids: [ 0, 1 ])
[PM2] [chat](0) ✓
[PM2] [parse](1) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
```


**?Qué ocurre cuando tenemos ngonx funcionando como proxi inverso y la app que está detrás no está en pie?**

Ngins intenta trabajaro con al app que hay detrás pero la app no está funcionando

![](/img/48.png)

---
**CARGANDO EL CHAT**
---

```sh
ubuntu@ip-172-31-39-104:~$ sudo -u pepe -i
pepe@ip-172-31-39-104:~$ cd node-chat/
pepe@ip-172-31-39-104:~/node-chat$ node --version
        v21.6.1
pepe@ip-172-31-39-104:~/node-chat$ nvm use 16 # Parse necesita la version 16
        Now using node v16.20.2 (npm v8.19.4)
pepe@ip-172-31-39-104:~/node-chat$ npm start

        > node-chat@1.0.7 start
        > node app.js

        [--:--:--][CONSOLE] [10:33:01] [Start] Listening at port 3000 # <--- escuchando en el uerto 3000
        (node:88389) [DEP0066] DeprecationWarning: OutgoingMessage.prototype._headers is deprecated
        (Use `node --trace-deprecation ...` to show where the warning was created)
```

Ahora la app del chat funciona correctamente en http://54.224.151.83/

**Ahora vamos a desplegar el chat usando el comando `npm start`**

Voy a user node 21 que es donde está instalado `pm2`

```sh
pepe@ip-172-31-39-104:~$ nvm use default # pm2 trabaja se ha creado con node 21
        Now using node v21.6.1 (npm v10.2.4)
```

Generamos el esqueleto de ecosytem

```sh
pepe@ip-172-31-39-104:~$ pm2 init simple
        File /home/pepe/ecosystem.config.js generated
pepe@ip-172-31-39-104:~$ ls -l
        total 16
        -rw-rw-r--  1 pepe pepe   83 Feb 15 10:43 ecosystem.config.js # <--- hemos generado este nuevo
        -rw-rw-r--  1 pepe pepe  530 Feb 14 20:07 ecosystem.config.js.backup
        drwxrwxr-x  7 pepe pepe 4096 Feb 11 16:12 node-chat
        drwxrwxr-x 11 pepe pepe 4096 Feb 13 16:02 parse
```

Configurando el modulo

```sh
  GNU nano 6.2   ecosystem.config.js *     
                                      
module.exports = {
  apps : [
    {
      name   : "chat",
      cwd    : "/home/pepe/node-chat", # directorio de trabajo
      script : "npm", # ¿qué comando quiero ejecutar en node-chat?
      args   : "start", # con qué argumento? npm start
   }
```

Arrancamos pm2 con node-chat

```sh
pepe@ip-172-31-39-104:~$ pm2 start ecosystem.config.js
[PM2][WARN] Applications chat not running, starting...
[PM2] App [chat] launched (1 instances)
┌────┬─────────┬─────────────┬─────────┬─────────┬──────────┬────────┬──────┬───────────┬──────────┬──────────┬──────────┬──────────┐
│ id │ name    │ namespace   │ version │ mode    │ pid      │ uptime │ ↺    │ status    │ cpu      │ mem      │ user     │ watching │
├────┼─────────┼─────────────┼─────────┼─────────┼──────────┼────────┼──────┼───────────┼──────────┼──────────┼──────────┼──────────┤
│ 0  │ chat    │ default     │ 0.39.7  │ fork    │ 90036    │ 0s     │ 0    │ online    │ 0%       │ 19.8mb   │ pepe     │ disabled │
└────┴─────────┴─────────────┴─────────┴─────────┴──────────┴────────┴──────┴───────────┴──────────┴──────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
pepe@ip-172-31-39-104:~$ pm2 list
┌────┬─────────┬─────────────┬─────────┬─────────┬──────────┬────────┬──────┬───────────┬──────────┬──────────┬──────────┬──────────┐
│ id │ name    │ namespace   │ version │ mode    │ pid      │ uptime │ ↺    │ status    │ cpu      │ mem      │ user     │ watching │
├────┼─────────┼─────────────┼─────────┼─────────┼──────────┼────────┼──────┼───────────┼──────────┼──────────┼──────────┼──────────┤
│ 0  │ chat    │ default     │ 0.39.7  │ fork    │ 90036    │ 5s     │ 0    │ online    │ 0%       │ 70.4mb   │ pepe     │ disabled │
└────┴─────────┴─────────────┴─────────┴─────────┴──────────┴────────┴──────┴───────────┴──────────┴──────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.
pepe@ip-172-31-39-104:~$ 

```

![](/img/49.png)

---
¿porqué nos da este error? porque está trabajandno con node 21

```sh
pepe@ip-172-31-39-104:~$ pm2 monit # con esto lo puedes ver
```

![](/img/50.png)

Te dice que el script path `Script path           /home/pepe/.nvm/versions/node/v21.6.1/bin/npm   `

¿como lo arreglamos? le hemos de dar más información de contexto.

Lo más importante, cuando tienes una terminal y ejecutas un comando, eso es un programa, todo son programas y han de estar instalados en algún sistio, si tu haces `witch ls` ese programa te dice donde esta localizado ls. Entonces si estás en otro ptah como sabe dobnde ejecutar el programa que tu quieres , y en este caso para ello se llama `PATH`. Cuando te diga programa no encontrado, casi seguro sea esto.


Le voy a configurar variables de entorno, redefiniedno el `path`

```sh
pepe@ip-172-31-39-104:~$ nvm which 16
        /home/pepe/.nvm/versions/node/v16.20.2/bin/node
```

* `/home/pepe/.nvm/versions/node/v16.20.2/bin`: Esta parte del PATH señala al directorio donde están instalados los binarios de Node.js para la versión 16.20.2 gestionada por nvm 
* `/usr/bin`: Es un directorio estándar en Unix donde se almacenan muchos de los ejecutables que vienen con el sistema operativo y otros programas instalados globalmente.

`PATH: "/home/pepe/.nvm/versions/node/v16.20.2/bin:/usr/bin`


```sh
  GNU nano 6.2   ecosystem.config.js *     
                                      
module.exports = {
  apps : [
    {
      name   : "chat",
      cwd    : "/home/pepe/node-chat", # directorio de trabajo
      script : "npm", # ¿qué comando quiero ejecutar en node-chat?
      args   : "start", # con qué argumento? npm start
      env    : { PATH: "/home/pepe/.nvm/versions/node/v16.20.2/bin:/usr/bin" } # le tienes que decir donde buscar la version correcta de node
   }  
 ]
}
```

```sh
pepe@ip-172-31-39-104:~$ pm2 start ecosystem.config.js
[PM2][WARN] Applications chat not running, starting...
[PM2] App [chat] launched (1 instances)
┌────┬─────────┬─────────────┬─────────┬─────────┬──────────┬────────┬──────┬───────────┬──────────┬──────────┬──────────┬──────────┐
│ id │ name    │ namespace   │ version │ mode    │ pid      │ uptime │ ↺    │ status    │ cpu      │ mem      │ user     │ watching │
├────┼─────────┼─────────────┼─────────┼─────────┼──────────┼────────┼──────┼───────────┼──────────┼──────────┼──────────┼──────────┤
│ 0  │ chat    │ default     │ 0.39.7  │ fork    │ 90896    │ 0s     │ 0    │ online    │ 0%       │ 16.0mb   │ pepe     │ disabled │
└────┴─────────┴─────────────┴─────────┴─────────┴──────────┴────────┴──────┴───────────┴──────────┴──────────┴──────────┴──────────┘
[PM2][WARN] Current process list is not synchronized with saved list. App app differs. Type 'pm2 save' to synchronize.

```

Tu chat ya funciona en en http://54.224.151.83/

De hecho si te vas a 

```sh
pepe@ip-172-31-39-104:~$ htop
```

Y aprietas `f5` para extender el arbol de las rutas hechas

![](/img/51.png)

Puedes ver que, de pm2, se ha ido a `npm start` luego `sh -c node app.js` , entonces vemos que lo que no encontraba era el `sh -c` por eso cuando le hemos puesto el `/usr/bin` al path arranca porque puede hacer lo siguiente `sh -c node app.js`

**CARGANDO PARA PASE**
---


```sh
  GNU nano 6.2   ecosystem.config.js *     
                                      
module.exports = {
  apps : [
    {
      name   : "chat",
      cwd    : "/home/pepe/node-chat", # directorio de trabajo
      script : "npm", # ¿qué comando quiero ejecutar en node-chat?
      args   : "start", # con qué argumento? npm start
      env    : { PATH: "/home/pepe/.nvm/versions/node/v16.20.2/bin:/usr/bin" } # le tienes que decir donde buscar la version correcta de node
   },
    {
      name   : "parse",
      cwd    : "/home/pepe/parse",
      script : "npm",
      args   : "start",
      env    : {
        PATH: "/home/pepe/.nvm/versions/node/v18.19.0/bin:/usr/bin",
        DATABASE_URI: "mongodb://axempleparse:axempleparse@127.0.0.1:27017/parsedb"
      }
    }
  ]
}
```


![](/img/52.png)

> [!IMPORTANT]
> Ahora miamo si el ordenador se reinicia las app no se van a levantar.
> Hay que hacer una foto `pm2 save`
> Esto hay que hacerlo siempre quemodifiquemos algún archivo de configuracion

```sh
pepe@ip-172-31-39-104:~$ pm2 save
        [PM2] Saving current process list...
        [PM2] Successfully saved in /home/pepe/.pm2/dump.pm2
```

**Tenemos que poner nginx por delante**

Para que el despliegue del PArse esté perfecto ... falta el puerto `http://54.224.151.83:1337/parse/classes/Cervezas`

Ahora hemos de utilizar `nginx como proxy inverso`

* En las DNS `ec2-54-224-151-83.compute-1.amazonaws.com` estaba funcionando la app de React
* El chat en la ip `http://54.224.151.83`

```sh
pepe@ip-172-31-39-104:~$ cat /etc/nginx/sites-enabled/chat
server {
        listen 80 default; # este responde la llamada.
        location / {       # cuando la peticion comienza por barra (cualquir peticion)
                proxy_pass http://127.0.0.1:3000; # se la pasas a este
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }
}
```

Quiero que entrando por la ip pueda acceder al `chat` pero tambien a `Parse`. 

Todas las peticiones que hagan cominezan por `/parse`

```sh
server {
        listen 80 default; 

         location /parse {       # cuando la peticion comienza por /parse (cualquir peticion)
                proxy_pass http://127.0.0.1:1337; # la reeencia al 1337 con toda la ruta                 
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }

        location / {       # cuando la peticion comienza por barra (cualquir peticion)
                proxy_pass http://127.0.0.1:3000; # se la pasas a este
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }
}
```


```sh
ubuntu@ip-172-31-39-104:~$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
ubuntu@ip-172-31-39-104:~$ sudo systemctl reload nginx
```

Sigue funcionando sin la dns

![](/img/53.png)


* En las DNS `ec2-54-224-151-83.compute-1.amazonaws.com` estaba funcionando la app de React
* El chat en la ip `http://54.224.151.83`
* Siempre que comience por `/parse` ya funciona : `http://54.224.151.83/parse/classes/Cervezas`

---
**Importante** podemos cerrar el puerto 1337 y nos quedamos com

![](/img/54.png)


Ya puedes trabajar sin dns

![](/img/55.png)

---

## archivos estáticos de la aplicación


![](/img/56.png)

---
La `~` le dice que vas a usar una expresion regular.

![](/img/57.png)

Fíjate que tienes archivos servidos con /js | /css | img | etc

Y los sirve express

Dejemos que `nginx` sirva estos archivos que lo hace muy bien


```sh
ubuntu@ip-172-31-39-104:~$ sudo -u pepe -i
pepe@ip-172-31-39-104:~$ cd node-chat/
pepe@ip-172-31-39-104:~/node-chat$ ls -l
        total 92
        -rw-rw-r--  1 pepe pepe  1079 Feb 11 16:06 LICENSE
        -rw-rw-r--  1 pepe pepe  2691 Feb 11 16:06 README.md
        -rw-rw-r--  1 pepe pepe 14805 Feb 11 16:06 app.js
        -rw-rw-r--  1 pepe pepe   234 Feb 11 16:06 config.json
        drwxrwxr-x  2 pepe pepe  4096 Feb 11 16:06 lib
        drwxrwxr-x 58 pepe pepe  4096 Feb 11 16:12 node_modules
        -rw-rw-r--  1 pepe pepe 41017 Feb 11 16:12 package-lock.json
        -rw-rw-r--  1 pepe pepe   347 Feb 11 16:06 package.json
        drwxrwxr-x  7 pepe pepe  4096 Feb 11 16:06 public
        drwxrwxr-x  2 pepe pepe  4096 Feb 11 16:06 views
pepe@ip-172-31-39-104:~/node-chat$ ls -l public/
        total 20
        drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 css
        drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 fonts
        drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 img
        drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 js
        drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 sounds
pepe@ip-172-31-39-104:~/node-chat$ 
```

Ya sabes donde tienes que ir a buscar las cosas, fíjate las carpetas que tiene /public

La instrucción laponemos antes de `location /` porque si no `nginx` la procesa por orden y ya no actuaría


Lo que te pido en la práctica es una cabecera personaliada para demostrar que lo has puesto tu. ¿como? en nginx podemos poner a las cabeceras de las respuestas la instrucción add header , `X-Owner` y a continuación iría el valor, el valor pondría el usuario de `github` : `alexjust-data`


```sh
pepe@ip-172-31-39-104:~/node-chat$ logout
ubuntu@ip-172-31-39-104:~$ sudo nano /etc/nginx/sites-enabled/chat


server {
        listen 80 default; # este responde la llamada.

         location /parse {       # cuando la peticion comienza por /parse (cualquir peticion)
                proxy_pass http://127.0.0.1:1337;
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }

        location ~ ^/(css|img|sounds|fonts|js)/ { 
                root /home/pepe/node-chat/public;
                acces_log off;
                expires max;
                add_header X-Owner AlexJustData
        }

        location / {       # cuando la peticion comienza por barra (cualquir peticion)
                proxy_pass http://127.0.0.1:3000; # se la pasas a este
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }
}
```

```sh
ubuntu@ip-172-31-39-104:~$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
ubuntu@ip-172-31-39-104:~$ sudo systemctl reload nginx
```

![](/img/59.png)


```sh
# vamos a ver en los logs
ubuntu@ip-172-31-39-104:~$ sudo tail nginx /var/log/nginx/error.log


tail: cannot open 'nginx' for reading: No such file or directory
==> /var/log/nginx/error.log <==
==> /var/log/nginx/error.log <==

2024/02/15 17:24:03 [error] 92015#92015: *11816 open() "/home/pepe/node-chat/public/js/chat.js" failed (13: Permission denied), client: 85.87.66.72, server: , request: "GET /js/chat.js HTTP/1.1", host: "54.224.151.83", referrer: "http://54.224.151.83/"
```


El error "Permission denied" (Permiso denegado) indica que Nginx no tiene permiso para acceder al archivo complete.ly.1.0.1.min.js ubicado en /home/pepe/node-chat/public/js/. Esto suele ocurrir por problemas de permisos en el sistema de archivos.

```sh
ubuntu@ip-172-31-39-104:~$ sudo ls /home/pepe/node-chat/public/js/chat.js
/home/pepe/node-chat/public/js/chat.js # la ruta existe 
```

**1ro hemos de ver con qué usuario nginx accede a la ruta**

```sh
ubuntu@ip-172-31-39-104:~$ ps aux | grep nginx
root         432  0.0  0.6  55956  6076 ?        Ss   Feb13   0:00 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
www-data   91490  0.0  0.6  56240  6396 ?        S    16:27   0:00 nginx: worker process is shutting down
www-data   92015  0.0  0.6  56264  6560 ?        S    17:23   0:00 nginx: worker process
ubuntu     92026  0.0  0.2   7008  2304 pts/0    S+   17:29   0:00 grep --color=auto nginx
```

Es `www-data` porque root hace lo que quiere.

```sh
ubuntu@ip-172-31-39-104:~$ ls -l /home/pepe/node-chat/public
ls: cannot access '/home/pepe/node-chat/public': Permission denied
ubuntu@ip-172-31-39-104:~$ sudo !!
sudo ls -l /home/pepe/node-chat/public
total 20
drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 css
drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 fonts
drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 img
drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 js
drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 sounds
```

Podemos ver que hay permisos de ejecución sobre estas carpetas

```sh
ubuntu@ip-172-31-39-104:~$ sudo ls -l /home/pepe/node-chat/public/js/
total 636
-rw-rw-r-- 1 pepe pepe  35452 Feb 11 16:06 bootstrap.min.js
-rw-rw-r-- 1 pepe pepe  24829 Feb 11 16:06 chat.js
-rw-rw-r-- 1 pepe pepe   6038 Feb 11 16:06 complete.ly.1.0.1.min.js
-rw-rw-r-- 1 pepe pepe  84774 Feb 11 16:06 emojione.min.js
-rw-rw-r-- 1 pepe pepe  84320 Feb 11 16:06 jquery-2.1.3.min.js
-rw-rw-r-- 1 pepe pepe 240427 Feb 11 16:06 jquery-ui.min.js
-rw-rw-r-- 1 pepe pepe   5564 Feb 11 16:06 jquery.easing.min.js
-rw-rw-r-- 1 pepe pepe  95785 Feb 11 16:06 jquery.js
-rw-rw-r-- 1 pepe pepe   3599 Feb 11 16:06 jquery.linkify.min.js
-rw-rw-r-- 1 pepe pepe   4094 Feb 11 16:06 material.min.js
-rw-rw-r-- 1 pepe pepe   3939 Feb 11 16:06 material.min.js.map
-rw-rw-r-- 1 pepe pepe   2809 Feb 11 16:06 ripples.min.js
-rw-rw-r-- 1 pepe pepe   3743 Feb 11 16:06 ripples.min.js.map
-rw-rw-r-- 1 pepe pepe  33887 Feb 11 16:06 sockjs-0.3.min.js
```

Todos tiene permiso de lectura para otros usuarios. Los permisos están bien! ¿donde está el problema? más para arriba


```sh
ubuntu@ip-172-31-39-104:~$ sudo ls -l /home/pepe/node-chat/public/
total 20
drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 css
drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 fonts
drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 img
drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 js
drwxrwxr-x 2 pepe pepe 4096 Feb 11 16:06 sounds
```

Hay permisos

```sh
ubuntu@ip-172-31-39-104:~$ sudo ls -l /home/pepe/node-chat/
total 92
-rw-rw-r--  1 pepe pepe  1079 Feb 11 16:06 LICENSE
-rw-rw-r--  1 pepe pepe  2691 Feb 11 16:06 README.md
-rw-rw-r--  1 pepe pepe 14805 Feb 11 16:06 app.js
-rw-rw-r--  1 pepe pepe   234 Feb 11 16:06 config.json
drwxrwxr-x  2 pepe pepe  4096 Feb 11 16:06 lib
drwxrwxr-x 58 pepe pepe  4096 Feb 11 16:12 node_modules
-rw-rw-r--  1 pepe pepe 41017 Feb 11 16:12 package-lock.json
-rw-rw-r--  1 pepe pepe   347 Feb 11 16:06 package.json
drwxrwxr-x  7 pepe pepe  4096 Feb 11 16:06 public
drwxrwxr-x  2 pepe pepe  4096 Feb 11 16:06 views
```

Aquí de lectura y ejecucion 

```sh
ubuntu@ip-172-31-39-104:~$ sudo ls -l /home/pepe/
total 16
-rw-rw-r--  1 pepe pepe  531 Feb 15 11:39 ecosystem.config.js
-rw-rw-r--  1 pepe pepe  530 Feb 14 20:07 ecosystem.config.js.backup
drwxrwxr-x  7 pepe pepe 4096 Feb 11 16:12 node-chat
drwxrwxr-x 11 pepe pepe 4096 Feb 13 16:02 parse
```

tbn lectura y ejecucion



```sh
ubuntu@ip-172-31-39-104:~$ sudo ls -l /home
total 8
drwxr-x--- 10 pepe   pepe   4096 Feb 15 11:39 pepe
drwxr-x---  5 ubuntu ubuntu 4096 Feb 13 15:21 ubuntu
```

La salida del comando `ls -l /home` muestra que el directorio `/home/pepe`, que contiene tu aplicación `node-chat`, tiene permisos `drwxr-x---`. 

Esto significa:

* `d`: Es un directorio.
* `rwx` para el usuario propietario (pepe): Tiene permisos de lectura (r), escritura (w), y ejecución (x).
* `r-x` para el grupo propietario (pepe): Tiene permisos de lectura y ejecución, pero no de escritura.
* Ningún permiso para otros usuarios (`---`): Otros usuarios no tienen ningún permiso en este directorio.

Dado que Nginx suele ejecutarse bajo el usuario `www-data` o similar, dependiendo de la configuración de tu sistema, el servidor web actualmente no tiene permiso para leer o acceder a los archivos dentro de `/home/pepe` debido a la falta de permisos para "otros usuarios".

Solución: Ajustar los Permisos

Para resolver este problema, hay varias estrategias que puedes seguir, dependiendo de tus necesidades de seguridad y configuración. Una opción común es agregar el usuario bajo el cual se ejecuta Nginx (comúnmente www-data) al grupo pepe y asegurarse de que el grupo tenga permisos de lectura (y ejecución, para directorios) en los archivos y directorios necesarios.

Me gusta las soluciones que se vean por la pantalla

```sh
ubuntu@ip-172-31-39-104:~$ sudo chmod o+rx /home/pepe
ubuntu@ip-172-31-39-104:~$ ls -l /home
        total 8
        drwxr-xr-x 10 pepe   pepe   4096 Feb 15 11:39 pepe
        drwxr-x---  5 ubuntu ubuntu 4096 Feb 13 15:21 ubuntu
```

Si recargas ya funciona. Además mira la cabecera estática 

![](/img/58.png)

El `755` es `rx` el chmod  


## DNS - Domain Name Service
Lo que hace que Internet, sea Internet

El servicio de DNS nos permite navegar por internet utilizando nombres de dominio, evitando así la necesidad de recordar las direcciones IP de los servidores que sirven el contenido que queremos consumir.

Actúa en la capa de aplicación de la pila de protocolos.

Tipos de registro DNS más importantes

* **A/AAAA** = Address. Apuntan a una IP. Traducen el dominio a una IP. 
* **CNAME** = Alias.
* **NS** = Name Server. Apuntan a una IP o dominio de un servidor DNS. 
* **MX** = Mail Exchange. Apuntan a los servidores de correo.

**Ejemplo: servidor propio y correo con Google Apps**

* **NS** = IP o dominio del servidor DNS del proveedor de dominio A/AAAA = IP de servidor de AWS
* **MX** = `aspmx.l.google.com`

**Jerarquía DNS***

![](/img/60.png)

---

![](/img/61.png)


[www.dnschecker.org](https://dnschecker.org/)

**Vamos a gestionar un dominio desde aws**

Cada uno lo tedrá comprado en una interface diferente, pero conceptualmente es lo mismo.

Fíjate que en AWS durante la prácticas habrás apagado el servidor para que no te cobre. Nosotros queremos que la web que vamos a crear no se apague.

En AWS podemos solicitar tener una ip fija para miservidor gratos mientras sea una ip por maquina, es decir ahora por la `web-15`

en Elastic IP addresses podemos solicitar en `Allocate Elastic IP address` / `create allocate`

![](/img//62.png)

Si la tienes ahí quieta AWS te la va a cobrar , si la asocias te permite gratis asociarla con alguna instancia

![](/img//64.png)

![](/img//65.png)

![](/img//66.png)

* esta ip te carga el chat http://34.224.192.130/
* la dns `te carga te carga el chat`.... porque?? 

```sh
➜  FullStack15_Servidores_Despliegue_Aplicaciones git:(main) ✗ ssh -i ../Despliegue_AWS/web15.pem ubuntu@34.224.192.130
Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 6.2.0-1018-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Thu Feb 15 19:03:42 UTC 2024

  System load:  0.0               Processes:             110
  Usage of /:   59.3% of 7.57GB   Users logged in:       1
  Memory usage: 53%               IPv4 address for eth0: 172.31.39.104
  Swap usage:   0%

 * Ubuntu Pro delivers the most comprehensive open source security and
   compliance features.

   https://ubuntu.com/aws/pro

Expanded Security Maintenance for Applications is not enabled.

31 updates can be applied immediately.
To see these additional updates run: apt list --upgradable

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


Last login: Thu Feb 15 16:05:46 2024 from 85.87.66.72
ubuntu@ip-172-31-39-104:~$ 
```

nada cambió , `te carga te carga el chat`.... porque?? 

```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-enabled$ ls -l
        total 0
        lrwxrwxrwx 1 root root 31 Feb 12 09:50 chat -> /etc/nginx/sites-available/chat
        lrwxrwxrwx 1 root root 37 Feb  9 13:46 react -> /etc/nginx/sites-available/react-todo
```

```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-enabled$ cat react 
server {
        listen 80;
        server_name ec2-54-224-151-83.compute-1.amazonaws.com;
        root /var/www/react-todo;
        index index.html;
        location / {
                try_files $uri $uri/ /index.html;
        }
}
```

Reacto sólo carga para la DNS que hemos dicho, por eso no carga. Pero porqué carga el chat?? que tiene de especial??
Hemos dicho que React solo responde por esta dns ` server_name ec2-54-224-151-83.compute-1.amazonaws.com;`

¿QUien atiende una peticion si nadie me atiende una peticion? el chat

```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-enabled$ cat chat 
server {
        listen 80 default; # este responde la llamada.
       
	 location /parse {       # cuando la peticion comienza por /parse (cualquir peticion)
                proxy_pass http://127.0.0.1:1337;
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }
        
	location ~ ^/(css|img|sounds|fonts|js)/ {
		root /home/pepe/node-chat/public;
		access_log off;
		expires max;
		add_header X-Owner AlexJustData;
	}

	location / {       # cuando la peticion comienza por barra (cualquir peticion)
                proxy_pass http://127.0.0.1:3000; # se la pasas a este
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }
}
```


hemos de modificar el archivo para que coja la nueva dns de amazon



ec2-34-224-192-130.compute-1.amazonaws.com


```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-enabled$ sudo nano react 

# ANTES
server {
        listen 80;
        server_name ec2-54-224-151-83.compute-1.amazonaws.com;
        root /var/www/react-todo;
        index index.html;
        location / {
                try_files $uri $uri/ /index.html;
        }
}
#DESPUES
server {
        listen 80;
        ec2-34-224-192-130.compute-1.amazonaws.com;
        root /var/www/react-todo;
        index index.html;
        location / {
                try_files $uri $uri/ /index.html;
        }
}


ubuntu@ip-172-31-39-104:/etc/nginx/sites-enabled$ sudo nginx -t
nginx: [warn] server name "/var/www/react-todo" has suspicious symbols in /etc/nginx/sites-enabled/react:4
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-enabled$ sudo systemctl reload nginx
```

Ahora la carga la app de Redux!! `http://ec2-34-224-192-130.compute-1.amazonaws.com/`


---

**para comprimir los estáticos**, 

> [!NOTE]
> Además es recomendable porque se te comprime al 90%

```sh
ubuntu@ip-172-31-39-104:/etc/nginx$ sudo nano nginx.conf

# Descomenta esta linea de nano
gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/java>

```

```sh
ubuntu@ip-172-31-39-104:/etc/nginx$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
ubuntu@ip-172-31-39-104:/etc/nginx$ sudo systemctl reload nginx
```

Ahora vete al browser 

![](/img//67.png)



**CREAR UN DOMINIO**

El servicio `Route 53 Dashborad` se pueden comprar dominios y gestionar dns´s. No hace falta comprar un dominio en amazon para poder gestionar las dns con ellos.

Las `Hosted zones` son las zonas hospedadas en aws

> [!NOTA]
> MIRA EL VIDEO -> 2:36:00 video 5.mp4


**Me creo un dominio gratis con** https://www.duckdns.org/

Le coloco la ip de la instancia aws web-15

![](/img//68.png)

Ahora en alexjust.duckdns.org  está cargando tu chat

Si tu ahora le dices `me-lo-invento.alexjust.duckdns.org`  te va a cargar igual el chat. Es decir cualquier subdominio que le pongas va a puntar a la mismia ip de dominio.

Esto significa que con nginx te pudes montar un servicio por ejemplo `next-cloud` que es como para montarte una nube en tu casa; es open source y tienes tus archivos concronizados desde el movil o pc, etc es una nube opencsource 

Si cualquier subdominio apunta al mismo servidor, podemos hacer 

* `chat.alexjust.duckdns.org`
* `react.alexjust.duckdns.org`
* `parse.alexjust.duckdns.org`


```sh
ubuntu@ip-172-31-39-104:~$ cd /etc/nginx/sites-available/
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ la -l
total 12
-rw-r--r-- 1 root root 1006 Feb 15 17:23 chat
-rw-r--r-- 1 root root 2412 May 30  2023 default
-rw-r--r-- 1 root root  229 Feb 15 19:17 react-todo
```

```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo nano chat 


server {
        listen 80 default; # este responde la llamada.

        server_name chat.alexjust.duckdns.org;

         location /parse {       # cuando la peticion comienza por /parse (cualquir peticion)
                proxy_pass http://127.0.0.1:1337;
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }

        location ~ ^/(css|img|sounds|fonts|js)/ {
                root /home/pepe/node-chat/public;
                access_log off;
                expires max;
                add_header X-Owner AlexJustData;
        }

        location / {       # cuando la peticion comienza por barra (cualquir peticion)
                proxy_pass http://127.0.0.1:3000; # se la pasas a este
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }
}
```


```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo nano react-todo 

server {
        listen 80;
        server_name ec2-34-224-192-130.compute-1.amazonaws.com react.alexjust.duckdns.org;
        root /var/www/react-todo;
        index index.html;
        location / {
                try_files $uri $uri/ /index.html;
        }
}
```

En nginx sólo puede haber un sitio que actue como defoult server

```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo nano default


# ANTES
server {
        listen 80 default_server;
        listen [::]:80 default_server;

# DESPUES
server {
        listen 80;
        listen [::]:80;

# ....


# ANTES
        server_name _;

# DESPUES
        server_name alexjust.duckdns.org;

```

CON NGINX HEMOS DE ACTIVARLO, ACUÉRDATE QUE ERA CON UN ENLACE DIRECTO

```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default

ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo nginx -t
nginx: [warn] conflicting server name "alexjust.duckdns.org" on 0.0.0.0:80, ignored
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

Falta generar el subdominio para parse
* Parse estaba funcionando con un subdominio del chat. entonces no hemos de crear un server nuevo para parse

```sh
# hago un copiar pegar y lo llamo parse
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo cp chat parse
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ ls -l
total 16
-rw-r--r-- 1 root root 1068 Feb 15 19:51 chat
-rw-r--r-- 1 root root 2401 Feb 15 19:56 default
-rw-r--r-- 1 root root 1068 Feb 15 20:00 parse
-rw-r--r-- 1 root root  256 Feb 15 19:53 react-todo
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo nano parse


# ANTES
server {
        listen 80 default; # este responde la llamada.

        server_name alexjust.duckdns.org chat.alexjust.duckdns.org;

         location /parse {       # cuando la peticion comienza por /parse (cualquir peticion)
                proxy_pass http://127.0.0.1:1337;
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }

        location ~ ^/(css|img|sounds|fonts|js)/ {
                root /home/pepe/node-chat/public;
                access_log off;
                expires max;
                add_header X-Owner AlexJustData;
        }

        location / {       # cuando la peticion comienza por barra (cualquir peticion)
                proxy_pass http://127.0.0.1:3000; # se la pasas a este
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }
}

# DESPUES
server {
        listen 80;

        server_name parse.alexjust.duckdns.org;

         location /parse {       # cuando la peticion comienza por /parse (cualquir peticion)
                proxy_pass http://127.0.0.1:1337;
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }
}
```

```sh
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo ln -s /etc/nginx/sites-available/parse /etc/nginx/sites-enabled/parse
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo nginx -t
        nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
        nginx: configuration file /etc/nginx/nginx.conf test is successful
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo systemctl reload nginx
```

**Ya te funciona todos los subdominios**

* http://alexjust.duckdns.org/
* http://chat.alexjust.duckdns.org/
* http://react.alexjust.duckdns.org/
* http://parse.alexjust.duckdns.org/parse/classes/Cervezas/



Quiero quitar esto `/parse` ->  http://parse.alexjust.duckdns.org`/parse`/classes/Cervezas/
Sin tocar el codigo de parse


```sh
# ANTES
server {
        listen 80;

        server_name parse.alexjust.duckdns.org;

         location /parse {       # cuando la peticion comienza por /parse (cualquir peticion)
                proxy_pass http://127.0.0.1:1337;
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }
}


# DESPUES
server {
        listen 80;

        server_name parse.alexjust.duckdns.org;

         location /parse {                                                                   
                proxy_pass http://127.0.0.1:1337/parse; # añadimos /parse
                proxy_redirect off;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "Upgrade";
                proxy_set_header Host $host;
        }
}


ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
ubuntu@ip-172-31-39-104:/etc/nginx/sites-available$ sudo systemctl reload nginx
```



