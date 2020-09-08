# Redireccionando en Linux

Un proceso en un sistema Linux tiene inicialmente abiertos 3 canales:

* 0: STDIN o entrada estándar
* 1: STDOUT o salida estándar
* 2: STDERR o salida de error

Ejemplo: (refinería) Metes crudo por 0 (STDIN), consigues gasolina por 1 (STDOUT) y bastantes residuos por el “desagüe” 2 (STDERR).

## Tubería

También conocidas como pipes relacionan la salida estándar de un comando con la entrada estándar de otro .

Redirigiendo la salida de un comando:


### > : redirigir STDOUT a un fichero
```
$ ls > listado.txt
```
### >>: redirigir STDOUT al final de un fichero
```
$ ls >> listados.txt
```
### 2>: redirigir STDERR a un fichero:
```
ls  2> errores.txt
```
### 2>>: redirigir STDERR al final de un fichero:
```
ls  2>> errores.txt
```
### 2>&1: redirigir STDOUT y STDERR a un fichero:
```
ls > salida 2>&1
```

## Redirigiendo la salida de un comando

`|` símbolo pipe ayuda a redirigir  el STDOUT  de un comando al STDIN de otro: es posible recoger la salida de un desagüe y conducirlo a la entrada de otro comando.

```
$ history | more
$ cat fichero.txt | grep nuevo | tail –n 10 
$ cat fichero.txt | sort –u
$ cat fichero.txt | sort > fichero_1.txt 
$ ps | grep sshd
```

## Compresión de Archivos 

En Linux existen varios formatos de compresión como ser: bzip2, gzip, p7zip, tar, unzip, zip, unrar.

### gzip y bzip2

Para comprimir primero tenemos que empaquetar todos los archivos y directorios que queremos comprimir para ello se utiliza el comando tar.

### tar

Permite empaquetar archivos y directorios
```
$ tar [opciones][origen] [destino]
```
Opciones
* c crear un archivo
* x extraer de un archivo
* t listar contenidos del archivo 
* v ver un reporte de las acciones a medida que se van realizando.
* f empaquetar contenidos de archivos
* z para comprimir a la vez que se empaqueta.

1. empaquetar: `tar cvf archivo.tar carpeta/*`
2. desempaquetar: `tar xvf archivo.tar`

#### gz

solo comprime archivos, no carpetas

1. empaquetar: `gzip -q archivo`
2. desempaquetar: `gzip -d archivo.gz`

#### tar.gz

1. empaquetar: `tar czvf archivo.tar.gz carpeta/*`
2. desempaquetar: `tar xzvf archivo.tar.gz`

#### zip

1. empaquetar: `zip archivo.zip carpeta/archivos`
2. desempaquetar: `unzip archivo.zip`

#### .bz2 
solo comprime archivos, no carpetas

1. empaquetar: `bzip2 archivobunzip2 archivo`
2. desempaquetar: `zip2 -d archivo.bz2bunzip2 archivo.bz2`

#### tar.bz2

1. empaquetar: `tar -c archivos | bzip2 > archivo.tar.bz2`
2. desempaquetar: `bzip2 -dc archivo.tar.bz2 | tar jvxf archivo.tar.bz2`

#### rar
1. empaquetar: `rar a archivo.rar /carpeta/archivos`
2. desempaquetar: `rar x archivo.rar`


## Manejo de Procesos

(bg, fg and CTRL+Z) El sistema es multitarea, podemos dejar múltiples procesos corriendo en segundo plano. 
ejemplo `$ sleep 100 &` y con el comando `jobs` se puede ver los procesos que se estan ejecutando.

### bg

Permite listar el ultimo proceso enviado a segundo plano

```
$ bg
```

### fg

Permite colocar un proceso a primer plano  (foreground).

```
$ fg [numero de proceso]
```

### kill

Nos permite matar un proceso por su id 

```
$ kill -9 [id proceso]
```

### pkill

Nos permite matar un proceso por su nombre 
```
$ pkill -9 [nombre_proceso]
```


## Alias en linux

Un alias es un nombre mas entendible que se le da a un comando.

```
$ alias nombre_entendible=comando
$ alias apagar=halt
$ alias listar_archivos=ls 
$ alias leer_archivo=cat
$ alias listar_archivos='ls -l'
$ unalias apagar # Permite eliminar un alias personalizado.
```

## Administración de Usuarios

Características de usuarios Unix: Los sistemas Unix son sistemas multiusuario. Cada usuario tiene una serie de características propias y asociadas:

`su/sudo (cambia de usuario o privilegios)`

```
uid: identificativo de usuario (debe ser único)
gid: identificativo de grupo
```

### Gestión de usuarios

#### adduser (crear usuarios)
```
$ adduser alumno --ingroup nombre_grupo
$ adduser –-home /home/alumno –-shell /bin/sh –uid 5001 –groups curso alumno
```
#### usermod (modificar usuarios)
```
$ usermod –-shell /bin/bash alumno
$ usermod -G softwarelibre alumno # esto añade a 'alumno' al grupo 'softwarelibre'
```
#### userdel (eliminar usuarios)
```
$ userdel softwarelibre
$ userdel -r softwarelibre
```
### Gestión de grupos

#### groupadd (añade grupo o usuario a grupo)
```     
$ groupadd curso1
```
#### groupmod (modifica grupo)

```
$ groupmod -n curso curso1
```

#### delgroup (elimina grupo o usuario de grupo)

```
$delgroup curso
```
#### groups (muestra a que grupos pertenece un usuario)
```
$groups group_name user_name
```

Los archivos de configuracion de usuarios:

* /etc/passwd
* /etc/shadow
* /etc/sudoers
