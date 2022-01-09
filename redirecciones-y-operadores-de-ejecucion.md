# Redirecciones en la shell y Operadores

## Operadores de entrada y salida

La mayoría de los comandos tienen 2 tipos de salida, la normal y que nos devuelve un resultado (stdout o standard out) y la que es un error (stderr o standard error)

```
                 stdout (Salida estandar o 1)
                /                             \
stdin -> Comando                               resultado en pantalla
                \                             /
                 stderr (Salida de error o 2)
```

### redireccion de salida a archivos (> y >>)

Para escribir la salida en pantalla de un comnado se debe colocar [elComando] ">" [elArchivo.txt], esto hara que no se muestre nada en pantalla y todo se envíe a "elArchivo.txt" Si el archivo no existe se creará.

**¡¡¡ Es importante saber que con cualquiera de estos simbolos de redireccion se sobre escribe un archivo sin preguntar !!!**

Ej: `ls > archivosDelDir.txt`

En caso de querer agregar más datos del mismo o de otro comando al mismo archivo (concatenar), se debe colocar ">>", que en cierta medida es mejor práctica en varios modos.

### Redirección de salida de errores (stderr)

Al ejecutar un comando cuya salida es un error como por ejemplo al ver el contenido de una carpeta que no existe (ls estaCarpetaNoExisteONoEstaCreada > error.txt) el resultado es `ls: cannot access 'estaCarpetaNoExisteONoEstaCreada': No such file or directory` sin escribir nada en el archivo

Este error no se escribe con la redirección vista anteriormente usando ">" o ">>" simplemente ya que el shell está configurado para que solo escriba una salida correcta. En este caso es necesaio forzar la salida de error colocando un 2 antes del simbolo de redirección.

Ejemplo:
`ls estaCarpetaNoExisteONoEstaCreada 2> error.txt`
`ls otraCarpetaInexistente 2>> error.txt`

luego de ejecuitar ambos comandos el contenido de error.txt es el siguiente:

    ls: cannot access 'estaCarpetaNoExisteONoEstaCreada': No such file or directory
    ls: cannot access 'estaCarpetaNoExisteONoEstaCreada': No such file or directory

También se pueden redirigir cada salida a un archivo distinto:

Ejemplo:
`ls careptaQueNoSeSiExiste 1> listadoDeArchivos.txt 2> error.txt`

Al final terminaría escribiendo la salida en el archivo que corresponda dependiendo de si tiene o no exito la solicitud del comando.

### Redirección de ambas salidas a un mismo archivo (stderr y stdout)

Pueden existir casos en los que queremos guardar la salida sea erronea o no. Para ello se debe colocar el comando, el simbolo de redirección, el archivo al que se redirige la salida y una redireccion de las 2 salidas.

Ejemplo:
Suponiendo que exite una carpeta llamada 'carpetaExistente' que tiene otras carpetas (datos, ejemplo, incepcionDeCarpeta y la cocinera)

Los comandos a ejecutar son:

`ls carpetaExistente >> contenido.txt 2>&1`
`ls estaCarpetaNoExisteONoEstaCreada >> contenido.txt 2>&1`

El archivo 'contenido.txt' tendrá:

    datos
    ejemplo
    incepcionDeCarpeta
    la cocinera
    ls: cannot access 'estaCarpetaNoExisteONoEstaCreada': No such file or directory

### Redirección a la entrada (stdin)

Al igual que a las salidas pueden ser redirigidas, la entrada generalmente se utiliza para comandos que requieren que el usuario ingrese datos.

Ejemplo:

Es posible crear un archivo con un texto cualquiera usando el comando echo (echo sirve para mostrar un texto en pantalla) y luego redirigir ese texto a un archivo. El parametro e permite el escape para caracteres no imprimibles (en este caso \n que es nueva linea).

`echo -e "5 cinco\n6 seis\n8 ocho\n2 dos\n10 diez\nz\nc\na" > listado.txt`

esto nos deja con el archivo listado con este conenido:

    5 cinco
    6 seis
    8 ocho
    2 dos
    10 diez
    z
    c
    a

Este contenido puede pasarse al comando sort que requiere un listado para ordenar cada linea con la redirección de entrada

Ejemplo

`sort < listado.txt`

Lo cual mostrará:

    10 diez
    2 dos
    5 cinco
    6 seis
    8 ocho
    a
    c
    z

Esta ultima salida tambien puede ser direccionada a un archivo llamado ordenado.txt y visualizarse con cat

Ejemplo:

```
sort < listado.txt > ordenado.txt
cat ordenado.txt
```

Mostrará desde ordenado.txt lo siguiente:

    10 diez
    2 dos
    5 cinco
    6 seis
    8 ocho
    a
    c
    z

## Operador en cadena (pipe)

Es un operador que sirve para redirigir el stdout (la salida o lo que se ve en pantalla)de un comando, como stdin (datos de entrada) en otro comando para procesarlo.

Ejemplo

Quiero que se guarden en el archivo modif2am.txt los archivos el que hayan sido modificados entre las 2:00am y 2:59 am.

Usando los fltros del comando ls no sería muy facil de hacer sin embargo como grep procesa patrones de busqueda de texto y teniendo en cuenta que lh -l nos mustra la hora de modificación de un archivo en formato 24 horas se puede usar un truco como este:

`ls -lh | grep -e'02:'`

Grep nos muestra solo las lineas que contienen el texto '02:' de todas las que fueron pasadas como 'stdin'

Ahora como se quiere pasar a un archivo, hay 2 formas, una es con el operador de redirección ">", y otro con el comando 'tee' que vamos a usar con fines de demostración del operador en cadena.

`ls -lh | grep -e'02:' | tee modif2am.txt`

## Operador de ejecución síncrona (;)

Este operador realiza una tarea despues de otra, en el orden en que se escriben.

Ejemplo;

`ls soyNuevo; mkdir soyNuevo; cal`
(el comando 'cal' muestra un calendario del mes actual)

El resultado anterior muestra algo similar a los siguiente:

    ls: cannot access 'soyNuevo': No such file or directory
       December 2021
    Su Mo Tu We Th Fr Sa
              1  2  3  4
     5  6  7  8  9 10 11
    12 13 14 15 16 17 18
    19 20 21 22 23 24 25
    26 27 28 29 30 31

Al haber solicitado que se mostrara 'soyNuevo' el comando ls nos arrojó un error, pero continuó ejecutandose cal, el directorio 'soyNuevo' tambien se creó.

## Operador de ejecución Asyncrona (&)

Este operador crea nuevos procesos al mismo tiempo en la consola para ejecutar varias tareas al mismo tiempo:

Ejemplo ;

`echo "soy 1ero" & ls -R /dev/ & date & cal & echo "soy ultimo"`

Puede devolver en distinto orden los resultados, en mi caso fue similar al siguiente:

    [1] 263
    soy 1ero
    [2] 264
    [3] 265
    [4] 266
    soy ultimo
    [1]   Done                    echo "soy 1ero"
    Wed Dec  1 19:08:13 -05 2021
    /dev/:
    December 2021
    Su Mo Tu We Th Fr Sa
            1  2  3  4
    5  6  7  8  9 10 11
    12 13 14 15 16 17 18
    19 20 21 22 23 24 25
    26 27 28 29 30 31

    autofs           loop-control  net    ram13  random  tty0   tty19  tty29  tty39  tty49  tty59  ttyS2      vsock
    block            loop0         null   ram14  rtc0    tty1   tty2   tty3   tty4   tty5   tty6   ttyS3      zero
    bsg              loop1         nvram  ram15  sda     tty10  tty20  tty30  tty40  tty50  tty60  urandom
    btrfs-control    loop2         ppp    ram2   sdb     tty11  tty21  tty31  tty41  tty51  tty61  vcs
    console          loop3         ptmx   ram3   sg0     tty12  tty22  tty32  tty42  tty52  tty62  vcs1
    cpu_dma_latency  loop4         pts    ram4   sg1     tty13  tty23  tty33  tty43  tty53  tty63  vcsa
    cuse             loop5         ram0   ram5   shm     tty14  tty24  tty34  tty44  tty54  tty7   vcsa1
    fd               loop6         ram1   ram6   stderr  tty15  tty25  tty35  tty45  tty55  tty8   vcsu
    full             loop7         ram10  ram7   stdin   tty16  tty26  tty36  tty46  tty56  tty9   vcsu1
    fuse             mapper        ram11  ram8   stdout  tty17  tty27  tty37  tty47  tty57  ttyS0  vfio
    kmsg             mem           ram12  ram9   tty     tty18  tty28  tty38  tty48  tty58  ttyS1  vhost-net

    /dev/block:

    /dev/bsg:
    0:0:0:0  0:0:0:1

    /dev/mapper:
    control

    /dev/net:
    tun

    /dev/pts:
    0  1  ptmx

    /dev/vfio:
    vfio

    [2]   Done                    ls --color=auto -R /dev/
    [3]-  Done                    date
    [4]+  Done                    cal

Teniendo en cuenta que el último comando no se ejecuta en un proceso paraleo o de fondo, al verificar el orden de ejecución fue el siguiente:

Escribió "soy primero"
Escribió "soy ultimo"
Escribió la fecha: Wed Dec 1 19:08:13 -05 2021
mostró el calendario
Por ultimo el listado de archivos

El orden correcto era: `echo "soy 1ero" & ls -R /dev/ & date & cal & echo "soy ultimo"`

Escribir 'soy primero' (bien)
Listado de archivos (retrasado por 3 comandos)
mostrar la fecha (adelantado 1 comando)
mostrar un calendario (adelantado 1 comando)
Escribir 'soy ultimo' (impreso al inicio del comando)

    [1] 263
    soy 1ero
    [2] 264
    [3] 265
    [4] 266
    soy ultimo
    [1]   Done                    echo "soy 1ero"
    ....

La ejecución del comando echo es inmediata y no hace espera, por eso "soy 1ero" se ejecuta inmediatamente se solicita, pero el comando ls demora un poco mas en procesarse y por ello es el último en ejecutarse y mostrar el resultado.

## Operador de ejecución condicional AND (&&)

El operador permite ejecutar una serie de comandos si el comando anterior no da por salida a stderr.

Ejemplo:

`cal && cd carpetaQueNoExiste && pwd`

El anterior comando muestra lo siguiente;

    December 2021
    Su Mo Tu We Th Fr Sa
            1  2  3  4
    5  6  7  8  9 10 11
    12 13 14 15 16 17 18
    19 20 21 22 23 24 25
    26 27 28 29 30 31

    -bash: cd: carpetaQueNoExiste: No such file or directory

Al final no ejecuta pwd. Si se cambia a una carpeta que si existe pwd se ejecutará:

` usuario@usuario: ~ cal && cd carpetaExistente && pwd`

Mostrará:

    December 2021
    Su Mo Tu We Th Fr Sa
            1  2  3  4
    5  6  7  8  9 10 11
    12 13 14 15 16 17 18
    19 20 21 22 23 24 25
    26 27 28 29 30 31

    home/usuario/carpetaExistente

## Operador de ejecución condicional OR (||)

Ejecuta una serie de comandos verificando que el anterior comando no haya sido ejecutado.

Ejemplo:

Vamos colocar una serie de comandos que me listen los archivos.txt y si no hay cree uno llamado 'no.txt' con la fecha dentro de ese archivo y que por ultimo muestre en pantalla si no se crea el archivo un texto que diga no que hay archivos txt.

`ls -lh *.txt || date > no.txt || echo "No hay archivos de texto"`

En la ejecucion muestra los siguiente:

    ls: cannot access '*.txt': No such file or directory

Esto sucede por lo siguiente:

Entre `ls -lh *.txt || date > no.txt` al no haber archivos ".txt" crea uno nuevo llamado 'no.txt'

Entre `date > no.txt || echo "No hay archivos de texto"` al haberse creado 'no.txt' no hay error alguno, entonces no muestra el texto.

En una siguiente ejecución de mismo comando (`ls -lh *.txt || date > no.txt || echo "Si hay archivos de texto"`)

Muestra en pantalla lo siguiente:

    -rwxrwxrwx 1 chybeat chybeat 29 Dec  1 23:39 no.txt

Pero tampoco muestra el echo, y es por lo siguiente:

Entre `ls -lh *.txt || date > no.txt` Se ejecuta ls y la salida no pasa por stderr (no hay error), como la unica condición para que se ejecute un comando después de '||' es que haya previamente un error, al poder ejecutar desde el 'ls' desde el principio los demás comandos son omitidos.

Caso distinto es que si no se pueda escribir 'no.txt' por ejemplo por permisos.
