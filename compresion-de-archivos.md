# Compresión de archivos

Comprimir un archivo es redudicr la cantidad de bits que ocupa un archivo. En linux se puede realizar este proceso

## Empaquetado con el comando tar

Es la opción mas utilizada en repositorios.

### Parámetros

**-c**: Indica compresion o creación
**-v**: Muestra el procesamiento en la terminal (verbose)
**-f**: Indica el tipo de recurso archivo (file) como destino
**-z**: Compresión o descompresión en formato gzip
**-x**: Descompresión

**¡El orden de los parametros importa!**

El orde DEBE ser:
**tar**: Comando de ejecución
**cvf**: Parametros en este orden (el destino debe ir de último)
**export.tar** El nombre del archivo que se va a crear
**compress** La carpeta de origen de los archivos

## Compresión en .tar (estándar)

Ejemplo:

`tar -cvf export.tar compress`

## Compresión en .gz (gzip)

Ejemplo:

`tar -cvzf export.tar.gz compress`

## Extracción de archivos

La descompresión de archivo no requiere de un destino, sin embargo si coloca la opción para el formato gzip, el archivo a descomprimir debe estar en ese formato. **La extracción crea siempre la ruta comprimida, puede sobreescribir archivos sin preguntar si ya existen**

### Parámetros

Hay que tener en cuenta que los parametros de extración deben estar (es buena practica) luego escribir el nombre del archivo empaquetado o comprimido, para evitar confusión.

**-c, --directory**: Carpeta de destino de los archivos (debe estar creada previamente)

Ejemplo:
`tar -xvzf export.tar.gz` (descomrimir gzip)
`tar -xvzf export.tar.gz --directory ~/aquired/checkInfo` (descomrimir gzip en la carpeta ~/aquired/checkInfo)

`tar -xvf export.tar` (descomrimir tar)
`tar -xvf export.tar --directory ~/aquired/temporal` (descomrimir gzip en la carpeta ~/aquired/temporal)

## Compresión en .zip

Posiblemente requiere de la instalación del paquete con `sudo apt install zip`. Este formato es más común y estandarizado

### Parámetros

**-r**: Comprimir de manera recursiva (con todos los directorios y archivos)

Ejemplo:
`zip -r packZip.zip compress`

## Descomsesion desde .zip

Posiblemente requiere de la instalación del paquete con `sudo apt install zip`.

### Parámetros

**-d**: Indica el directorio donde se extraerán los archivos

Ejemplo:
`unzip packZip.zip -d ~/uncompressed/packZip`
