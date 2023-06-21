# Máquina Fawn

## Contenido

1. [Introducción](#introducción)
2. [Escaneo de puertos](#escaneo-de-puertos)
4. [Explotación](#explotación)

## Introducción

Las preguntas introductorias son:

¿Qué significa el acrónimo de 3 letras FTP?

Respuesta: File Transfer Protocol

¿En qué puerto escucha normalmente el servicio FTP?

Respuesta: 21

¿Qué acrónimo se utiliza para la versión segura de FTP?

Respuesta: SFTP

¿Cuál es el comando que podemos usar para enviar una solicitud de eco ICMP para probar nuestra conexión con el objetivo?

Respuesta: ping

Según sus escaneos, ¿qué versión de FTP se está ejecutando en el destino?

Respuesta: vsftpd 3.0.3. Se utiliza el comando `nmap -sV <IP>` para obtener esta información.

Según sus escaneos, ¿qué tipo de sistema operativo se ejecuta en el objetivo?

Respuesta: Unix. Se utiliza el comando `nmap -O <IP>` para obtener esta información.

¿Cuál es el comando que debemos ejecutar para mostrar el menú de ayuda del cliente 'ftp'?

Respuesta: fpt -h

¿Cuál es el nombre de usuario que se usa a través de FTP cuando desea iniciar sesión sin tener una cuenta?

Respuesta: anonymous

¿Cuál es el código de respuesta que recibimos para el mensaje FTP 'Inicio de sesión exitoso'?

Respuesta: 230

Hay un par de comandos que podemos usar para enumerar los archivos y directorios disponibles en el servidor FTP.  Uno es dir.  ¿Cuál es el otro que es una forma común de enumerar archivos en un sistema Linux?

Respuesta: ls

¿Cuál es el comando utilizado para descargar el archivo que encontramos en el servidor FTP?

Respuesta: get

## Escaneo de puertos

Para hacer un escaneo de puertos se necesita la herramienta `nmap` y se ejecuta el siguiente comando:
```bash
nmap <IP>
```

Al ejecutarlo nos damos cuenta que tiene un puerto abierto, el puerto 21 que es el puerto de ftp.

## Explotación

Para explotar la máquina vamos a usar el comando `ftp` pasándole como argumento la IP de la máquina.

```bash
ftp <IP>
```

Al no tener un usuario y contraseña para acceder al ftp se usa el usuario `anonymous` y se deja en blanco la contraseña.

Ya dentro de la máquina se puede usar el comando `ls` para ver los archivos que hay en la máquina. En este caso hay un archivo llamado `flag.txt` que contiene la flag de la máquina. Para descargar el archivo se usa el comando `get flag.txt` y se descarga en la máquina local.

Con esto podemos decir:

> Máquina Fawn **HACKEADA**





