# Máquina Redeemer

## Contenido

1. [Introducción](#introducción)
2. [Escaneo de puertos](#escaneo-de-puertos)
4. [Explotación](#explotación)

## Introducción

Cuestionario:

¿Qué puerto TCP está abierto en la máquina?

Respuesta: 6379. Se usa el comando `nmap -p- <IP> --min-rate 5000` para ver los puertos abiertos. La flag --min-rate 5000 es para que el escaneo sea más rápido. Se puede omitir pero tarda más tiempo.

¿Qué servicio se está ejecutando en el puerto que está abierto en la máquina?

Respuesta: Redis. Se puede ver en la descripción del puerto.

¿Qué tipo de base de datos es Redis?  Elija entre las siguientes opciones: (i) Base de datos en memoria, (ii) Base de datos tradicional

Respuesta: In-memory database.

¿Qué utilidad de línea de comandos se usa para interactuar con el servidor Redis?  Ingrese el nombre del programa que ingresaría en la terminal sin ningún argumento.

Respuesta: redis-cli.

¿Qué bandera se usa con la utilidad de línea de comandos de Redis para especificar el nombre de host?

Respuesta: -h.

Una vez conectado a un servidor Redis, ¿qué comando se utiliza para obtener la información y estadísticas sobre el servidor Redis?

Respuesta: INFO.

¿Cuál es la versión del servidor Redis que se usa en la máquina de destino?

Respuesta: 5.0.7. Lo podemos comprobar con el comando `INFO`.

¿Qué comando se usa para seleccionar la base de datos deseada en Redis?

Respuesta: SELECT. Los comandos de Redis se pueden ver [aquí](https://redis.io/commands). Los índices de las bases de datos son de 0 a 15.

¿Cuántas claves están presentes dentro de la base de datos con índice 0?

Respuesta: 4. Se puede ver con el comando `DBSIZE`.

¿Qué comando se utiliza para obtener todas las claves de una base de datos?

Respuesta: KEYS *.

## Escaneo de puertos

Para hacer un escaneo de puertos se necesita la herramienta `nmap` y se ejecuta el siguiente comando:

```bash
nmap -p- <IP> --min-rate 5000
```

> El flag --min-rate 5000 es para que el escaneo sea más rápido. Se puede omitir pero tarda más tiempo.

Al ejecutarlo nos damos cuenta que hay varios puertos abiertos. El puerto 6379 es el que nos interesa.

## Explotación

Para explotar la máquina vamos a usar la herramienta `redis-cli` que sirve para interactuar con el servidor Redis. Usando el flag -h podemos especificar el nombre del host.

```bash
redis-cli -h <IP>
```

Para ver las keys que hay en la base de datos 0 se usa el comando `KEYS *`. En este caso hay 4 keys.

Para obtener el contenido de una key se usa el comando `GET <key>`. En este caso la key `flag` contiene la flag.

```redis-cli
get flag
```

Eso nos muestra la flag.

Con esto podemos decir:

> Máquina Redeemer **Hackeada**



