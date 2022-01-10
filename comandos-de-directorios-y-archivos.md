# Comandos de directorios y archivos

##Teclas hacia arriba y hacia abajo van mostrando los comandos anteriores

**cd:** cambiar directorio a la ruta que se le pasa por parametro

    (sin parametro): Llea directamente a la carpeta home

    . : Parámetro relativo a la carpeta actual para cambiar de directorio (No es necesario escribirla)
    Ej: cd ./Documentos/Trabajo
    Lo mismo es: cd documentos/trabajo
    .. : Parámetro relativo a la carpeta anterior de la ruta.
    Ej: Suponiendo que estamos en la carpeta trabajo de documentos y que existe dentro de documentos otra carpeta llamada hogar podemos escrbir:
    cd ../hogar

    / : Ruta relativa a la raíz del sistema de archivos
    Ej: cd /home
    Nos lleva a la home principal de la parpeta raiz
    /home $

**cp:** Crea una copia de un archivo.
ej: cp "la cocinera/fotografia.jpg" datos/cocinera.jpg

**clear:** (atajo > CTRL + L) limpia la panalla para dejar solo una linea del prompt, para escribir un comando

**file:** describe o muestra información acerca de un archivo (contenido dimensiones, etc)

**ls:** Muestra los archivos de la carpeta actual

-   -l (long): Muestra los archivos en formato detallado

-   -h: Muestra el tamaño de los archivos en formato KB, MB. GB en vez de en bytes

-   -S: ordena los archivos por tamaño (del mas grande al mas pequeño)

-   -r: Ordena los archivos en oprden descendente (en reversa)

Ej: `ls -lhS`

La siguiene tabla muestra los tipos de recursos que puede ser el primer caracter de una lista larga

| Caracter | Tipo de recurso         |
| -------- | ----------------------- |
| -        | Archivo                 |
| d        | Directorio              |
| l        | Enlace simbólico        |
| c        | Dispositivo de carácter |
| b        | Dispositivo de bloques  |
| s        | Conexiones locales      |
| p        | Conexiones              |

**mkdir:** Sirve para crear directorios o carpetas (si el directorio necesita espacios escribir entre comillas)

Ej: `mkdir "pruebas/incepcionDeCarpeta/Prueba de espacio"` crea la carpeta "Prueba de espacio" si previamente existe la carpeta con el nombre "incepcionDeCarpeta" y "pruebas". La última (pruebas) en la ruta actual

Si se colocan varios nombres de archivo (separados por espacio un espacio) se pueden crear inmediatamente.

EJ `mkdir ejemplo datos "la cocinera"`
crea un arbol similar al siguiente: (ver con tree)

    .
    | datos (dir)
    | ejemplo (dir)
    | la cocinera (dir)

**mv:** mover o renombrar un archivo o un directorio

Ej: `mv ejemplo/ComoSizo.txt "la cocinera/Como se hizo.txt"`

Ej:
`mkdir dirCercano dirCercano/undirPaEntro`
`mv dirCercano dirAjuera`

**pwd:** (Print Working directory) Muestra el directorio actual

**rm:** Sirve para eliminar un archivo o un directorio

Ej: `rm datos/cocinera.jpg`

-r (--recvursive): Sirve para eliminar recursivamente el contenido de un directorio (Con todo lo que tenga por dentro)
-i pregunta antes de eliminar cada archivo o directorio

Ej: `rm -r dirAjuera"`: Elimina tambien "undirPaEntro"

**rmdir:** elimina un drectorio siempre y cuando este vacio
Ej: `rmdir dirCercano` -> Lanza error ya que dirCercano tiene un directorio llamado "undirPaEntro"
Ej: `rmdir rCercano/undirPaEntro`

**tree:** Muestra el contenido en forma de arbol de los archivos y carpetas en la carpeta actual

(agregar con "sudo apt install tree" (o apt-get) y luego actualizar lista de paquetes mas recientes linux con "sudo apt-get update" y luego descargar e instalar con "sudo apt upgrade")

-L #: donde # es el nivel o profundidad de carpetas a ver dentro de las carpetas de la carpeta actual (nivel por defecto es)

**Touch:** crea un archivo (con nada de contenido)

Se pueden pasar varios nombres de archivo al tiempo separados por espacio. (ver ejemplo en mkdir para entender las rutas)

Ej: `./datos/amigos.txt datos/enemigos.md "la cocinera/fotografia.jpg" ejemplo/ComoSizo.txt`

Mostrará un arbol (comando tree) de la siguiente forma:

    .
    | datos (dir)
        |_amigos.txt
        |_enemigos.md
    | ejemplo (dir)
        |_ComoSizo.txt
    | la cocinera (dir)
        |_Fotografía.jpg
