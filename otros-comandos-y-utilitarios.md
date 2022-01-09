# Comandos utilitarios

Estos comando puede que no estén relacionados con un tema en específico.

**whoami:** muestra quien es el usuario actual del sistema

**id**: Muestra el identificador o identificadores de los usuarios y/o de los grupos.

**su**: (Switch User): cambia entre usuarios del computador. Ej `su root`

**passwd**: Cambio de contraseña de usuario.

**ln**:
Crea un enlace simbólico (acceso directo) a un archivo o carpeta. Ej:
`ln -s ~/carpeta/muy/increiblemente/lejana/ lejana`
'-s' Ejecuta el comando para crear un enlace simbólico

**grep**: Es una utilidad para encontrar un texto deontro de un archivo de texto o de otro texto, como un stdout. Como primer parametro recibe una expresión regular y el segundo el nombre de un fichero.

Ejemplo:

`grep Towers movies.csv`

-   **-i**: ignora si la palabra tiene caracteres en mayúscula o minúscula
-   **-c**: Muestra la cuenta de coincidencias
-   **-v**: Muestra las líneas que no tienen una coincidencia de lo que está solicitandose

**wc**: (Word count) muestra un resultado de la cantidad de palabras que existen en un archivo o un stdout.

Ejemplo:
`wc movies.csv`
El resultado puede ser similar a lo siguiente:

    9126 30006 477779 movies.csv

lineas palabras bytes archivo

-   **-l**: Mustra solo el número de lineas. `wc movies.csv` muestra `9126 movies.csv`
-   **-w**: Mustra solo el número de palabras. `wc movies.csv` muestra `30006 movies.csv`
-   **-C**: Mustra solo el número de bytes. `wc movies.csv` muestra `477779 movies.csv`

**cat**: Es programa que permite ver o agregar texto a un archivo. Para ver un archivo se utiliza `cat leeme.txt` y para agregar texto a un archivo se utiliza `cat > nuvoArchivo.txt`. Para terminar el programa y guardar el texto escrito se debe presionar **CTRL+D**, y para parar el proceso y dejarlo en memoria se presiona **CTRL+Z**

**less** Este comando es muy usado con el operador de control "|" para redirigir un texto muy largo y entrar en una "interfaz" que nos permita realizar desplazamiento y hacer una inspección del texto usando las teclas. Un comando muy útl es escribir la barra invertido y un texto `/buscar` para que resalte las coincidencias de la palabra "buscar" (si encuentra) dentro de la intterfaz.
