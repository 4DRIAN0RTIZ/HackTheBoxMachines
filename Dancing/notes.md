# Máquina Dancing

## Contenido

1. [Introducción](#introducción)
2. [Escaneo de puertos](#escaneo-de-puertos)
4. [Explotación](#explotación)

## Introducción

Cuestionario:

¿Qué significa el acrónimo de 3 letras SMB?

Respuesta: Server Message Block

¿Qué puerto utiliza SMB para operar?

Respuesta: 445

¿Cuál es el nombre del servicio para el puerto 445 que apareció en nuestro escaneo Nmap?

Respuesta: microsoft-ds. Se utiliza el comando `nmap -sV <IP>` para ver el nombre del servicio.

¿Cuál es la 'bandera' o 'interruptor' que podemos usar con la herramienta SMB para 'listar' el contenido del recurso compartido?

Respueta: smbclient -L <IP>

¿Cuántas participaciones hay en la máquina Dancing?

Respuesta: 4. Lo podemos ver con el comando `smbclient -L <IP>`

¿Cuál es el nombre del recurso compartido al que podemos acceder al final con una contraseña en blanco?

Respuesta: WorkShares. Lo podemos ver con el comando `smbclient -L <IP>`

¿Cuál es el comando que podemos usar dentro del shell SMB para descargar los archivos que encontramos?

Respuesta: get <archivo>

## Escaneo de puertos

Para hacer un escaneo de puertos se necesita la herramienta `nmap` y se ejecuta el siguiente comando:
```bash
nmap <IP>
```

Al ejecutarlo nos damos cuenta que tiene un puerto abierto, el puerto 445 que es el puerto de SMB.

## Explotación

Para explotar la máquina vamos a usar el comando `smbclient -L <IP>` para ver las carpetas compartidas. Una vez hecho esto nos damos cuenta que hay una carpeta llamada `WorkShares` a la que podemos acceder sin contraseña.

Para acceder a la carpeta se usa el siguiente comando:
```bash
smbclient //<IP>/WorkShares
```

Una vez dentro de la carpeta podemos ver los archivos que hay dentro de ella con el comando `ls`. En este caso hay dos directorios, uno llamado 'Amy.J' y otro llamado 'James.P'.

Dentro del directorio 'Amy.J' hay un archivo llamado 'worknotes.txt'. Y dentro del directorio 'James.P' hay un archivo llamado 'flag.txt'.

Para obtener el archivo flag.txt se usa el comando `get flag.txt`. Y para obtener el archivo worknotes.txt se usa el comando `get worknotes.txt`.

Con esto podemos decir:

> Máquina Dancing: **Hackeada**





