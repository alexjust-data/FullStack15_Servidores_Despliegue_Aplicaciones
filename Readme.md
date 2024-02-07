
## AWS

Iniciamos con el video **1.mp4**

---

**trucos**

* `Ctrl+r` : es un buscador de comandos antiguos, has de decirle las palabras que quieres buscar
* `sudo !!` : cuando te olvidas poner sudo en el comando, esto te permite ejecutar ell mismo comando que antes con sudo delante

![](img/1.png)

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

![](img/2.png)

![](img/4.png)

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

![](img/5.png)

* **sudo nano /etc/crontab** : Programando tareas de sistema


![](img/6.png)


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

![](/img/7.png)

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

![](/img/8.png)

---

![](/img/9.png)

---

Incluimos el puerto de acceso HTTP con dns 0.0.0.0. para que pueda acceder todo el mundo, si quieres puedes decirle que solo puede acceder una direccion particular.
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

![](/img/12.png)

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


Ahora vete al browser y recarga la página `https://54.224.151.83` la verás así `https://startbootstrap.com/template/sb-admin`




