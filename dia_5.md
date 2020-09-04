# Búsqueda de archivos

Tipos de Rutas
* Absolutas: desde el directorio raiz hasta el archivo deseado.
* Relativas: desde el directorio actual hasta el archivo deseado.

## Caracteres especiales
```
*: sustituye una cantidad cualquiera de caracteres
?: sustituye exactamente un carácter
[]: sustituye un carácter de los indicados
```

Ejemplos

```
ls *ue*
ls nuev?
ls nuevo[1-5]
```

## find

```
$ find /usr -name mozilla # Busca todos los archivos que tengan en su nombre mozilla y que se encuentren en el directorio usr.

$ find /usr -name '*.so‘ # Busca todas las librerías del sistema con extension so

$ find / -name '*gtk*' # Busca todos los ficheros cuyo nombre contenga “gtk”

$ find / -size +3000k # Busca todos los ficheros de tamaño >= 3000 KB 

$ find / -name "*nuevo*" -type d -exec rm -fr {} \; 2>/dev/null # Borra todos los directorios del sistema que contengan la palabra nuevo.

$ find ./ -maxdepth 1 -type d # listar los directorios que hay en el directorio actual.

$ find ./ -mtime 0 -type f # lista los ficheros que se han modificado hoy en el directorio actual

$ find /var/dir -mtime +20 -type d -exec rm -f {} \; # borra todos los subdirectorios del directorio /var/dir que tengan una antigüedad mayor de 20 días
```

## locate

Es un comando de búsqueda de archivos, bastante parecido al comando find. La diferencia de locate es que la búsqueda la hace en una base de datos indexada para aumentar significativamente la velocidad de respuesta.

```
$ locate archivo
```

## Enlace Simbólico

Los enlaces son archivos especiales que permiten que varios nombres (enlaces) se asocien a un único e idéntico archivo,  existen 2 tipos de enlaces : enlace rígido y enlace simbólico.

### Enlaces simbólicos

En el caso de que se elimine un enlace simbólico, no se elimina el archivo al que indica. Los enlaces simbólicos se crean utilizando comandos In -s de acuerdo con la siguiente sintaxis: 

```
$ ln -s  /directorio  nombre_del_enlace
```

### Enlaces Duros

representan un nombre alternativo para un archivo. Así, cuando un archivo tiene dos enlaces físicos, la eliminación de uno u otro de estos enlaces no implica la eliminación del archivo. Más específicamente, mientras haya quedado al menos un enlace físico, el archivo no se elimina. Por otro lado, cuando se eliminan todos los enlaces físicos de un mismo archivo, también se elimina dicho archivo. Sin embargo, debemos advertir que sólo es posible crear enlaces físicos dentro de un único e idéntico sistema de archivos. Los enlaces físicos se crean utilizando comandos:

```
$ ln nombre_del_archivo_real nombre_del_enlace_fisico 
```


## Montaje de Dispositivos

### Dispositivos

* Disco duro IDE y CDROM: /dev/hdXY

- X: Número de disco/dispositivo_IDE (a, b, c...)
- Y: Número de partición (1, 2, 3...)

```
> /dev/hda
> /dev/hda1
> /dev/hdb3
```

* Disco duro SCSI, SATA y externos USB: /dev/sdXY
```
> /dev/sda
> /dev/sda1
> /dev/sdc4
```

**Montar** equivale a crear un acceso desde un directorio a una unidad o dispositivo.

**Desmontar**  es eliminar ese enlace.

### Tipos de montaje:
* Montaje Permanente: Se lo realiza configurando el archivo de configuración llamado fstab  el cual se encuentra dentro el directorio /etc/fstab.

* Montaje Temporal:  Se lo realiza con el comando mount el cual nos permite montar cualquier tipo de dispositivo  en los directorios /mnt y /media y para desmontar se utiliza el comando umount.

### tipos de sistemas de archivos:

Como ya vimos en otras entregas, todos los dispositivos se encuentran en el directorio /dev, solamente puede hacerlo el ROOT, los usuarios podrán hacer exclusivamente el montaje de manera reducida. 

```
> ext2, ext3 y ext4 (formato de linux para montaje de sistemas de archivos). 
> reisers (formato de linux utilizado en servidores). 
> vfat (formato fat utilizado para disketes y para particiones win9x). 
> ntfs (formato para particiones windows nt/2000/xp/vista/seven). 
> iso9660 (dispositivos ópticos y archivos punto iso). 
> /dev/hda0 primer disco duro, partición primaria  
> /dev/fd0 disquetera 
> /dev/sda pendrive y dispositivos scasi
> /dev/cdrom dispositivos cdrom
```
### mount

Este comando te permite montar dispositivos. 

```
$ mount /dev/dispositivo /ruta. 
$ mount -t vfat /dev/hda1 /mnt/windows # montar partición especificando el tipo de formato.
```

### umount

Este comando te permite desmontar dispositivos. 

```
$ umount /dev/dispositivo
```