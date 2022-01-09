# Variables de entorno

Las variables de entorno son comandos que usa el sistema para identificar una característica para el sistema operative y que los programas las puedan usar.

Para visualizar **todas** las variables de entorno se puede utilizar en comando `printenv` o con el comando `env`

Para visualizar una sola variable de entrno se puede usar el comando echo ${nombreDeVariable}

Ejemplo:

`echo $PWD` Muestra la carpeta actual, algo como `/home/SoyUsuario/carpeta/actual`

Algunas variables importantes son:

-   **$HOME**: Muestra la ubicacion de la carpeta principal del usuario

-   **$PATH**: Muestra las rutas donde estan los archivos ejecutables de los programas para poder realizar su ejecución sin tener que ir a buscar la carpeta

## Modificar alias

Para agregar un alias o una valriable de entorno se debe modificar el archivo .bashrc desde cualquier editor de texto (como nano). Este cambio es permanente hasta eliminar el comando, pero solo aplica para el usuario actual

`nano ~/.bashrc`

Para agregar a todos los usuarios, se debe modificar el archivo '/etc/profile':
`nano /etc/profile`

Para colcar el alias anteriormente descrito, se puede buscar si ya existe y modificarlo o colocarlo al final en un área 'especializada' para el alias creada por cada el usuario para tal fin. Es buena practica colocar un comentario sobre lo que trata el alias utilizando '#' como caracter para omitir la ejecución del comando

Ejemplo:

```
#Alias para ver todos los archivos
alias ls="ls --all --human-readable -l --indicator-style=classify"`
```

## Modificar o agregar variables de entorno

Las variables de entorno se modifican o agregan desde el archivo `~/.bashrc`. Su sintaxis es la siguiente:

`VARIABLE="dato"`

Por ejemplo para la variable `PATH` a la que le agregaremos la ruta `~/cositas` podriamos ejecutar lo siguiente:

1. `nano ~/.bashrc` para poder editar el archivo
2. Ir al final del documento
3. escribir `PATH="$PATH:~/cositas"`
4. Salit y guardar cambios (Se sale con CTRL + X, en la parte inferior pregunta si guardar cambios y el nombre del archivo después)

A tener en cuenta en $PATH:~/cositas es que:

**$PATH**: Es la varibale de sistema PATH que esta establecida
**:** : Concantena el texto que sigue
**~/cositas**: El nuevo texto

Para inicializar la variable sin necesidad de salir de la terminal, se puede escribir `source .bashrc`
