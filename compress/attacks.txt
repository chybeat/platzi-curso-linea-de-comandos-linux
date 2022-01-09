# Wildcards

Son una serie de caractres epeciales para denominar patrones como:

`*`: Que implica "cualquier caracter o caracteres"
Ej:
`ls w_.md`
Muestra todos los archivos que empiecen por 'w' y tengan la extension ".md"

`?`: Que implica "cualquier caracter" (uno solo);
Ej:
`ls w*.??`
Muestra todos los archivos que empiecen por 'w' y tengan una extension de 2 caracteres unicamente

`[]`: Que en la posición que se coloquen los corchetes contenga los caracteres o rango dentro de corchetes. Tener en cuenta es que en este caso los nombres de archivos y la extensión se toman como una sola cadena de texto. Para colocar rangos de letras o números se utiliza "-" como puente de un rango como en el Ejemplo 2.

Ej:
`ls *[os].*`
Muestra todos los archivos de los cuales el nombre termine en [os] de cualquier extension

    Ej 2:
    `ls users-[2-7][l-oL-O]*`
    (Mustra todos los archivos que comiencen por "users-", que el primer caracter sea un número entre 2 y 7, que luego traiga una letra en minúscula o mayúscula en el rango de la "ele" a la "o" y que luego contenga cualquier caracter)

# Categorias o clases en wildcards

Las categorías se pueden describir como un rango global de caracteres. En el ejemplo anterior (ejemplo 2) se especifica un rango, como en [2-7] (de 2 a 7).

Algo importante a destacar es que las siguientes categorías **deben estar o mostrarse dentro de un rango, es decir, son un "rango" de un rango.**

Ejemplo:
`ls *[[:space:]]*` (muestra los archivos que tienen un espacio)

`[:upper:]` SOLO Letras mayúsculas
`[:lower:]` SOLO Letras minúsculas
`[:alpha:]` letras del alfabeto mayúscuas y minúsculas
`[:digit:]` múmeros decimales del 1 al 9
`[:alnum:]` alfanuméricos lo que contiene [:digi:] y lo que contiene [:alpha:]
`[:space:]` Espacios en blanco como espacios tabulaciones lineas de retorno o nuevas lineas, etc
`[:graph:]` caracteres imprimibles EXcluyendo espacio
`[:print:]` caracteres imprimibles INcluyendo espacio
`[:punct:]` caracteres de puntiucion o lo mismo que en [:graph:] EXcluyendo lo que aparece en [:alpha:] y [:digit:]
`[:cntrl:]` caracteres de control o carateres no imprimibles
`[:xdigit:]` Caracteres que son figitos hexadecimales
