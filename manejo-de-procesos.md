# Manejo de procesos

**ps**: Muestra información acerca de procesos activos en el sistema. Entre otros muestra su ID de ejecucion, y el comnado en consola que lo ejecutó.

**kill**: Es el comnado para cerrar o acabar con un proceso. Para terminar un proceso es necesario obter el PID (Process IDentifier) del proceso a terminar. La opción mas fácil para enviar la señal de terminación forzada es `-9` que realiza la terminación total del proceso.

Ejemplo

`cat & ls` (Para dejar en ejecución el proceso cat)
`ps` (Para ver los procesos activos y su PID)

Resultado:
PID TTY TIME CMD
6780 pts/0 00:00:00 bash
6828 pts/0 00:00:00 cat
6830 pts/0 00:00:00 ps

`kill -9 6828` (para terminar el proceso cat)

**top**: Es un comando con una interfaz que permite el filtrado de procesos

**htop**: Es un comando que no viene por defecto, pero se puede isntalar con `sudo apt install htop`. En general es un programa con una interfaz un poco mas completa que top y permite realizar un cierre completo (kill) de un proceso.

**pkill**: Es igual que kill, pero como parametro se puede pasar una expresion regular para el nombre del proceso, admite también el parámetro de señales (como -9 para SIGKILL)

## Proceos en suspensión (background)

Algunos comandos útiles para esta tarea son:

**jobs**: Mustra procesos que fueron parados o suspendidos de su ejecución pero que no han terminado. Como por ejemplo `cat > miArchivo.txt` y luego presionar CTRL+Z.

**fg**: Vuelve a la ejecución de un comando o proceso que este en background o haya sido susprendido. Este comando depende del número del proceso que mustra jobs: `fg 1`

**bg** envía un proceso a suspensión o background. Depende del número que jobs nos arroja". `bg 1`

**operador de control &**: Con este operador se ejecuta asyncronamente, eso quiere decir que los comandos se ejecutan independientemente de su resultado o standar output pero en segundo plano. Ejemplo `cat > miArchivo.txt &`
