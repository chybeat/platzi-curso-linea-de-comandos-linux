# Comandos de búsqueda

Son comandos para encontrar facilmente archivos directorios

## Which

Este comando muestra la ruta de archivos o enlaces ejecutables que están dentro de las carpetas de la variable de entorno $PATH

Ejemplo:

`which nano` : /usr/bin/nano

## Find

Find permite encontrar cuaquier archivo desde una ruta raiz y dentro de todas las carpetas de esa ruta enviada.

Ejemplo

`find ~/miCarpeta -name archivo*`

**~/miCarpeta**: La ruta de la carepta donde iniciará la busqueda (./ inicia desde la carpeta actual)
**-name**: opción para buscar nombre de archivio
**archivo\***: patron de busqueda, en este caso todos los archivos que comiencen con 'archivo' tengan o no mas caracteres

En caso de encontrarse muchos archivos se pueden pasar por el operador de redirección los resultados al comando less o more

`find ~/miCarpeta -name archivo* | less`

### Modificadores de find

**-name**: Busca en el nombre de archivo, directorio o recurso `find ~/miCarpeta -name archivo*`
**-type**: Busqueda por tipo (d=directorio f= archivo). `find ~/miCarpeta -type d -name *cosa*` busca solo carpetas cuyo nombre tenga "cosa" en cualquier parte
**-size**: Busqueda por tamaño de archivo
**-exec**:
