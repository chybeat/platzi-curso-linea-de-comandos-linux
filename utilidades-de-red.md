# Utiliades de red

Las utilidades de red muestran información acerca de la red. Estas funciones pueden no venir directamente con la distribución de linux, para utilizarlas se deben instalr con el comando `sudo apt install net-tools`.

## ifconfig

Este comando muestra la configuración de las tarjetas de red y de internet como direcciones, IPv4, IPv6, e incluso datos de paquetes.

## Ping

Ping sirve para verificar la conexión a un computador o servidor utilizando la dirección ip, su nombre o una URL. Para salir presionas CTRL + C

Ejemplo:
`ping www.google.com`

## CURL

Sirve para traer o enviar datos de un computador o servidor a otro usando los protocolos DICT, FILE, FTP, FTPS, GOPHER, HTTP, HTTPS, IMAP, IMAPS, LDAP, LDAPS, POP3, POP3S, RTMP, RTSP, SCP, SFTP, SMB, SMBS, SMTP, SMTPS, TELNET y TFTP

Ejemplo:

`curl https://www.google.com`

## wget

Descarga un archivo directamente desde la web, soporta los protocolos HTTP, HTTPS y FTP y atraves de proxis de tipo HTTP

Ejemplo:

`wget https://www.google.com`

## tracerout

Es un comando que sirve para ver los saltos por los servidores o dispositivos que se conecta el computador hasta llegar a una dirección ip o una URL especificada mostrando tambien el tiempo de respuesta.

Ejemplo:

`traceroute www.yandex.com`

## netstat

Mustra información de la tarjeta de red. Con el modificador `netstat -i` muestra el estado de las interfaces de red disponibles
