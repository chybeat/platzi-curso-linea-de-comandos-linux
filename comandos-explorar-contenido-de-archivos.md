## Comandos para explorar el contenido de archivos

cat: muestra todo el contenido de un archivo en la ventana de la terminal

head: Muestra la cabezera o inicio de un archivo (10 primeras lineas)

    Ej: head principios_de_usabilidad_ejemplo.md

    -n #: muestra las primeras # líneas en un archivo
    Ej: head principios_de_usabilidad_ejemplo.md -n 15

tail: Muestra el final o lineas finales del contenido de un archivo (10 últimas lineas)

    Ej: tail principios_de_usabilidad_ejemplo.md

    -n #: muestra las últimas # líneas en un archivo
    Ej: tail principios_de_usabilidad_ejemplo.md -n 8

less: es un comando para interactuar con el archivo mirandolo con desplazamiento con las flechas

    EJ: less principios_de_usabilidad_ejemplo.md

    Flechas: mueve una línea a la vez (arriba y abajo) y en horizontal (izquierda y derecha) mueve 137 caracteres, esto último puede servir para revisar archivos que tengan conenido "oculto" a los lados

    Barra espaciadora: Mueve la visualización una pagina a la vez (alto de pantalla) hacia abajo

    Scroll del mouse: permite movimiento vertical infinito del archivo

    "/": permite hacer una busqueda de texto dentro del documento resaltando las coincidencias

    q: sale del entorno

nautilus: Lanza el explorador de archivos desde Linux

    Como parámetro se le puede colocar la carpeta que se quiera abrir

explorer.exe con el paramatro "." (punto), abre la carpeta actual ó la ruta completa (como se escribe en Windows) dentro de comillas.

wslpath muestra la ruta de cualquier ubicacion de windows dentro del sistema de archivos de WSL

wslview: sirve para lanzar la aplicacion predeterminada asociada a un archivo desde el entorno gráfico.

xdg-open: Lo mismo que wslview pero para Linux
