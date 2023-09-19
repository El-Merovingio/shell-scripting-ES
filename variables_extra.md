# Ejemplos
A continuación se muestran un par de ejemplos en los que se utilizan llaves para delimitar explícitamente el nombre de la variable y concatenarlo con otros caracteres o variables:
## Concatenando una variable con una cadena:
``` bash
nombre="Julio"
echo "Mi nombre es ${nombre} Iglesias."
echo "Mi nombre es $nombre Iglesias."
```

## Concatenando una variable con caracteres adicionales:
``` bash
contar=10
echo "Tienes ${contar} nuevos mensajes."
```

## La sintaxis $(...), conocida como sustitución de comandos, le permite capturar la salida de un comando y utilizarla como valor en su script de shell. A continuación se muestra un ejemplo que demuestra el uso de la sustitución de comandos:
``` bash
fecha_actual=$(date +%Y-%m-%d)
echo "Hoy es ${fecha_actual}."
```
