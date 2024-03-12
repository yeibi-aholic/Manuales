# COMANDOS LINUX

|LETRA|COMANDOS|
|:-:|:-|
|c|[cat](#cat), [cd](#cd), [chmod](#chmod), [chown](#chown), [cp](#cp)|
|d|[df](#df), [diff](#diff), [dig](#dig)|
|g|[grep](#grep)|
|h|[head](#head), [history](#history)|
|k|[kill](#kill)|
|l|[locate](#locate), [ls](#ls)|
|m|[man](#man), [mkdir](#mkdir), [mv](#mv)|
|p|[ps](#ps), [pwd](#pwd)|
|r|[rm](#rm), [rmdir](#rmdir)|
|t|[tail](#tail)|

- ### pwd
##### *"print working directory"*

Muestra el nombre de la ruta del **directorio actual**.

~~~~ bash
$ pwd
/home/usuario
~~~~

- ### cd
##### *"change directory"*

Cambia el **directorio de trabajo** respecto a lo que se ponga después del comando.
~~~~ bash
$ pwd
/home/usuario
$ cd Carpeta1/Carpeta2
$ pwd
/home/usuario/Carpeta1/Carpeta2
~~~~

Para retroceder un directorio:
~~~~ bash
$ cd ..
$ pwd
/home/usuario/Carpeta1
~~~~

Para ir al *home* por defecto:
~~~~ bash
$ cd
$ pwd
/home/usuario
~~~~

Para retroceder hasta el direcdtorio principal:
~~~~ bash
$ cd /
$ pwd
/
~~~~

También se puede escribir la ruta completa deseada para acceder directamente:
~~~~ bash
$ cd /home/usuario/Carpeta3
$ pwd
/home/usuario/Carpeta3
~~~~

- ### ls
##### *"list"*

Listar el contenido de un directorio.
~~~~ bash
$ ls              
Contacts            Desktop             Documents
Downloads           Favorites           Links
Music               Pictures            source
Videos
~~~~

Para listar el contenido del directorio principal sin cambiar la ruta actual:
~~~~ bash
$ ls /
bin   dev  home  lib64  mnt  proc  run   srv  tmp  var
boot  etc  lib   media  opt  root  sbin  sys  usr
~~~~

Para listar el contenido del directorio *home* sin cambiar la ruta actual:
~~~~ bash
$ ls ~
Contacts            Desktop             Documents
Downloads           Favorites           Links
Music               Pictures            source
Videos              texto.txt
~~~~

Para listar solo directorios:
~~~~ bash
$ ls -d */
Contacts/           Desktop/            Documents/
Downloads/          Favorites/          Links/
Music/              Pictures/           source/
Videos/
~~~~

Para listar el contenido de los directorios con sus subdirectorios:
~~~~ bash
$ ls *
~~~~

Para listar todos los archivos y directorios con sus subdirectorios correspondientes hasta el último archivo:
~~~~ bash
$ ls -R
~~~~
> Se puede especificar un directorio para ejecutar la misma acción:
> ~~~~ bash
> $ ls Downloads -R
> ~~~~

Para listar el contenido de un directorio junto con su tamaño:
~~~~ bash
$ ls -s
total 10
0 Contacts          0 Desktop           0 Documents
0 Downloads         0 Favorites         0 Links
0 Music             0 Pictures          0 source
0 Videos       253744 texto.txt
~~~~

Para listar los contenidos en formato largo, por columnas: permisos, propietario, tamaño, fecha ultima modificación, ...
~~~~ bash
$ ls -l
total 10
d-r--          07/09/2022    13:59                Contacts
d-r--          30/11/2023    16:14                Desktop
da---          21/11/2023    16:42                Documents
d-r--          20/02/2024     9:31                Downloads
d-r--          07/09/2022    13:59                Favorites
d-r--          07/09/2022    13:59                Links
d-r--          07/09/2022    13:59                Music
d-r--          21/09/2023     9:36                Pictures
d----          12/09/2022    10:13                source
d-r--          08/09/2022    10:07                Videos
-a---          29/12/2022    12:47         253744 texto.txt
~~~~

Para listar hasta archivos y directorio ocultos:
~~~~ bash
$ ls -a
~~~~
> Cualquier cosa que comience con "." se considera oculto.

Para listar archivos y directorios por orden de fecha de última modificación en orden descendente:
~~~~ bash
$ ls -t
Downloads           Downloads           Downloads           
Downloads           Desktop             Documents
Pictures            texto.txt           source
Videos              Contacts            Favourites
Links               Music
~~~~
> Para un orden ascendente:
> ~~~~ bash
> $ ls -tr
> ~~~~

Para listar archivos y directorios por orden de tamaño en orden descendente:
~~~~ bash
$ ls -S
~~~~
> Para un orden ascendente:
> ~~~~ bash
> $ ls -Sr
> ~~~~

Para listar los archivos y directorios en una sola línea separada por comas:
~~~~ bash
$ ls -m
Contacts, Desktop, Documents, Downloads, Favorites, Links, Music, Pictures, source, Videos
~~~~

Para generar un archivo con el listado que queremos:
~~~~ bash
$ ls > output.txt
~~~~
> Se pueden usar cualquiera de los indicadores anteriores, solo que en este caso no se registrará por pantalla.

- ### cat
##### *"concatenate"*

Muestra el contenido de un archivo de texto.
> Es necesario saber el nombre y extensión del archivo.
~~~~ bash
$ cat archivo.txt
~~~~
> Si quisieramos desplazarnos por el contenido línea por línea:
> ~~~~ bash
> $ cat archivo.txt | more
> ~~~~

> Si quisieramos desplazarnos por el contenido por páginas (pudiendo usar *RePag* y *AvPag*):
> ~~~~ bash
> $ cat archivo.txt | less
> ~~~~

Para ver el contenido de varios archivos con el mismo formato:
~~~~ bash
$ cat *.txt
~~~~

Para crear un archivo nuevo:
~~~~ bash
$ cat > nuevoarchivo.txt
~~~~

Para redirigir el contenido de un archivo a otro:
~~~~ bash
$ cat archivo1.txt > archivo2.txt
~~~~
> Si el <archivo2.txt> no existe se creará. En caso contrario, sobrescribirá el existente.

Para escribir el contenido de un archivo al final de otro:
~~~~ bash
$ cat archivo1.txt >> archivo2.txt
~~~~

Para juntar varios archivos en uno nuevo:
~~~~ bash
$ cat archivo1.txt archivo2.txt > archivo3.txt
~~~~

Para marcar el final de cada línea con un *"$"*:
~~~~ bash
$ cat -E archivo.txt
$ cat -e archivo.txt
~~~~

Para mostrar el número línea:
~~~~ bash
$ cat -n archivo.txt
~~~~

Para evitar líneas vacías:
~~~~ bash
$ cat -s archivo.txt
~~~~

Para mostrar el archivo de forma inversa:
~~~~ bash
$ tac archivo.txt
~~~~

- ### cp
##### *"copy"*

Copiar archivos o directorios a otro directorio.
~~~~ bash
$ cp texto.txt /home/usuario/carpeta_destino/
~~~~
> Si queremos mandar varios archivos al mismo destino, solo habrá que escribirlos todos seguidos:
> ~~~~ bash
> $ cp texto.txt imagen.jpg cancion.mp3 /home/usuario/carpeta_destino/
> ~~~~

> Si queremos copiar el contenido pero cambiar el nombre, habrá que especificarlo en el directorio:
> ~~~~ bash
> $ cp texto.txt /home/usuario/carpeta_destino/texto_nuevo.txt
> ~~~~
>> Si no especificamos un directorio, se creará una copia en el directorio actual.

- ### mv
##### *"move"*

Mueve o renombra archivos y directorios.
~~~~ bash
$ mv archivo.txt nuevo_archivo.txt
$ mv archivo.txt /home/usuario/Carpeta
~~~~

- ### mkdir
##### *"make directory"*

Crea directorios y subdirectorios.
~~~~ bash
$ mkdir /home/Carpeta1/Carpeta2/Carpeta3
~~~~

Para crear un directorio entre dos directorios existentes:
~~~~ bash
$ mkdir -p /directorio1/directorio3/directorio2
~~~~

- ### rmdir
##### *"remove directory"*

Elimina directorios vacíos.
~~~~ bash
$ rmdir Carpeta
~~~~

- ### rm
##### *"remove"*

Elimina archivos y directorios.
~~~~ bash
$ rm texto.txt
~~~~

Para eliminar únicamente directorios no vacíos:
~~~~ bash
$ rm -r Carpeta
~~~~

Para preguntar antes de borrar:
~~~~ bash
$ rm -i *.txt
~~~~

El equivalente a *rmdir*:
~~~~ bash
$ rm -d
~~~~

- ### locate
##### *"localizar"*

Busca archivos en la base de datos de **Linux**.
~~~~ bash
$ locate archivo
$ locate Carpeta
~~~~
> Los resultados con el nombre del archivo incluirán la ruta completa de archivos que su nombre incluya tal texto.

> Los resultados con el nombre del directorio incluirán los ficheros finales de todos los subdirectorios.

Para búsquedas específicas de archivos:
~~~~ bash
$ locate -r archivo$
~~~~
> Este formato busca nombres de archivos exactos, incluyendo extensión.

Para obtener la cantidad de archivos con el mismo nombre:
~~~~ bash
$ locate -c archivo
~~~~

Para no hacer distinción entre mayúsculas y minúsculas:
~~~~ bash
$ locate -i archivo
~~~~

Para limitar el número de resultados:
~~~~ bash
$ locate archivo n 1234
~~~~

- ### grep
##### *"global regular expression print"*

Busca patrones a partir de [expresiones regulares](https://github.com/yeibi-aholic/Markdown/blob/main/ManualPython.md#expresiones-regulares).
~~~~ bash
$ grep texto archivo.txt
~~~~

Para obtener la cantidad de líneas con el texto de búsqueda:
~~~~ bash
$ grep -c texto archivo.txt
~~~~

Para no hacer distinción entre mayúsculas y minúsculas:
~~~~ bash
$ grep -i texto archivo.txt
~~~~

Normalmente se suele mezclar con el comando de búsqueda *cat*:
~~~~ bash
$ cat archivo.txt | grep texto
~~~~

- ### dig
##### *"domain information groper"*

Consulta los registros DNS de un dominio.
~~~~ bash
$ dig github.com

; <<>> DiG 9.9.4-RedHat-9.9.4-18.el7_1.5 <<>> github.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 60218
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; MBZ: 0005 , udp: 4000
;; QUESTION SECTION:
;github.com.			IN	A

;; ANSWER SECTION:
github.com.		5	IN	A	140.82.121.3

;; Query time: 2006 msec
;; SERVER: 192.168.163.2#53(192.168.163.2)
;; WHEN: mar feb 20 16:57:23 CET 2024
;; MSG SIZE  rcvd: 55
~~~~

- ### df
##### *"disk filesystem"*

Enumera el espacio utilizado y disponible en todos los sistemas de archivos montados.
~~~~ bash
$ df
S.ficheros              bloques de 1K   Usados Disponibles Uso% Montado en
/dev/mapper/centos-root      52403200  7807356    44595844  15% /
devtmpfs                       925548        0      925548   0% /dev
tmpfs                          935256       76      935180   1% /dev/shm
tmpfs                          935256     9076      926180   1% /run
tmpfs                          935256        0      935256   0% /sys/fs/cgroup
/dev/mapper/centos-home      70687004 44012452    26674552  63% /home
/dev/sda1                      508588   171008      337580  34% /boot
~~~~

Para hacerlo más legible:
~~~~ bash
$ df -h
S.ficheros              Tamaño Usados  Disp Uso% Montado en
/dev/mapper/centos-root    50G   7,5G   43G  15% /
devtmpfs                  904M      0  904M   0% /dev
tmpfs                     914M    76K  914M   1% /dev/shm
tmpfs                     914M   8,9M  905M   1% /run
tmpfs                     914M      0  914M   0% /sys/fs/cgroup
/dev/mapper/centos-home    68G    42G   26G  63% /home
/dev/sda1                 497M   167M  330M  34% /boot
~~~~

Para leerlo en MB:
~~~~ bash
$ df -m
S.ficheros              bloques de 1M Usados Disponibles Uso% Montado en
/dev/mapper/centos-root         51175   7625       43551  15% /
devtmpfs                          904      0         904   0% /dev
tmpfs                             914      1         914   1% /dev/shm
tmpfs                             914      9         905   1% /run
tmpfs                             914      0         914   0% /sys/fs/cgroup
/dev/mapper/centos-home         69031  42981       26050  63% /home
/dev/sda1                         497    167         330  34% /boot
~~~~

- ### head
- ### tail

Muestra las primeras/últimas 10 líneas del archivo.
~~~~ bash
$ head archivo.txt
$ tail archivo.txt
~~~~
> Si se quiere imprimir un número "*" de líneas:
> ~~~~ bash
> $ head -* archivo.txt
> $ head -n* archivo.txt
> $ tail -n * archivo.txt
> ~~~~

Para examinar un archivo en busca de variaciones (solo para *tail*):
~~~~ bash
$ tail -f archivo.txt
~~~~

- ### diff
##### *"difference"*

Muestra las diferencias entre dos archivos.
~~~~ bash
$ diff archivo1.txt archivo2.txt
~~~~
> *<*: Hace referencia a la línea que presenta cambios en el fichero 1.
> *>*: Hace referencia a la línea que presenta cambios en el fichero 2.

Para mostrar las diferencias de forma más visual:
~~~~ bash
$ diff -y archivo1.txt archivo2.txt
~~~~
> Se mostrarán ambos archivos en dos columnas con los caracteres *|*, *<* o *>* para representar las diferencias.

Para comparar dos directorios:
~~~~ bash
$ diff -r Carpeta1 Carpeta2
~~~~

Para crear un archivo de parche con las diferencias:
~~~~ bash
$ diff -u archivo1.txt archivo2.txt > archivo3.diff
~~~~

Para ignorar los espacios en blanco:
~~~~ bash
$ diff -b archivo1.txt archivo2.txt
~~~~

- ### chmod
##### *"change mode"*

Permite cambiar los permisos de un archivo.
> Los permisos están representados por letras, y cada letra representa un tipo diferente de acceso.
> El permiso para todos los demás usuarios no se cambiará.
~~~~ bash
$ chmod *** archivo.txt
~~~~
> Cada dígito representa el permiso de *usuario*, *grupo* y *resto* respectívamente.

|Dígito|Binario|Lectura (r)|Escritura (w)|Ejecución (x)|
|:-:|:-:|:-:|:-:|:-:|
|0|000| | | |
|1|001| | |X|
|2|010| |X| |
|3|011| |X|X|
|4|100|X| | |
|5|101|X| |X|
|6|110|X|X| |
|7|111|X|X|X|

Para dar permisos de forma recursiva en una carpeta:
~~~~ bash
$ chmod -R *** Carpeta
~~~~

> De forma estandar se suele aplicar los permisos:
> - **644** para ficheros.
> - **755** para directorios.

> Es mejor evitar el permiso **777**.

- ### chown
##### *"change owner"*

Indica quién es el dueño y grupo de un archivo.
~~~~ bash
$ chowm usuario:grupo archivo.txt
~~~~

Para asignar de forma recursiva en una carpeta:
~~~~ bash
$ chown -R *** Carpeta
~~~~

- ### ps
##### *"process status"*

Lista los procesos que se ejecutan en el sistema.
~~~~ bash
$ ps -*
~~~~

|Opción|Descripción|
|:-:|:-|
|-e/-A|muestra todos los procesos que se están ejecutando en el sistema (los de todos los usuarios).|
|-a|muestra todos los procesos excepto los que no están asociados a la terminal con la que se ejecuta el comando.|
|-C [procesos]|muestra únicamente los procesos que tienen el nombre que se ha indicado en la condición [procesos].|
|-d|muestra todos los procesos sin los nombres de los usuarios cuya sesión está asignada al proceso.|
|-f|muestra todos los procesos con mayor detalle.|
|-r|muestra únicamente los procesos que están ejecutándose en ese momento.|
|-T|muestra únicamente los procesos asignados a la terminal con la que se ejecuta el comando *ps*.|
|-x|muestra únicamente los procesos que pertenecen al usuario ejecutor.|
|-u|muestra únicamente los procesos que pertenecen al usuario.|
|-w|lo mismo que *-u* pero con la información más simplificada.|

- ### kill

Finaliza procesos en ejecución.
~~~~ bash
$ kill -9 *****
~~~~
> Para el número del proceso a "matar" se puede obtener mediante el comando *ps*.

Para obtener las diferentes señales del comando *kill*:
~~~~ bash
$ kill -l        
 1) SIGHUP        2) SIGINT          3) SIGQUIT        4) SIGILL         5) SIGTRAP        6) SIGABRT        7) SIGBUS
 8) SIGFPE        9) SIGKILL        10) SIGUSR1       11) SIGSEGV       12) SIGUSR2       13) SIGPIPE       14) SIGALRM
15) SIGTERM      16) SIGSTKFLT      17) SIGCHLD       18) SIGCONT       19) SIGSTOP       20) SIGTSTP       21) SIGTTIN
22) SIGTTOU      23) SIGURG         24) SIGXCPU       25) SIGXFSZ       26) SIGVTALRM     27) SIGPROF       28) SIGWINCH
29) SIGIO        30) SIGPWR         31) SIGSYS        32) SIGRTMIN      33) SIGRTMIN+1    34) SIGRTMIN+2    35) SIGRTMIN+3
36) SIGRTMIN+4   37) SIGRTMIN+5     38) SIGRTMIN+6    39) SIGRTMIN+7    40) SIGRTMIN+8    41) SIGRTMIN+9    42) SIGRTMIN+10
43) SIGRTMIN+11  44) SIGRTMIN+12    45) SIGRTMIN+13   46) SIGRTMIN+14   47) SIGRTMIN+15   48) SIGRTMAX-14   49) SIGRTMAX-13
50) SIGRTMAX-12  51) SIGRTMAX-11    52) SIGRTMAX-10   53) SIGRTMAX-9    54) SIGRTMAX-8    55) SIGRTMAX-7    56) SIGRTMAX-6
57) SIGRTMAX-5   58) SIGRTMAX-4     59) SIGRTMAX-3    60) SIGRTMAX-2    61) SIGRTMAX-1    62) SIGRTMAX	
~~~~

- ### history

Muestra el historial de acciones por parte del usuario en el sistema.
~~~~ bash
$ history
~~~~

Para borrar el historial:
~~~~ bash
$ history -c
~~~~

- ### man
##### *"manual"*

Proporciona páginas de manual completas de las herramientas de **Unix**.
~~~~ bash
$ man wget
WGET(1)                            GNU Wget                            WGET(1)

NAME
       Wget - The non-interactive network downloader.

SYNOPSIS
       wget [option]... [URL]...

DESCRIPTION
       GNU Wget is a free utility for non-interactive download of files from
       the Web.  It supports HTTP, HTTPS, and FTP protocols, as well as
       retrieval through HTTP proxies.

       Wget is non-interactive, meaning that it can work in the background,
       while the user is not logged on.  This allows you to start a retrieval
       and disconnect from the system, letting Wget finish the work.  By
       contrast, most of the Web browsers require constant user's presence,
       which can be a great hindrance when transferring a lot of data.

       Wget can follow links in HTML, XHTML, and CSS pages, to create local
       versions of remote web sites, fully recreating the directory structure
       of the original site.  This is sometimes referred to as "recursive
       downloading."  While doing that, Wget respects the Robot Exclusion
       ...
~~~~
