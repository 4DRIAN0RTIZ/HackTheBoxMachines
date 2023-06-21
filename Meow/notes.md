# Máquina Meow

## Contenido

1. [Introducción](#introducción)
2. [Escaneo de puertos](#escaneo-de-puertos)
4. [Explotación](#explotación)

## Introducción

Lo primero es saber que el hacking ético es eso. En esta máquina se está usando Telnet, por ende se va a vulnerar.

## Escaneo de puertos

Para hacer un escaneo de puertos se necesita la herramienta `nmap` y se ejecuta el siguiente comando:
```bash
nmap <IP>
```

Al ejecutarlo nos damos cuenta que tiene un puerto abierto, el puerto 23 que es el puerto de Telnet.

## Explotación

Para explotar la máquina vamos a usar el comando Telnet pasándole como argumento la IP de la máquina.

```bash
telnet <IP>
```

En este ejemplo el usuario es `root` y no cuenta con contraseña.

Ya dentro de la máquina se puede usar el comando `ls` para ver los archivos que hay en la máquina. En este caso hay un archivo llamado `flag.txt` que contiene la flag.


Con esto podemos decir:

> Máquina Meow **Hackeada**



