# Permisos

Los permisos para un archivo o carpeta son la posiblidad de realizar una de las 3 operaciones que se pueden realizar con para o en un archivo:

Escritura (**w**rite): Quiere decir que un archivo o directorio puede ser escrito o modificado

Lectura (**r**ead): Quiere decir que un archivo o directorio puede ser leido

Ejecución (e**x**ecute): Quiere decir que el archivo o directorio puede ser utilizado para ejecutarse como programa/script o en el caso de un directorio utilizarse para la ejecución o solicitud de recursos (imagenes, scripts, etc) desde un programa o script.

Para entender más de todo esto tomaremos como ejemplo el resultado del siguiente comando `ls -lh index.tml`

    -rwxrwxrwx 1 usuario elParche 1558 Dec 1 01:16 index.html

Expliquemos cada uno de los apartes que nos arroja este comando

## El primer caracter

En el primer caracter en `-rwxrwxrwx` (el guión) indica el tipo de recurso. Para este caso se refiere a un archivo, pero para esta posición existen las siguientes posibilidades:

| Caracter | Tipo de recurso         |
| -------- | ----------------------- |
| -        | Archivo                 |
| d        | Directorio              |
| l        | Enlace simbólico        |
| c        | Dispositivo de carácter |
| b        | Dispositivo de bloques  |
| s        | Conexiones locales      |
| p        | Conexiones              |

## Los 9 caracteres de permisos

Inmediatamente después venen los permisos: `rwxrwxrwx`. Cada caracter es un permiso y cada grupo de 3 caracteres le perteneces a un tipo de usuario.

| Tipo de usuario     | Descripción                                                         |
| ------------------- | ------------------------------------------------------------------- |
| Owner (propietario) | El usuario que creó el archivo                                      |
| Groups (grupos)     | Grupos de usuarios[^1]                                              |
| Other (otros)       | Cualquier usuario que no sea el creador o no haga parte de un grupo |
| All (todos)         | Todos los tipos de usuario (comodin en comandos de permisos)        |

[^1]: Los grupos son conjuntos de cuentas de usuarios que comparten ciertos permisos.

En ese orden de ideas `rwxrwxrwx` especifica que:

Usuario: puede leer, puede escribir y puede ejecutar index.html (u+rwx)
Grupo: puede leer, puede escribir y puede ejecutar index.html (g+rwx)
Otros: pueden leern pueden escribir y pueden ejecutar el archivo index.html (o+rwx)

Leído de otro modo se podría decir:

Todos: pueden leer, pueden escribir y pueden ejecutar el archivo index.html (a+rwx)

Cuando un permiso es denegado a un grupo se representa con un "-" (guión).

Ejemplo:

Supongamos que el archivo index.html tiene los siguientes permisos:

`rwxrw-r--`

Esto quiere decir que:

Usuario: puede leer, puede escribir y puede ejecutar index.html (u+rwx)
Grupo: puede leer, puede escribir y puede ejecutar index.html (g+rwx)
Otros: pueden leern pueden escribir y pueden ejecutar el archivo index.html (o+rwx)

## El número de enlaces fisicos

En el resultado trabajado para index.html es el numero que está luego de los permisos:

-rwxrwxrwx **_1_** usuario elParche 1558 Dec 1 01:16 index.html

Estos enlaces son etiquetas que se le colocan a un archivo o directorio para que haga referencia a otro archivo o directorio (solo se admiten enlaces de archivo a archivo o de directorio a directorio). Si se colocó un enlace simbolico hacia el archivo 'index.html' desde el archivo 'editMe.html', editMe.html no tendrá en sí información salvo la referencia de ubicación de index.html y permisos de editMe.html. Al cambiar su contenido, cambiará realmente en index.html.

El número de enlaces físicos hace referencia a estos archivos simbólicos incluyendose a sí mismo, si el número fuera 3, querría decir que hay 2 enlaces simbólicos de ese archivo.

Hay que tener en cuenta que los permisos que se cambien a un enlace simbolico **solo** se cambian a la carpeta o directorio de destino, no al enlace.

## Creador y grupos para el archivo

En el ejemplo el creador del archivo es 'usuario' y el grupo de ese usuario es 'elParche', estos solo hacen referencia para saber quienes tienen privilegios o permisos para ese archivo.

## Binario y octal

Los permisos al guardar en binario tienen 8 posibilidades para ello como se muestra en la siguiente tabla:

| r   | w   | x   | Binario  | Valor decimal | Permiso                        |
| --- | --- | --- | -------- | ------------- | ------------------------------ |
| 0   | 0   | 0   | 00000000 | 0             | Ningun permiso                 |
| 0   | 0   | 1   | 00000001 | 1             | Solo ejecución                 |
| 0   | 1   | 0   | 00000010 | 2             | Solo escritura                 |
| 0   | 1   | 1   | 00000011 | 3             | Escritura y Ejecución          |
| 1   | 0   | 0   | 00000100 | 4             | Solo lectura                   |
| 1   | 0   | 1   | 00000101 | 5             | Lectura y ejecución            |
| 1   | 1   | 0   | 00000110 | 6             | Lectura y escritura            |
| 1   | 1   | 1   | 00000111 | 7             | Lectura, escritura y ejecución |

El modo octal simplemente hace referencia a las ocho posibilidades dependiendo de su valor binario y convirtiendolo en decimal, es decir si tiene un permiso se coloca 1 y si no lo tiene se toma 0,siguiendo el orden de los permisos al asignarle un permiso a un archivo y pasandolo de binario a decimal ese número representa los permisos otorgados y/o denegados para un archivo.

### ¿Y los tipos de usuario en el modo octal?

Los tres grupos de usuario van consecutivamante, usando el modo octal de los permisos simplmenete los permisos se asignan con el número de permiso consecitvamente

Ejemplo:

`rwxrwxrwx` = 777

`rwxrw-r--` = 764

## Cambio de permisos

Los permisos en linux se pueden cambiar con el comando chmod o chowner, las siguientes tablas mustran los modos sombólicos para los grupos o tipos de usuario y los permisos

| grupo   | Símbolo | Conocido como                |
| ------- | ------- | ---------------------------- |
| Usuario | u       | Owner, creador               |
| Grupo   | g       | grupos, tipos de usuario     |
| Otros   | o       | Mundo, world, cualquier otro |
| Todos   | a       | Los grupos anteriores        |

| Símbolo | Permiso   |
| ------- | --------- |
| r       | Lectura   |
| w       | Escritura |
| x       | Ejecución |

| Valor octal | Permiso                        |
| ----------- | ------------------------------ |
| 0           | Ningun permiso                 |
| 1           | Solo ejecución                 |
| 2           | Solo escritura                 |
| 3           | Escritura y Ejecución          |
| 4           | Solo lectura                   |
| 5           | Lectura y ejecución            |
| 6           | Lectura y escritura            |
| 7           | Lectura, escritura y ejecución |

Con los datos anteriores y utilizando el comando chmod mira estos ejemplos:

| Comando              | Resultado                               |
| -------------------- | --------------------------------------- |
|                      | Usuario: Lectura, escritura y ejecución |
| `chmod 755 delme.tx` | Grupo: Lectura y ejecución              |
|                      | Otros: Lectura y ejecución              |

| Comando               | Resultado                               |
| --------------------- | --------------------------------------- |
|                       | Usuario: Lectura, escritura y ejecución |
| `chmod u+r delme.txt` | Grupo: lo deja como estaba              |
|                       | Otros: Lo deja como estaba              |

| Comando                    | Resultado                                                              |
| -------------------------- | ---------------------------------------------------------------------- |
|                            | Usuario: Lectura y escritura los deja como estaba y le quita ejecución |
| `chmod u-x,go=w delme.txt` | Grupo: deja solo escritura                                             |
|                            | Otros: deja solo escritura                                             |
