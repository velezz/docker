### ¿Qué es Docker?

Docker es un empaquetador de aplicaciones o un sistema de virtualización como lo quieran llamar, a que me refiero con esto? docker en pocas palabras es una máquina virtual ligera en la se puede contener aplicaciones o sistemas operativos.

### ¿Para qué sirve docker?

Docker sirve para crear contenedores independientes al servidor que desplieguen aplicaciones diferentes el cual evita la sobrecarga de iniciar y mantener máquinas virtuales completas en una instancia, sirve para crear imágenes personalizadas de diferentes sistemas operativos con diferentes aplicaciones, ya sean, tomcat, apache, node js, MySQL, etc…  

### ¿Qué podemos hacer en docker?

Como lo comente anteriormente en docker podemos hacer varias cosas desde inicar un contenedor con alguna aplicación o un sistema personalizado, crear imágenes personalizadas de las mismas aplicaciones o sistemas y compartirlos en la nube con docker hub y docker cloud, e iniciarlas en algún otro servidor sin tener que cargar algún dispositivo con las imágenes aunque claro también puedes empaquetar la imagen y trasladarla en un dispositivo.

### Cómo funciona docker?

Docker es una plataforma de código abierto que sus funcionalidades son de aislamiento de los recursos del kernel  para poder crear contenedores en el cual podamos desplegar una única aplicación con sus dependencias, es una manera evolucionada de crear “máquinas virtuales” a diferencia por el tamaño y la utilización de servicios, docker funciona como un motor que utiliza los recursos del sistema operativo para crear contenedores.
la gráfica de la diferencia entre un contenedor de docker y una máquina virtual sería:


![funcionamiento docker](https://github.com/velezz/docker/blob/main/images/docker1.png)

### ¿Porqué virtualizar con docker? 

En pocas palabras hacer una maquina virtual nos consume bastantes recursos del servidor, por lo menos tendríamos que tener 1GB de memoria libre, y utilizar parte de nuestro almacenamiento destinado a esa máquina virtual, como mínimo unos 20 GB para el sistema operativo y las aplicaciones a instalar en el, docker lo que hace es cargar la memoria con las librerías y dependencias que necesarias para ejecutar las aplicaciones, y ahorrar hasta en un 80% la carga hacia nuestro servidor, además de que docker nos da una serie de ventajas respecto  a hacerlo con máquinas virtuales, 
docker nos da:
Portabilidad: los contenedores creados con docker son portables porque podemos trasladarlos fácilmente a otro equipo con docker.
ligereza: Al no tener un sistema operativo por completo los recursos utilizados son mínimos.
Autosuficiencia: el motor se encarga de todo por eso los contenedores solo tienen lo necesario para poder correr las aplicaciones.

### ¿Qué es un contenedor?

Se puede describir como un directorio o una micro-máquina virtual que tiene todo lo necesario para poder hacer funcionar una aplicación y cada uno de estos está completamente aislado del resto que tengamos en un mismo servidor.

### ¿Qué es una Imagen?

Las imágenes podríamos describirlas como un sistema operativo ya instalado con algunas plataformas cargadas y son bases para poder desempeñar el motor de docker ampliamente 

### ¿Qué es docker Hub?

Docker Hub es un repositorio para descargar o subir imágenes ya sean públicas o privadas esta misma tiene servicios automatizados ys e integra con GitHub y Bitbucket

### Registro en Docker Hub

El registro no es necesario para la descarga de imagenes solo para subirlas y guardarlas podemos hacer el registro en la consola con un simple comando que es: docker login

### Instalación de docker en ubuntu

Para la instalación de docker en ubuntu simplemente es seguir los siguientes comandos:

    sudo apt update && sudo apt dist-upgrade -y 
    sudo apt install docker.io -y
    sudo usermod -aG docker username

### Sitanxis de docker

Está sintaxis es muy facil es aplicar
    
    docker [opción] [comando] [argumento]
 
las opciones y comandos a utilizar vendrán al final de este repositorio o pueden verificarlos escribiendo docker en la consola

### Descargar imagen, crear contener y correrlo con un comando

Antes de comenzar a caminar podemos correr un poco lo proximo que haremos será crear un contenedor y para ello solo necesitamos el comando "run" esto descargará una imagen, creará el contenedor y lo correra en su sistema operativo, parece una descripción demasiado complicada pero en realidad es más sencillo de lo que se puede pensar, solo necesitamos correr el comando:

    docker run hello-world

esto descargará una imagen llamada hello-world, creará un contenedor y lo correra de forma automatica, en la imagen de abajo podremos ver el resultado que arroja

![hello world](https://github.com/velezz/docker/blob/main/images/docker2.png)

### buscar una imagen

Nos dedicaremos a buscar una imagen y descargarla para tenerla en nuestro ordenador, con calma no es necesesario abrir otra pestaña del navegador para realizar la busqueda todo lo haremos através de la terminal ejecutando el comando

    docker search [imagen a buscar]

en este caso buscaremos una imagen de ubuntu si bien les parece
    
    docker search ubuntu

y tan sencillo como es nos apareceran los resultados en forma de lista con nombre y descripción de la imagen

![docker search ubuntu](https://github.com/velezz/docker/blob/main/images/docker3.png)

ahora si viene la descarga, al haber escogido alguna de las imagenes para descargar podremos hacerlo sin mas ni menos tan sencillo como ejecutar

    docker pull ubuntu

![docker pull ubuntu](https://github.com/velezz/docker/blob/main/images/docker4.png)

que? que como sabremos si realmente se descargo la imagen?
simplemente solo escribimos en la consola 

    docker images

![docker images](https://github.com/velezz/docker/blob/main/images/docker5.png)

es facil aprender docker verdad? si vemos bien la lista veremos la imagen de ubuntu que acabamos de descarga y también la imagen de hello world que descargamos anteriormente

### vamos por más

Como no es suficiente solo descargar y tener las imagenes en nuestro ordenador sin hacer nada, comenzaremos a crear contenedores y personalizarlos a gusto de cada quien

### Crear un contenedor a partir de nuestra imagen ubuntu

Para realizar este paso solo es cuestión de ejecutar 

    docker run -it ubuntu

si, de seguro te estas preguntando ¿De dondé salio el -it? si lo ejecuté anteriormente y blah blah blah
no, -it es un flag (por llamarlo así) y es la abreviatura de iteractive tty (una terminal interactiva) lo cuál podrán ver, al ejecutar el comando nos cambio de usuario y nombre del equipo

![docker run -it ubuntu](https://github.com/velezz/docker/blob/main/images/docker6.png)

como pueden ven en la imagen anterior ahora somos root@9870dfd6c811 lo cuál es el usuario administrador y el id del contenedor creado
varios estarán como ¿que hago, como salgo, entro a otra terminal para poder seguir trabajando en mi maquina?

tranquilidad mis jovenes padawan simplemente escribir un exit en la consola del contenedor para poder salir y regresaran a su terminal muy rápido

si ejecutan docker ps -a  podrán ver que ahí se encuentra su contenedor junto al contenedor anterior de hello-world completamente dormiditos y relajados ahora pondremos a trabajar a ese flojo de nuevo 

### iniciando un contenedor

para poder iniciar el contenedor solo escribimos en la consola 

    docker start [CONTAINER ID] 

este comando activara el contenedor y lo correra nuevamente pero esta vez no estarás en él simplemente podras verlo desde afuera y para verificar que realmente este corriendo deberás escribir docker ps y aparecerá el contenedor iniciado hace algunos minutos
 
Para volver a entrar al contenedor simplemente escribimos el comando docker attach [CONTAINER ID] o también utilizar el comando docker exec -it [CONTAINER ID] bash que "bash" es el comando del contenedor que seguramente observaron y estamos de regreso en el contenedor
ahora podremos aplicar comandos como apt update, apt updgrade, apt install y modificar el contenedor como se te ocurra

### Dentro del contenedor

recuerden que el contenedor en sí es una maquina muy ligera con la distribución elegida así que no tendrá muchas cosas como cuando instalas ubuntu en un ordenador normal así que comenzaremos con unos pequeños comando para tenerlo más personalizada

    apt update
    apt upgrade -y
    apt install -y net-tools
    ifconfig

otra manera de salir cuanto entras con el comando attach es presionar ctr + p + q ya que si intentas salir con el comando exit este mismo detendra el contendor pero si entras en un principio con el comando exec -it para entrar puedes salir con el comando exit sin detener el contenedor

### Deteniendo/eliminando un contenedor


