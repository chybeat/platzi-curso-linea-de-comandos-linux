# Alias

Los alias son comandos de comandos mas complejos. Por complejos se refere a que en una palabra mas corta se empleen parametros de uno o mas comandos.
Con `type` podemos saber si un comando es alias (un comando mas complejo o con parametros), un binario o si viene dentro del shell

Ejemplos:
`type cd` Muestra: `cd is a shell builtin` (viene dentro del shell de linux)
`type mkdir` Muestra: `mkdir is /usr/bin/mkdir` (Es un binario)
`type tree` Muestra: `mkdir is /usr/bin/tree` (Es un binario)
`type git` Muestra: `mkdir is /usr/bin/git` (Es un binario)
`type ls` Muestra: `` ls is aliased to `ls --color=auto' `` (Es un alias de ls --color=auto )
En este ultimo caso "color" hace que al escribir ls siempre se muestren en colores dependiendo del tipo de elemento (archivos y directorios)

## Crea un alias

Para crear un alias se debe escribir la palabra 'alias', luego el nombre del alias, un igual y por último el comando entre comillas

Ej: Crear el alias la, para que muestre una lista humanamente amigable y que al final de cada directorio agregue un "/" (clasificación)

El codigo a escribir es el siguiente:

`alias dir="ls --all --human-readable -l --indicator-style=classify"`

## Duración de un alias

Los alias son temporales, solo puede ser usados mientras se tenga abierta la ventana acutal del shell

## Alias persistentes

Para agregar un alias se debe modificar el archivo .bashrc desde cualquier editor de texto como nano

`nano ~/.bashrc`

Para colcar el alias anteriormente descrito, se puede buscar si ya existe y modificarlo o colocarlo al final en un área 'especializada' para el alias creada por cada el usuario para tal fin. Es buena practica colocar un comentario sobre lo que trata el alias utilizando '#' como caracter para omitir la ejecución del comando

Ejemplo:

```
#Alias para ver todos los archivos
alias dir="ls --all --human-readable -l --indicator-style=classify --color=auto"`
```

Otra opción es decirle a Linux que ejecute (si existe) un archivo especifico para alias con el siguiente comando en el archivo `.bashrc` (puede ya venir escrito)

```
#Bash custom alias definitions
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

**\*Este código es persistente solo para el usuario actual**

Luego se debe crear el archivo. Se puede usar `touch ~/.bash_aliases` y luego editarlo (puede usarse `nano ~/.bash_aliases`) para agregar el alias dentro del archivo

Un alias puede ser tan largo como se requiera y utilizar redirecciones y operadores de ejecución. El siguiente ejemplo que usa los parametros que se le pueden dar a `ls`, muestra todos los archivos (a), en una lista larga (l), con tamaños de archivo facilmente entendibles (h) y al final de cada elemento le coloca una clasificación (/ para carpetas, \*para archivos, etc.) y tambien "ordena" o muestra primero los directorios, luego los archivos, luego los enlaces y después otros tipos de recursos que pueden existir en el sistema de archivos de linux (los más usados); al final muestra el total de uso en disco (tamaño total de archivos), todo gracias a que se enlaza el resultado con el comando grep.

    alias dir="ls -ahlF | grep '^d'; ls -ahlF | grep '^-'; ls -ahlF | grep '^l'; ls -ahlF | grep '^c'; ls -ahlF | grep '^b'; ls -ahlF | grep '^s'; ls -ahlF | grep '^p'; ls -ahlF | grep '^total'"

Se repite el comando `ls` tantas veces como tipos de recursos existen (archivos, directorios, enlaces, etc), pues grep imprime SOLO el resultado de las lineas que comienzan (^) por la letra de cada tipo de recurso, por ello hay que hacerlo, en secuencia por cada tipo de recurso, incluyendo la palabra total al final en una ultima busqueda.
