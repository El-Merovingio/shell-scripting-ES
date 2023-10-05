# Ejemplos 2

## En este script vamos a verificar si un objeto existe en el Sistema Operativo y determinar el tipo de objeto
```
#!/bin/bash
ok="\033[32m" # verde
error="\033[31m" # rojo
advertencia="\033[33m" # amarillo
f="\033[0m" # concluye el escape de secuencia ANSI
read -p "Introduzca un objeto del Sistema Operativo: " obj

# Comprobar si el objeto existe
if [ -e "$obj" ]
then
    if [ -d "$obj" ]; then echo -e "El objeto ${advertencia} '$obj' ${f} es un directorio"
    elif [ -L "$obj" ]; then echo -e "El objeto ${advertencia} '$obj' ${f} es un acceso directo"
    elif [ -f "$obj" ]; then echo -e "El objeto ${advertencia} '$obj' ${f} es un archivo"
    fi
else
echo -e "El objeto ${error} '$obj' ${f} no existe"
fi
```

## Script mejorado
Utilizando `file -b` y un `if [[....]]`
```
#!/bin/bash
ok="\033[32m" # verde
error="\033[31m" # rojo
advertencia="\033[33m" # amarillo
f="\033[0m" # concluye el escape de secuencia ANSI
read -p "Introduzca un objeto del Sistema Operativo: " obj

# Comprobar si el objeto existe
if [ -e "$obj" ]
then
    if [ -d "$obj" ]; then echo -e "El objeto ${advertencia} '$obj' ${f}es un ${ok}directorio${f}"
    elif [ -f "$obj" ]
    then
        tipo=$(file -b "$obj")
        if [[ $tipo == "symbolic link"* ]]; then echo -e "El objeto ${advertencia} '$obj' ${f}es un ${ok}acceso directo${f}"
        else
        echo -e "El objeto ${advertencia} '$obj' ${f} es un ${ok}archivo${f}"
        fi
    fi
else
echo -e "El objeto ${error} '$obj' ${f} no existe"
fi
```
