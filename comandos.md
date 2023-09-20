# Docker - Comandos Básicos

Utilizaremos la imagen de Ubuntu (la última). Usa Visual Studio Code y Docker junto con esta imagen para seguir las siguientes instrucciones:

Descarga la imagen 'ubuntu y comprueba que está en tu equipo
Crea un contenedor sin ponerle nombre. ¿está arrancado? Obtén el nombre
Crea un contenedor con el nombre 'ubu1'. ¿Como puedes acceder a él?
Comprueba que ip tiene y si puedes hacer un ping a google.com
Crea un contenedor con el nombre 'ubu2'. ¿Puedes hacer ping entre los contenedores?
Sal del terminal, ¿que ocurrió con el contenedor?
¿Cuanta memoria en el disco duro ocupaste? ¿Hay alguna herramienta de docker para calcularlo?
¿Cuanta RAM ocupan los contenedores? Crea cuantos contenedores necesites para calcularlo.

1 - 
Primero, iremos a la página “Docker Hub” para ver una lista de imágenes. Empezaremos entrando en la Terminal y continuamente para descargar la imagen de cualquier Ubuntu pondremos “docker pull [imagen] que en este caso es ubuntu:22.04. Listo, ya estará descargada.
Para comprobar que está descargada podemos ir a la Terminal con el siguiente comando: docker ps -a. El “-a” es para ver todos los contenedores, es decir, los que están funcionando y los que no.

2 - Para crear un contenedor si

n nombre iremos a la Termiprimeros pasos

-docker run -it hello-world, continuamente si ponemos docker ps -a donde en la lista nos fijamos en los últimos cambios donde se nos creó un nombre, en mi caso distracted_leakey.

3 - 

Para crear un contenedor con un nombre (en este caso ‘ubu1’) pondremos el siguiente comando: docker run -it --name ubu1 ubuntu:22.04.

4 - 

Para comprobar la IP que tiene y si se puede pingear con Google / acceder a él, lo empezamos (Start) con “docker start ubu1” y continuamente con “docker exec -it ubu1 bash”. Una vez dentro hacemos un apt-get update para evitar fallos de paquetes y un apt-get upgrade continuamente. 

Una vez hecho esto, hacemos un “apt-get install net-tools” que es para poder ver las propiedades o detalles de dicho contenedor. Finalmente, pondremos “ifconfig”, mi IP en mi caso es “inet 172.17.0.2”.

Para poder pingear con Google, ponemos “apt-get update && apt-get install -y iputils-ping”. Por último, hacemos “ping 8.8.8.8” que es la IP de google y ya estaría.



5 -

Creamos otro contenedor con el nombre ‘ubu2’ y poder hacer ping entre ubu1 y ubu2.

Resumidamente, “docker run -it --name ubu2 ubuntu:22.04”, una vez dentro actualizamos con un update y un upgrade incluso e instalamos el net-tools dentro de este contenedor junto al de Ping. Finalmente, hacemos ping de este contenedor al otro, es decir, “ping 172.17.0.3” que es la IP del otro contenedor. Cabe recalcar que ambos contenedores deben estar encendidos para que esto funcione.

6 -

Es un poco relativo, es decir, si habías iniciado con un start un contenedor (no se cerrará) pero luego otro de otra forma (con exit), se deberían cerrar los contenedores abiertos.

7 -

Ponemos “docker ps –size” y ya podremos ver la memoria en el disco en ocupación. 62MB ambos contenedores.


8 - 

Para ver la RAM que ocupan los contenedores, ponemos el comando “docker stats”. Cabe destacar que tienen que estaré ambos encendidos / funcionando.  Está en un 0,01% de uso. Ocupa 892 KiB y 992 KiB de uso de memoria.












