Intérpretes de comandos y comandos
======================================

En la mayoría de las exploraciones en el mundo de UNIX, estará hablando con el
sistema a través del uso de un intérprete de comandos.

Un intérprete de comandos es simplemente un programa que toma la entrada del usuario (p.ej. las órdenes
que teclea) y las traduce a instrucciones.

Esto puede ser comparado con el COMMAND.COM de MS-DOS, el cual efectua esencialmente las misma tarea.
El intérprete de comandos es solo uno de los interfaces con UNIX. Hay muchos interfaces posibles como el sistema X Windows, el cual le permite ejecutar
comandos usando el ratón y el teclado.

'/Users/elvikito->' es el prompt del intérprete de comandos, indicando que está listo para recibir órdenes. Tratemos de decirle al sistema que haga algo
interesante:

``
$ make love
``

Bien, como resulta que make es el nombre de un programa ya existente en el sistema, el intérprete de comandos lo ejecuta.

Esto nos lleva a una cuestión importante: >Que son órdenes? >Que ocurre cuando tecleamos "make love"?. La primera palabra de la orden, "make", es el nombre de la orden a ejecutar. El resto de la orden es tomado como argumentos de la orden. Ejemplos:

``
$ cp foo bar
``

Aquí, el nombre de la orden es "cp", y los argumentos son "foo" y "bar".

Una orden que el propio intérprete de comandos sabe ejecutar por si mismo, El intérprete de comandos también comprueba si la orden es un
"alias" o nombre sustitutorio de otra orden

Intérpretes de comandos y comandos
======================================

En la mayoría de las exploraciones en el mundo de UNIX, estará hablando con el sistema a través del uso de un intérprete de comandos.

Shell
---------------------------------------
Shell como significado el caparazon, existen varias shells, el mas comun ``sh`` llamada bourne shell ``bash`` (bourne again shell), ``tcsh`` (C shell), ``zsh`` (Zero shell)


Un intérprete de comandos es simplemente un programa que toma la entrada del usuario (p.ej. las órdenes que teclea) y las traduce a instrucciones.

Esto puede ser comparado con el COMMAND.COM de MS-DOS, el cual efectua esencialmente las misma tarea.

El intérprete de comandos es solo uno de los interfaces con UNIX. Hay muchos interfaces posibles como el sistema X Windows, el cual le permite ejecutar comandos usando el ratón y el teclado.

"/Users/elvikito->" es el "prompt" del intérprete de comandos, indicando que está listo para recibir órdenes. Tratemos de decirle al sistema que haga algo
interesante:

``
$make love
``

Bien, como resulta que make es el nombre de un programa ya existente en el sistema, el intérprete de comandos lo ejecuta.

Esto nos lleva a una cuestión importante: >Que son órdenes? >Que ocurre cuando tecleamos "make love"?. La primera palabra de la orden, "make", es el nombre de la orden a ejecutar. El resto de la orden es tomado como argumentos de la orden. Ejemplos:

``
$ cp foo bar
``

Aquí, el nombre de la orden es "cp", y los argumentos son "foo" y "bar".

Una orden es propio del intérprete de comandos sabe ejecutar por si mismo, El intérprete de comandos también comprueba si la orden es un "alias" o nombre sustitutorio de otra orden

En nuestro ejemplo, el intérprete de comandos busca el programa llamado ``make`` y lo ejecuta con el argumento ``love``. make es un programa usado a menudo para
compilar programas grandes, y toma como argumentos el nombre de un "objetivo" a compilar.

En el caso de "make love", ordenamos a make que compile el objetivo love. Como make no puede encontrar un objetivo de ese nombre, falla enviando un mensaje de error y volviendo al intérprete de comandos.

```
$eat dir Entrada no valida.
```

Entorno de trabajo.
------------------------------------
* case sensitive, sencible a mayusculas. (ECHO =! echo)
* sintaxis, comando arg1 arg2...argn
* ./programa
* `$` | `#` mortal user, superuser

Entrada y salida
------------------------------------
Una vez que se ejecuta un comando abre tres procesos,
```
> stdin - teclado.
> stdout - pantalla.
> stderr - pantalla.
```
supongamos que tenemos una refineria, tenemos materia prima y como 2 salidas del producto.

comandos para el manejo del sistema de ficheros
------------------------------------------------
```
- ls (lista contenido de directorios)
- mkdir / rmdir (crea  / elimina directorios vacíos)
- cd / pwd (cambia /muestra la ruta de directorio)
- touch (crea fichero vacío o actualiza existente)
- cp / mv / rm (copia / mueve/ elimina fichero)
- man / info (ayuda sobre comandos)
- echo (muestra una línea de texto)
- date / cal (muestra la hora del sistema)
- file (muestra el tipo de fichero)
- halt / reboot (apaga el sistema)
- find (permite realizar busquedas de ficheros).
- du (permite ver el tamaño de un directorio en kbp, megas, gigas).
- df (permite ver las particiones montadas).
- locate (permite ver la localizacion de un archivo).
- tail (permite ver las ultimas lineas ).
- head (permite ver las primeras lineas ).
- mount (permite montar dispositivos)
- umount (permite desmmontar dispositivos)
- ln (permite crear enlaces simbolicos)
- sort (permite ordenar lineas)
```

## Comandos para el manejo del sistema

```
* who (Muestra el nombre de los usuarios que han ingresado al sistema.) 
* whoami (Muestra el nombre del usuario con el que estamos trabajando. )
* grep (Muestra todas las líneas de un fichero dado que coinciden con un cierto patrón.)
* top (Muestra la carga del sistema, CPU, etc. )
* free (Muestra la cantidad de espacio libre y utilizado en la memoria RAM y swap.)
* ps (Muestra los procesos que se están ejecutando en nuestro sistema actualmente).
```

## ls 

El comando para mostrar los ficheros y/o directorios. 

Opciones
```
$ ls -l  # Permite ver los archivos y directorios en lista, informándonos sobre sus permisos, dueños de los archivos, tamaño, fecha y hora de creación y su nombre respectivo. 
$ ls -a # Permite ver los archivos y carpetas ocultas que contiene el  directorio actual. 
$ ls -lh # Igual que ls -l, solo que el tamaño de los archivos están en kb o  mb. 
$ ls -la # Igual q ls -l, solo que ahora también lista los archivos ocultos. 
$ lspci # Ver dispositivos conectados a la placa madre mediante un bus  PCI. 
$ lsusb # Ver los buses USB y los dispositivos conectados a los mismos. 
$ lsmod # Ver los módulos del kernel 
```

## mkdir

Comando que nos permite crear directorios.

Estructura basica:

```
* mkdir primer_nombre_alumno
* mkdir -p semestre/curso_alumno/tema
```

Ejemplos:

```
$ mkdir carlos
$ mkdir "carlos alberto"
$ mkdir -p 2020/admin_de_servidores/ejm/a
```
## rmdir

Comando que nos permite borrar directorios

Estructura basica:

```
$ rmdir nombre_archivo
```

## cd

Comando que nos permite movernos a través del árbol de directorios

Estructura basica: 

```
* cd /  Esto nos moverá al directorio raíz. 
* cd .. Subir un nivel en el árbol de directorios.
* cd ../directorio2 Moverse en el mismo nivel de directorios.
* cd directorio Bajar un nivel, a la carpeta directorio. 
* cd -  Retornar al directorio que se ubicaba anteriormente.
```

## rm

Borrar archivos y/o directorios. Este es un comando que debemos utilizar con mucho cuidado, ya que si borramos algunos archivos por equivocación, Sera imposible recuperarlos. 

```
$ rm archivo  # Borra un archivo.
$ rm archivo1 archivo2 archivon  # Borrar varios archivos a la vez. 
$ rm *  # Borrar todos los archivos que se encuentran en la carpeta desde donde es ejecutado el comandos. (¡CUIDADO...!) 
$ rm carpeta/*  # Borra todos los archivos que se encuentran en carpeta, solo si esta vacia. 
$ rm -rf carpeta # Borra todos los archivos y carpetas que contenga.
```

## cp

Copiar archivos y/o directorios.

Ejemplos 

```
$ cp archivo /ruta/directorio # Copia archivo en /ruta/directorio/.
$ cp arch1 arch2 arch3 /ruta # copia arch1, arch2 y arch3 en /ruta
$ cp archivo1 archivocopia Hacer una copia de archivo1 con otro nombre(archivocopia). 
$ cp * /ruta/directorio # Copia todo el contenido de la carpeta donde nos encontramos al momento de ejecutar el comando /ruta/directorio.
$ cp - R directorio /ruta # Copia la carpeta con todo su contenido en forma recursiva, hacia la carpeta /ruta. 
$ cp -rf directorio /ruta # Copia carpeta y contenido a la ruta /ruta.
```

## mv

Comando con el cual puedo borra archivos y/o directorios, también permite renombrarlos. 

Ejemplos:

```
$ mv archivo /ruta #mueve archivo a la carpeta /ruta. 
$ mv * /ruta #moeve todos los archivos y carpetas que se encuentran en la carpeta actual en el directorio /ruta. 
$ mv archivo arch_renombrado #cambia de nombre a archivo por arch_renombrado. 
$ mv directorio nuevo_directorio # cambia de nombre a directorio por nuevo_directorio.
```

## pwd

El comando pwd indica el camino absoluto del directorio en el cual nos encontramos actualmente. 

```
$ pwd 
```

## file

El comando file determina con cierto grado de precisión el tipo de un fichero que se le pasa como argumento. 

```
  $ file nombre_fichero 
```

## du
Comando que permite conocer el tamaño ocupado por un archivo y su respectiva jerarquía de directorios .

```
$ du -h # Visualiza los tamaños de los directorios en forma representativa (M para Megabytes y K para kilobytes). 
$ du -sh # directorio Visualiza los tamaños de los directorios que contiene directorio.
```

## less

Muestra un archivo en la pantalla pagina por pagina. 

```
$ less archivo 
```

## cat

Muestra un archivo en la pantalla.

```
$ cat archivo 
```
## tail

visualiza las ultimas líneas de un archivo. 
```
$ tail archivo  
$ tail –n 10 # archivo muestra las 10 ultimas líneas del archivo.
$ tail –f  # archivo muestra las líneas del archivo dinámicamente.
```

## head

visualiza las primeras líneas de un archivo. 
```
$ head archivo 
$ head –n 10 # archivo muestra las 10 primeras líneas de un archivo.
```
## df

Se emplea para conocer información acerca de las particiones y dispositivos montados actualmente en el sistema, el espacio libre y ocupado por los dispositivos.

```
$ df -h # Ver particiones montadas actualmente en Mb y Gb. 
$ df -Th # Ver particiones montadas con su  formato de archivos. 
```
## fdisk

En Linux el particionador estándar es el fdisk. Este posee una interfaz texto que permite crear, modificar y borrar particiones de diversos tipos (Linux, FAT12/16 / 3 2, NTFS, minix, Linux Swap, HPFS, Novell, etc.).

```
$ fdisk -l # Listar las particiones. 
```

## cfdisk

Editor de particiones fdisk ( ¡cuidado solo expertos!) 

```
#cfdisk /dev/sda  # sda es el primer disco duro.
```
## touch

Permite crear ficheros vacíos

```
$ touch nombre_archivo.
```

## more

Muestra un archivo en la pantalla pagina por pagina. 

```
$ more archivo
```

## echo

Muestra en la terminal los argumentos pasados.

```
$ echo 'cadena'
```

## sort

Permite ordenar lineas de un archivo. 

```
$ sort archivo 
$ sort -r archivo # muestra las lineas en orden inverso
$ sort -u archivo # Ordenar un fichero eliminando las líneas
```

## grep

Muestra todas las líneas de un fichero dado que coinciden con un cierto patrón.

```
$ grep <patrón> archivo
```

## top

Muestra la carga del sistema, CPU, etc. dinámicamente. 
```
$ top
```
## ps 

Muestra los procesos que se están ejecutando en nuestro sistema actualmente.

## history

Permite mostrar el historial de todos los comandos ejecutados. 
```
$ history 
$ history  5 # muestra los 5 últimos comando ejecutados.
```