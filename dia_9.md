# ¿Qué es un script de bash?

Un script de bash es un archivo de texto sin formato que contiene una serie de comandos. Estos comandos son una mezcla de comandos que normalmente escribiríamos nosotros mismos en la línea de comandos (como ls o cp, por ejemplo)

## ¿Cómo trabajan?

En el ámbito de Linux (y las computadoras en general) tenemos el concepto de programas y procesos. Un programa es un blob de datos binarios que consta de una serie de instrucciones para la CPU y posiblemente otros recursos (imágenes, archivos de sonido, etc.) organizados en un paquete y normalmente almacenados en su disco duro. Cuando decimos que estamos ejecutando un programa, en realidad no estamos ejecutando el programa, sino una copia de él que se llama proceso. Lo que hacemos es copiar esas instrucciones y recursos del disco duro a la memoria de trabajo (o RAM). También asignamos un poco de espacio en la RAM para que el proceso almacene variables (para contener datos de trabajo temporales) y algunos indicadores para permitir que el sistema operativo (SO) administre y rastree el proceso durante su ejecución.


Por ejemplo, podría tener dos terminales abiertos y ejecutar el comando cp en ambos. En este caso, habría dos procesos cp actualmente existentes en el sistema. Una vez que terminan de ejecutarse, el sistema los destruye y ya no hay procesos que representen el programa cp.

Cuando estamos en la terminal tenemos un proceso `bash` ejecutándose para darnos el shell bash. Si iniciamos un script en ejecución, en realidad no se ejecuta en ese proceso, sino que inicia un nuevo proceso para que se ejecute en su interior.


## ¿Cómo los manejamos?

Ejecutar un script de Bash es bastante fácil. Otro término con el que se puede encontrar es ejecutar el script (que significa lo mismo). Antes de que podamos ejecutar un script, debe tener el permiso de ejecución establecido (por razones de seguridad, este permiso generalmente no está establecido de forma predeterminada). Si olvida otorgar este permiso antes de ejecutar el script, aparecerá un mensaje de error indicándole como tal.

```
#!/bin/bash
# Un ejemplo Bash script, por elvis
echo Hello World!
```

## Porqué el ./

Cuando simplemente escribe un nombre en la línea de comando, bash intenta encontrarlo en una serie de directorios almacenados en una variable llamada `$PATH`. Podemos ver el valor actual de esta variable usando el comando echo (aprenderá más sobre las variables en la siguiente sección).

```
echo $PATH
```

Si un programa o script no está en uno de los directorios de su $PATH, puede ejecutarlo indicándole a Bash dónde debe buscarlo. Para ello, incluya una ruta absoluta o relativa delante del nombre del programa o del script. Recordará que el punto (.) Es en realidad una referencia a su directorio actual. Suponiendo que este script está en mi directorio de inicio, también podría haberlo ejecutado utilizando una ruta absoluta.


## Variables Almacenes temporales de información

Una variable es un almacén temporal de un dato. Hay dos acciones que podemos realizar para las variables: 

* Establecer un valor para una variable.
* Leer el valor de una variable.

<details>
<summary>Ejemplo</summary>

```
#!/bin/sh
Similar a lo que teniamos arriba
h='Hola'
w='Mundo'
printf "%s %s!\n" ${h} ${w}

# similar a read
echo Hola $1

```
</details>


Aquí hay algunos puntos rápidos sobre sintaxis:

* Al hacer referencia o leer una variable, colocamos un signo $ antes del nombre de la variable.
* Al establecer una variable, dejamos fuera el signo $.
* A algunas personas les gusta escribir siempre los nombres de las variables en mayúsculas para que se destaquen. Sin embargo, es tu preferencia. Pueden estar todas en mayúsculas, todas en minúsculas o una mezcla.
* Una variable puede colocarse en cualquier lugar de un script (o en la línea de comando para el caso) y, cuando se ejecuta, Bash la reemplazará con el valor de la variable. Esto es posible porque la sustitución se realiza antes de que se ejecute el comando.

### Argumentos de la línea de comandos.

Cuando ejecutamos un programa en la línea de comandos, estará familiarizado con el suministro de argumentos después de él para controlar su comportamiento. Por ejemplo, podríamos ejecutar el comando `ls -l /etc`. `-l` y `/etc` son argumentos de línea de comando para el comando `ls`. Podemos hacer algo similar con nuestros scripts bash. Para hacer esto usamos las variables $1 para representar el primer argumento de línea de comando, $2 para representar el segundo argumento de línea de comando y así sucesivamente. El sistema los configura automáticamente cuando ejecutamos nuestro script.

### Otras variables especiales.

* $0: el nombre del script Bash.
* $1 - $9: los primeros 9 argumentos del script Bash. (Como se ha mencionado más arriba.)
* $#: Cuántos argumentos se pasaron al script Bash.
* $@: Todos los argumentos proporcionados al script Bash.
* $$: el ID de proceso del script actual.
* $USER: el nombre de usuario del usuario que ejecuta el script.
* $HOSTNAME: el nombre de host de la máquina en la que se ejecuta el script.
* $SECONDS: el número de segundos desde que se inició el script.
* $RANDOM: devuelve un número aleatorio diferente cada vez que se hace referencia a él.
* $LINENO: devuelve el número de línea actual en el script Bash.


### Exporting Variables

The idea is that variables are limited to the process they were created in. Normaly this isn't an issue but sometimes, for instance, a script may run another script as one of its commands. If we want the variable to be available to the second script then we need to export the variable.

<details>
<summary>script1.sh</summary>

```
#!/bin/bash

# ==== script1.sh =====

var1=blah
var2=foo

echo $0 :: var1 : $var1, var2 : $var2
export var1
./script2.sh

echo $0 :: var1 : $var1, var2 : $var2

```
</details>

<details>
<summary>script2.sh</summary>

```
#!/bin/bash

# ==== script2.sh =====

echo $0 :: var1 : $var1, var2 : $var2

var1=flop
var2=bleh
```
</details>

### Read

Si quisiéramos pedirle al usuario una entrada, usamos un comando llamado read. Este comando toma la entrada y la guardará en una variable


<details>
<summary>Ejemplos de read</summary>
```
#!/bin/bash
echo Hola con quien estoy hablando ?
read varname
echo Encantado de conocerte $varname
```

```
#!/bin/bash
read -p 'Username: ' uservar
read -sp 'Password: ' passvar
echo
echo Gracias $uservar, ahora tenemos sus datos de inicio de sesión
```
</details>


### Aritmética

`let` es una función incorporada de Bash que nos permite hacer aritmética simple. Sigue el formato básico:

```$ let <arithmetic expression>```

<details>
<summary>Ejemplos de let</summary>

```
#!/bin/bash

let a=5+4
echo $a # 9
let "a = 5 + 4"
echo $a # 9
let a++
echo $a # 10
let "a = 4 * 5"
echo $a # 20
let "a = $1 + 30"
```
</details>


Las expresiones básicas que puede realizar:

| +, -, \ *, / | suma, resta, multiplicar, dividir        |
| -------------| -----------------------------------------|
| var++        | Incrementar la variable var en 1   	  |
| var--        | Disminuye la variable var en 1 		  |
| % Módulo     | Devuelve el resto después de la división |
|			   |									      |


### If 

Un enunciado if básico efectivamente dice, si una prueba en particular es verdadera, entonces realice un conjunto de acciones dado. Si no es cierto, no realice esas acciones. Si sigue el formato siguiente:

```
if [ <some test> ]
then
	<commands>
fi
```

<details>
<summary>Ejemplos de If</summary>

```
#!/bin/bash

if [ $1 -gt 100 ] # (gt) comparacion de enteros https://tldp.org/LDP/abs/html/comparison-ops.html
then
	echo Hey that\'s a large number.
	pwd
fi
date
```
</details>

### If Else 

A veces queremos realizar un determinado conjunto de acciones si una afirmación es verdadera y otro conjunto de acciones si es falsa.

```
if [ <some test> ]
then
	<commands>
else
	<other commands>
fi
```

### If Elif Else

A veces podemos tener una serie de condiciones que pueden llevarnos a diferentes caminos.

```
if [ <some test> ]
then
	<commands>
elif [ <some test> ]
then
	<different commands>
else
	<other commands>
fi
```

### Boolean Operations

* and - &&
* or - ||

```
# and
if [ -r $1 ] && [ -s $1 ]
then
	echo This file is useful.
fi
```

<details>
<summary>Ejemplos de || </summary>
if [ $USER == 'bob' ] || [ $USER == 'andy' ]
then
	ls -alh
else
	ls
fi
```
</details>


### Case Statements

Elije un conjunto de comandos para ejecutar dependiendo de una cadena que coincida con un patrón particular, Podríamos usar una serie de declaraciones if y elif, pero eso pronto se volvería poco agradable. Afortunadamente, hay una declaración de caso que puede hacer las cosas más limpias.

```
case <variable> in
<pattern 1>)
	<commands>
	;;
<pattern 2>)
	<other commands>
	;;
esac

```

<details>
<summary>Ejemplos de case </summary>

```
#!/bin/bash

case $1 in
	uno)
		echo 1
	;;
	dos)
		echo 2
	;;
	tres)
		echo 3
	;;
	*)
		echo cualquier numero $1
	;;
esac
```
</details>

### Bucle while

Si bien una expresión es verdadera, siga ejecutando estas líneas de código. Tienen el siguiente formato:

```
while [ <some test> ]
do
	<commands>
done
```

<details>
<summary>Ejemplos de while </summary>

```
#!/bin/bash

counter=1
while [ $counter -le 10 ]
do
	echo $counter
	((counter++))
done

echo All done
```
</details>

### Bucle for

Lo que hace es decir para cada uno de los elementos en una lista dada, ejecutar el conjunto de comandos dado.

```
for var in <list>
do
	<commands>
done
```

<details>
<summary>Ejemplos de For </summary>

```
#!/bin/bash

names='Elvis Lucas Pedro'
for name in $names
do
	echo $name
done
echo All done
```
</details>


*Notas*

* [Operadores de comparación](https://tldp.org/LDP/abs/html/comparison-ops.html)

* [bash-scripting-tutorial](https://ryanstutorials.net/bash-scripting-tutorial/bash-user-interface.php#introduction)