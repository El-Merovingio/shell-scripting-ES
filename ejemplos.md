# Ejemplos y código para programación en Shell

``` shell
#Ejemplo 1
#!/bin/bash
name=azucar
echo "La palabra es $name y contiene ${#name} caracteres"
```

``` shell
#Ejemplo 2
#!/bin/bash
read -p "Introduzca un valor" var
if [ "$var" -gt 0 ]; then echo "SI"; else echo "NO'
fi
#tenemos que meter valores positivos o negativos
```

``` shell
#Ejemplo 3
Tres:
#!/bin/bash
colors="rojo negro blanco azul amarillo"
for i in $colors
do
	echo $i
done
```

``` shell
#Ejemplo 4
#En el siguiente ejemplo podemos ver que con una coma, convertimos solo el primer carácter en minúscula y con doble coma ,, convertimos todo en minúscula
#!/bin/bash
var=JuLIOjaVIERIGlesias
echo ${var,,}
```

``` shell
#Ejemplo 5 - Para mayúsculas
#!/bin/bash
var=JuLIOjaVIERIGlesias
echo ${var^^}
```

``` shell
#Ejemplo 6 - Este es para pensar
#!/bin/bash
read -p "Introduzca un numero: " var1
echo $(( var2 = var1<20?1:0))
#si var1 es menor a 20, asigna 1 caso contrario asigna 0, también se puede hacer con un if -lt, pero esta manera es interesante también
```

``` shell
#Ejemplo 7 - Qué pasa si creamos un script 
#!/bin/bash
echo ""Linux es hermoso""
```

``` shell
#Ejemplo 8 - Entonces, si queremos que nos salga la comilla doble tendríamos que hacer
#!/bin/bash
echo "\"Linux es hermoso\""
```

``` shell
#Ejemplo 9 - Y si hacemos
#!/bin/bash
echo "\"Linux es hermoso"\"
#Nos dará el mismo resultado
#Por ejemplo si hacemos ls --help | grep "-U" no nos dará lo mismo que ls --help |grep "\-U"
```

``` shell
#Ejemplo 10 - Otro ejemplo
#!/bin/bash
var = test1\ test2\ test3
echo $var
#si no ponemos la \, nos sale test2 command not found

#Esto que hace en la consola bash?
echo \${test1,test2,test3}\$
#echo {0..9}
```

``` shell
#Ejemplo 11 - Vemos que hace el siguiente script
#!/bin/bash
var1=1
var2=2
{
var1=11
var2=12
}
echo "$var1 $var2"
```

``` shell
#Ejemplo 12 - Condiciones
#!/bin/bash
read -p "Introduzca un numero: " var
if [ $var -gt 0 ] || [ $var -eq 10 ]
then
	echo "una o mas condiciones son verdaderas"
else
	echo "ambas condiciones son falsas"
fi


#Para entender el let. Por ejemplo
let "num -= 10" es lo mismo que num = num - 10
```

``` shell
#Ejemplo 13 en script
#!/bin/bash
var=
let "var += 10"
echo $var
let "var = var +10"
echo $var
```

``` shell
#Ejemplo 14 - Una manera de sustituir
#!/bin/bash
num=10
var=${num/10/A}
echo $var
```

``` shell
#Ejemplo 15 - Comparaciones entre archivos
#!/bin/bash
NO_OF_ARGS=2
E_BADARGS=85
E_UNREADABLE=86

if [ $# -ne "$NO_OF_ARGS" ]
then
	echo "Utilizar `basename $0` archivo1 archivo2"
exit $E_BADARGS
fi

if [[ ! -r $1 || ! -r $2 ]]
then
	echo "Los archivos no son reales"
exit $E_UNREADABLE
fi

cmp $1 $2 &> /dev/null #compara los archivos y redireccionamos a null porque no nos interesa lo que nos diga el mensaje

if [ $? -eq 0 ]
then
	echo "Los archivos iguales"
else
	echo "Los archivos no son iguales"
fi
exit 0

#Con las condiciones se pueden hacer if dentro de otros

if [ ]
	then
		if [ ]
			then
		fi
fi

#-e verifica si lo introducido existe poir ej -e /var
#-f devuelve verdadero si el objeto es un archivo
#-s true si el valor no es 0, es decir, si hay algo en el
#-r true si el usuario q ejecuta tiene permiso de lectura en el objeto
#-x true si el usuario q ejecuta tiene permiso de ejecucion
#-w true si write
#! reverse el resultado
#Los exit codes
#NO_OF_ARGS=2
#E_NOARGS=65
#E_BADARGS=85
#E_UNREADABLE=86
#E_NOFILE=87
#E_SIZE=89
```

``` shell
#Ejemplo 16 - VARIABLES
#!/bin/bash
for n in {0..5}
do
	echo "BASH_VERSINFO[$n] = ${BASH_VERSINFO[$n]}"
done
```

``` shell
#Ejemplo 17 - Otro ejemplo de variables 
#!/bin/bash
ROOT_UID=0
echo -n "Tu eres: "
if [[ $UID -eq $ROOT_UID ]]
then
	echo "root. TU \$UID = $UID"
else
	echo "usuario. TU \$UID = $UID"
fi
```

``` shell
#Ejemplo 18 - Variable función
#!/bin/bash
unafuncion()
{
	echo "El nombre de esta funcion es $FUNCNAME"
}
unafuncion
echo "Fuera de la funcion \$FUNCNAME"
```

``` shell
#Ejemplo 19 - Mas variables
#!/bin/bash
if [[ $HOSTNAME && $USER && $HOME ]]
then
	echo "HOSTNAME ES: $HOSTNAME"
	echo "El usuario es: $USER"
	echo "HOME es: $HOME"
	echo "Las variables estan establecidas"
else
	echo "Las variables no estan establecidas"
fi
```

``` shell
#Ejemplo 20 - Otro ejemplo
#!/bin/bash
colores1="rojo-negro-azul"
colores2="rojo+negro+azul"
echo "Trabajando con IFS=-"
IFS=-
echo $colores1
echo $colores2
echo "Trabajando con IFS=+"
IFS=+
echo $colores1
echo $colores2

#Otras variables
echo $LINENO
echo $OLDPWD
echo $PWD
echo $OSTYPE
echo $BASHPID
echo $HOSTTYPE
echo $IFS
echo $IGNOREOF
echo $LC_COLLATE
echo $PIPESTATUS
echo $PPID
echo $PROMPT_COMMAND
echo $PS1
echo $PS2
echo $PS3
echo $PS4
echo $REPLY
echo $SECONDS
echo $SHELLOPTS
echo $SHLVL
echo $TMOUT
echo $TMOUT
echo $UID
```

``` shell
#Ejemplo 21 - Ejemplos mas
#!/bin/bash
read -p "Cuanto es 1 + 1: "
echo "Tu respuesta es $REPLY"
echo "La respuesta verdadera es 2"
```

``` shell
#Ejemplo 22 - Otro ejemplo mas
#!/bin/bash
LIMIT_TIME=12
TIME_INTERVAL=3
echo "Este script `echo $0` va a correr por $LIMIT_TIME segundos"
echo "Presione Ctrl-c para salir antes del tiempo limite"
while [[ $SECONDS -le $LIMIT_TIME ]]
do
	echo "Este script `echo $0` ha corrido por $SECONDS segundos"
	sleep $TIME_INTERVAL
done

#declare, modifica las propiedades de una variable
#-r readonly
#-i integer
#-a array
#-f function(s)
#-x export
```

``` shell
#Ejemplo 23 - Generar numeros random
#!/bin/bash
MAX=10
i=1
while [[ $i -le $MAX ]]
do
	n=$RANDOM
	echo $n
	let "i +=1"
done
```

``` shell
#Ejemplo 24 - Bucle for
#!/bin/bash
for i in 1 2 3 4 5
do
	echo "Bucle externo $i ....."
	for j in 1 2 3
	do
		echo "Bucle interno $j "
	done
done
```

``` shell
#Ejemplo 25 - Bucle while
#!/bin/bash
a=0
while [[ a -lt 10 ]]
do
	read -p "Introduzca un valor igual o superior 10: " a
	echo "Introdijiste $a, dije que introduzcas 10"
done
```

``` shell
#Ejemplo 26 - Bucle until
#!/bin/bash
until [[ $p = fin ]]
do
	read -p "Introduzca la palabra fin para salir: " p
	echo "Introdujiste $p"
done
```

``` shell
#Ejemplo 27 - Break y continue
#!/bin/bash
echo "Introduzca cualquier numero que sea menor a 10 y que no sea el numero 2"
while [[ $n -le 9 ]]
do
	read -p "Numero: " n2
		if [[ $n2 -gt 10 || $n2 -eq 2 ]]
		then
			break
		else
			continue
		fi
done

#En un continue, se puede poner por ejemplo continue 3, en un bucle digamos….. practicar y practicar
```

``` shell
#Ejemplo 28 - Case
#!/bin/bash
read -n 1 -p "Introduzca un caracter: " c
case $c in
[[:lower:]] ) echo "El caracter introcido es minuscula";;
[[:upper:]] ) echo "El caracter introcido es mayuscula";;
[0-9] ) echo "El caracter introcido es un numero";;
* ) echo "El caracter introcido es un caracter especial";;
esac
exit 0
```

``` shell
#Ejemplo 29 - Select
#!/bin/bash
PS3="Elija un color: "
select color in "blanco" "azul" "amarillo" "verde" "celeste" "beige" "dorado" "negro"
do
	echo "Elegiste este color: $color"
	break
done
```

``` shell
#Ejemplo 30 - Printf
#!/bin/bash
declare -r PI=3.1415926
printf "EL primer decimal de PI es %1.1f\n" $PI
printf "EL segundo decimal de PI es %1.2f\n" $PI
printf "EL tercer decimal de PI es %1.3f\n" $PI
printf "EL cuarto decimal de PI es %1.4f\n" $PI
printf "EL quinto decimal de PI es %1.5f\n" $PI
```

``` shell
#Ejemplo 31 - Read
#!/bin/bash
arriba=$'\x1b[A'
abajo=$'\x1b[B'
izquierda=$'\x1b[D'
derecha=$'\x1b[C'

read -s -n3 -p "Presione una tecla de flecha: " flecha
case $flecha in
	$arriba) echo "Presionaste arriba";;
	$abajo) echo "Presionaste abajo";;
	$izquierda) echo "Presionaste izquierda";;
	$derecha) echo "Presionaste derecha";;
Esac
```

``` shell
#Ejemplo 32 - eval y set
#!/bin/bash
if [[ ! -z $1 ]]
then
	proceso="ps -e | grep $1"
fi
eval $proceso

#set Nos permite modificar el comportamiento del interprete de ordenes que utiliza el script que vamos a ejecutar o el terminal en el que estemos trabajando. También se pueden poner los valores en la definición del script: #!/bin/bash -a 
#set -a A partir de este momento, las variables que se declaren se exportan automaticamente a globales sin necesidad de ejecutar "export variable" 
#set -b Si disponemos de una aplicacion que se ejecuta en segundo plano, nos reporta el estado una vez haya terminado. 
#set -vx Muestra las lineas que va ejecutando nuestra script. Para desactivar-lo: set +xv 
#set variable=valor Se crea una variable local 
#export variable Se pasa la variable local a global 
#echo ${variable} Muestra la variable
```

``` shell
#Ejemplo 33 - set
Primer ejemplo
#!/bin/bash
var="1 2 3"
echo $var
unset $var
echo $var

#Segundo ejemplo
#set +o history hard to keep turned off
#From: 	jidanni
#Subject: 	set +o history hard to keep turned off
#Date: 	Sun, 24 Feb 2008 07:31:06 +0800
```

``` shell
#Ejemplo 34 - set + o history en la parte inferior de .bashrc y confirmamos que es realmente lo último que se ejecutó 
$ bash -x
#Pero luego hacer
$ set -o|grep history
#va a mostrar que 
#!/bin/bash
set +o history
set -o history
echo "Antes de establecer los parametros"
echo "\$1 = $1"ha vuelvo de nuevo
echo "\$2 = $2"
set `echo "tres cuatro"`
echo "Despues de establecer los parametros"
echo "\$1 = $1"
echo "\$2 = $2"
```

``` shell
#Ejemplo 35 - OTRO EJEMPLO para entender mejor
#!/bin/bash
var="Julio Iglesias"
echo $var
set -- $var #(menos menos)
echo $var

#eval es un comando integrado en Linux o Unix. El comando eval se usa para ejecutar los argumentos como un comando de shell en el sistema Unix o Linux. El comando Eval es muy útil cuando tiene un comando unix o linux almacenado en una variable y desea ejecutar ese comando almacenado en la cadena. El comando eval primero evalúa el argumento y luego ejecuta el comando almacenado en el argumento.```

``` shell
#Ejemplo eval
#Tomará un argumento y construirá un comando de él, que será ejecutado por el shell. Este es el ejemplo de la página de manual:

foo=10 x=foo
y='$'$x
echo $y
$foo
eval y='$'$x
echo $y

#Resultado sera 10

#En la primera línea define $ foo con el valor '10' y $ x con el valor 'foo'.
#Ahora defina $ y, que consiste en la cadena '$ foo'. El signo de dólar se debe escapar con '$'.
#Para verificar el resultado, echo $ y.
#El resultado será la cadena '$ foo'
#Ahora repetimos la tarea con eval. Primero evaluará $ x a la cadena 'foo'. Ahora tenemos la declaración y = $ foo, que se evaluará a y = 10.
#El resultado de echo $ y ahora es el valor '10'.
```

``` shell
#Ejemplo 36 - Mas de eval
COMMAND="ls -lrt"
eval $COMMAND

#OTRO eval
Para imprimir el valor de la variable que de nuevo es variable con el valor asignado
$a=10
$b=a
$c='$'$b (nota: el signo de dólar se debe escapar con '$')
$echo $c
salida:
$a
$eval c = '$' $ b
$echo $ c
output:
10
```

``` shell
#Ejemplo 37 - Otro ejemplo de eval y set
#!/bin/bash
var="1 2 3"
echo $var
set -- $var
i=1
while [[ $i -le $# ]]
do
echo -n "\$$i = "
eval echo \$$i
(( i++ ))
done
set --
echo "\$1 = $1"
echo "\$2 = $2"
echo "\$3 = $3"

#getopts
#El comando getopts es un comando incorporado Korn / POSIX Shell que recupera opciones y argumentos de opciones de una lista de parámetros.
#Es útil para analizar los argumentos que son pasados a través de la linea de comandos.
#Para poder entender, primer ir ejecutando la parte de awk y sus resultados y luego construir el script```
```

``` shell
#Ejemplo 38
#!/bin/bash
while getopts :dm option
do
	case $option in
		d) d_option=1
		;;
		m) m_option=1
		;;
		*) echo "Utiliza: dm"
	esac
done

dia=`date | awk '{print $1 " " $2}'`
if [[ ! -z $d_option ]]
then
	echo "La fecha es: $dia"
fi
mes=`date | awk '{print $3}'`
if [[ ! -z $m_option ]]
then 
	echo "El mes es: $mes"
fi
shift $(($OPTIND - 1))
Ejecutar 
./script -d
./script -m
./script -d -m
 
#shopt
#Ejemplo Tiene varias opciones, por ejemplo si ejecutamos shopt vamos a ver las opciones que tiene configurado```
#Ejemplo Luego, si queremos establecer algún parámetro es con shopt -s y si queremos quitar (unset) es con shopt -u ```
#Ejemplo 
shopt -s cdspell
#vamos a 
cd /
#hacemos 
cd rout o cd etcc o cd vaar #y este entrara al directorio correctamente escrito

#El comando disown es para matar procesos en segundo plano, hay que investigar

#Este ejemplo es interesante
#!/bin/bash
ls ()
{
	echo "Esta vez no funcionare"
}

ls

read -p "Presione enter para continuar"

command ls /

#Analizar resultado
```

``` shell
#Ejemplo 39 - Ejemplo con grep
#!/bin/bash
E_NOPATTERN=71
DICT=/usr/share/dict/words
if [[ -z $1 ]]
then
	echo
	echo "Utilice: "
	echo "`basename $0` \"\patron,\""
	echo "donde \"patron\"esta en el form"
	echo "ooo..oo.o..."
	echo
	echo "Las letras \"o\" ya las conoces"
	echo "y los periodos estan perdiendo letras"
	echo "Las letras y periodos pueden estar en cualquier posicion"
	echo "por ejemplo: w...i....n"
	echo
	exit $E_NOPATTERN
fi
grep ^"$1"$ "$DICT" #el ^ coincide con el comienzo de la linea, y el $ que viene luego de $1"$ coincide con el final de la linea, grep va a buscar ese patron ^variable$ en el archivo $DICT
#Ejecutar  por ejemplo>
#./script wo.d
#./script ..w.o.
#./script ab.ol....y
#./script J...o
#./script Arg......

#Analizar resultados.

#Veamos un poco mas extendido a ls
ls -l /etc/ld?*
ls -l /etc/[fw]* #todos los archivos que comiencen con las letras f o w
ls -l /var/[ms]*
ls /etc/[e-q]* #busca q comiencen con e o q y cualquier letra que este entre ellos en el alfabeto
ls -l /etc/{w*,*ss*,*up*,s*} #varias condiciones, que muestre los objetos que comienzan con w, que en el medio tengan ss, up, que comiencen con s. Todas las condiciones va a buscar
```

``` shell
#Ejemplo 40 - Expresiones regulares con sed extendidas
#^ para buscar al principio del archivo
#Ej 
sed ^root /etc/passwd
#$ al final del archivo
#Ej
sed bash$ /etc/passwd

sed 's/patrón/reemplazo/' fichero

#sed [-f|e|n] → 'lista de comandos de ed' file/s
#-f → Lee los comandos ed desde un fichero. El nombre del fichero a continuación de la opción es el que leerá.
#-e → Coloca varias órdenes de edición en la propia línea (un -e por cada orden).
#-n → Suprime la salida normal de todas las líneas del fichero y sólo aparecen en la salida las líneas especialmente solicitadas con una operación de imprimir p o l (como p pero muestra los caracteres especiales). Sin la opción -n una salida p (ya la veremos posteriormente) duplica las líneas seleccionadas.

#Si usamos "$VAR", sed utiliza el valor de la variable VAR pero '$VAR' lo tomaría literalmente como $VAR.
```

``` shell
#Ejemplo 41 - Ejemplo para expresiones regulares extendidas con sed
#!/bin/bash
E_BADARGS=65
if [ $# -eq 0 ]
then
	echo Utilice : `basename $0` archivo
	exit $E_BADARGS
else
	for i
	do
		sed -e '1,/^$/d' -e '/^$/d' $i #elimina los blank lines y la primera sed elimina desde el principio luego de la primera linea blank
	done
fi

#Luego crear un archivo por ejemplo.
echo >> 1.txt
echo Hola >> 1.txt
echo >> 1.txt
echo >> 1.txt
echo Julio >> 1.txt
echo Javier >> 1.txt
echo Iglesias >> 1.txt

#al ejecutar el ./script 1.txt
#nos eliminara las líneas blank y quedaría solo 
#Julio
#Javier
#Iglesias
```

``` shell
#Ejemplo 42 STDOUT (Standard Output) STDIN STRERR
#El comando exec puede utilizarse para ejecutar otro programa que reemplace el shell actual. En el Listado 13 se inicia un shell bash secundario y luego se utiliza exec para reemplazarlo por un shell Korn. Luego de salir del shell Korn, usted vuelve al shell bash original (en este ejemplo, PID 2852).
#!/bin/bash
echo 12345 > prueba.txt #redirijimos este numero
exec 3<>prueba.txt #abrimos el archivo y asignamos un file descriptor (3)
read -n 2 <&3 #Aca necesitamos solamente leer dos caracteres desde el archivo
echo -n . >&3 #luego escribimos un punto en esa parte
exec 3>&- #cerramos el archivo 
cat prueba.txt
```

``` shell
#Ejemplo 43 - OTRO ejemplo stdout, stdin stderr

#!/bin/bash
E_FILE_ACCESS=70 #que el archivo no existe es el 70
E_BADARGS=71 #por ahi el archivo no existe o no tenemos permiso para abrir
if[ ! -r "$1" ] #no es leible
then
	echo "No se puede leer desde el archivo especificado" 
	echo Utilice `basename $0 input-file output-file
	exit $E_FILE_ACCESS #exit status
fi
if [ -z "$2" ] #revisa si el param no pasa el script
then
	echo "Especifique un archivo de salida"
	echo Utilice `basename $0 input-file output-file
	exit $E_BADARGS
fi
exec 4<&0 #significa que el descriptor del archivo de enlace (link) 4 con la entrada esta ok (estable)
exec < $1 #lee desde el archivo de entrada, este es el primer argumento al script

exec 7>&1 #entonces el numero de file descriptor es 7, con salida estandar
exec > $2 #segundo archivo, redireccion al segundo archivo

tr a-z A-Z #translitera

exec 1>&7 7>&- #restaura la salida estandar y y cierra el descriptor de archivo 7
exec 0>&4 4<&- #restaura el input estandar y cierra el descriptor de archivo 4
```

``` shell
#Ejemplo 44 - FUNCIONES
#!/bin/bash
funcion1 ()
{
	echo "Esta es la funcion 1"
}
funcion2 ()
{
	echo "Esta es la funcion 2"
}

funcion1
funcion2
```

``` shell
#Ejemplo 45 - Otra funcion introduciendo params
#!/bin/bash
_()
{
        echo Hola me llamo $FUNCNAME
        echo EL parametro 1 es $1
        echo El parametro 2 es $2
}

var1=10
var2=20
_ $var1 $var2
```

``` shell
#Ejemplo 46 - ARRAYS```

``` shell
#Ejemplo 1
#!/bin/bash
declare -a arr
arr=( 10 20 30 40 50 60)
echo -e "${arr[0]}\n${arr[1]}\n${arr[2]}\n${arr[3]}\n${arr[4]}"
```

``` shell
#Ejemplo 47 - EJEMPLO2
#!/bin/bash
a=algo1234
echo ${a[*]}
echo ${a[0]}
echo ${a[1]}
echo ${a[@]}
```

``` shell
#Ejemplo 48 - EJEMPLO3
#!/bin/bash
arr=( cero uno dos )
echo ${arr[0]}
echo ${#arr[0]} #el size del primer elemento
echo ${#arr[*]} #el size del array
```

``` shell
#Ejemplo 49 - EJEMPLO4
#!/bin/bash
declare -a colores
echo "Tus colores favoritos separados por espacio: "
read -a colores
count=${#colores[@]} #size del array
i=0
while [ "$i" -lt "$count" ]
do
	echo ${colores[$i]}
	(( i++ ))
done

echo ${colores[*]}

unset colores[2] #hace un unset al tercer elemento
echo ${colores[*]}

unset colores
echo "no hay colores. se fueron los colores"
echo ${colores[*]}
```

``` shell
#Ejemplo 50 - EJEMPLO5, ORDENAR ALFABETICAMENTE
#!/bin/bash
swap()
{
	local tmp=${colores[$1]}
	colores[$1]=${colores[$2]}
	colores[$2]=$tmp
return
}
declare -a colores
colores=(rojo amarillo verde azul blanco)
size=${#colores[@]}
	for (( last = $size -1 ; last > 0 ; last-- ))
do
	for (( i=0 ; i < last ; i++ ))
	do
		[[ "${colores[$i]}" > "${colores[$((i+1))]}" ]] && swap $i $((i+1))
	done
done

echo ${colores[@]}

```

``` shell
#Ejemplo 51 - OR AND Y LISTAS, EJEMPLO PARA "ENTENDER"
#!/bin/bash
a=1
b=2
c=3
[ "$a" -gt "$b" ] || [ "$c" -gt "$b" ] || ( (( c += a + b )) ;  echo "$c" )

```

``` shell
#Ejemplo 52 - DEBUGGING
#EJEMPLO1
#!/bin/bash
for n in 1 2 3 4
do
	echo "$n"
exit 0

#AL ejecutar

$echo $? muestra el exit status,en nuestro caso 2 que algo falta "missing"

#Ahora el sh -n o bash -n 
 
#podemos ver con bash --h o sh --h mas información

#Si ejecutamos con sh +x script
 

#Nos d mas clara la idea de lo que esta pasando
```

``` shell
#Ejemplo 53 - OTRO EJEMPELO 
#!/bin/bash
a=3
if[ $a -gt 0 ]
then
	echo $a
fi
```

``` shell
#Ejemplo 54 - EJEMPLO CON DEBUG en el código
#!/bin/bash
trap 'echo "listando variables: a = \"$a\""' DEBUG
a=3; line=$LINENO
echo "\$a inicializada a $a en la linea $line"
let "a *= 2"; line=$LINENO
echo " \$a multiplicado por dos en la linea $line "
