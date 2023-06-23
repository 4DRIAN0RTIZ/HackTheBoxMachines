# Máquina Appointment

## Contenido

1. [Introducción](#introducción)
2. [Escaneo de puertos](#escaneo-de-puertos)
4. [Explotación](#explotación)

## Introducción

Cuestionario:

¿Qué significa el acrónimo SQL?

Respuesta: Structured Query Language.

¿Cuál es uno de los tipos más comunes de vulnerabilidades de SQL?

Respuesta: SQL Injection.

¿Qué significa PII?

Respueta: Personally Identifiable Information.

¿Cuál es la clasificación OWASP Top 10 de 2021 para esta vulnerabilidad?

Respuesta: A03:2021-Injection

¿Qué informa Nmap como el servicio y la versión que se ejecutan en el puerto 80 del objetivo?

Respuesta: Apache httpd 2.4.38 ((Debian)). Se puede ver con el comando `nmap -sV <IP>`. El flag `-sV` es para ver la versión del servicio.

¿Cuál es el puerto estándar utilizado para el protocolo HTTPS?

Respuesta: 443

¿Cómo se llama una carpeta en la terminología de aplicaciones web?

Respuesta: Directory.

¿Cuál es el código de respuesta HTTP que se proporciona para los errores "No encontrado"?

Respuesta: 404.

Gobuster es una herramienta utilizada para forzar directorios en un servidor web.  ¿Qué interruptor usamos con Gobuster para especificar que buscamos descubrir directorios y no subdominios?

Respuesta: dir.

¿Qué carácter único se puede usar para comentar el resto de una línea en MySQL?

Respuesta: #.

Si la entrada del usuario no se maneja con cuidado, podría interpretarse como un comentario.  Use un comentario para iniciar sesión como administrador sin saber la contraseña.  ¿Cuál es la primera palabra de la página web devuelta?

Respuesta: Congratulations.


## Escaneo de puertos

Para hacer un escaneo de puertos se necesita la herramienta `nmap` y se ejecuta el siguiente comando:
```bash
nmap -sV <IP>
```

Al ejecutarlo nos damos cuenta que tiene un puerto abierto, el puerto 80 por ende se puede deducir que se trata de un servidor web.

## Explotación

Para explotar la máquina ingresamos a la página web con la IP de la máquina en el navegador. Al ingresar nos damos cuenta que es un sitio web que tiene un formulario para iniciar sesión. Aplicando el conocimiento que se tiene de SQL se puede deducir que el sitio web es vulnerable a SQL Injection. Usamos el siguiente comando para hacer un comentario en la consulta SQL:

```sql
admin' or 1=1;# 
```

> Lo que se realiza es una consulta SQL que devuelve todos los registros de la tabla de usuarios. El símbolo `#` es para hacer un comentario en MySQL. Ver [MySQL Comments](https://www.mysqltutorial.org/mysql-comments/). De esta forma se puede iniciar sesión como administrador sin saber la contraseña, vulnerando la autenticación de la página web.

En el campo de contraseña ingresamos cualquier cosa y damos clic en el botón de iniciar sesión. Al hacer esto nos redirige a otra página web que nos indica que hemos iniciado sesión como administrador. En la página web se muestra la flag.

Con esto podemos decir:

> Máquina Appointment **Hackeada**



