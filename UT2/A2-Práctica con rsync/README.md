<center>

# Práctica con rsync


</center>

***Hugo Suárez Pérez:***

***Curso:*** 2º de Ciclo Superior de Administración de Sistemas Informáticos en Red.

### ÍNDICE

+ [Introducción](#id1)
+ [Objetivos](#id2)
+ [Material empleado](#id3)
+ [Desarrollo](#id4)
+ [Conclusiones](#id5)


#### ***Introducción***. <a name="id1"></a>

rsync es una aplicación libre para sistemas de tipo Unix y Microsoft Windows que ofrece transmisión eficiente de datos incrementales, que opera también con datos comprimidos y cifrados. Mediante una técnica de delta encoding, permite sincronizar archivos y directorios entre dos máquinas de una red o entre dos ubicaciones en una misma máquina, minimizando el volumen de datos transferidos. Una característica importante de rsync no encontrada en la mayoría de programas o protocolos es que la copia toma lugar con sólo una transmisión en cada dirección. rsync puede copiar o mostrar directorios contenidos y copia de archivos, opcionalmente usando compresión y recursión.

Actuando como un daemon de servidor, rsync escucha por defecto el puerto TCP 873, sirviendo archivos en el protocolo nativo rsync o vía un terminal remoto como RSH o SSH. En el último caso, el ejecutable del cliente rsync debe ser instalado en el host local y remoto.

rsync se distribuye bajo la licencia GNU General Public License.

#### ***Objetivos***. <a name="id2"></a>

Cada miembro del grupo debe montar una máquina con sistema operativo Linux  a elegir ( Debian, Ubuntu, etc ) configurándola de la forma siguiente:

Una interfaz de red en modo puente. 
Una IP configurada en modo estático, para ello podemos fijar la dirección MAC  de la máquina haciendo uso de la que ya tenemos reservada en el DHCP.
El  hostname  de cada máquina debe ser 'rsync1' y 'rsync2' 
Comprobar que las máquinas se ven entre sí realizando ping entre ellas.
Compruebe si ambas máquinas tienen instalado y habilitado el protocolo rsync, en caso de que no esté instalado debe proceder a instalarlo y habilitarlo documentando los pasos seguidos.
Una vez configurado el entorno de trabajo se seguirán los pasos siguientes  pasos para comprender el funcionamiento del protocolo rsync:

En la primera máquina virtual ( rsync1 ) construya el directorio: ~/datos
Ejecute el comando: touch datos/fichero-{1..100}.txt
Observe el contenido del directorio datos. Después utilice rsync para sincronizar el directorio datos de la primera ( rsync1 ) a la segunda máquina ( rsync2 ).
Utilice un editor para editar alguno de los 100 ficheros escribiendo en su interior algunas líneas de texto.
Utilice de nuevo rsync para sincronizar el directorio. ¿Se transfieren todos los ficheros?
Borre el fichero datos/fichero-100.txt y sincronice el directorio. 
En el destino ¿existe el fichero?
¿Qué opción se debe utilizar para que en el destino se borren los ficheros que no existen en el origen?
¿Qué debe hacer para sincronizar de manera recursiva el directorio /etc/systemd de la primera máquina a ~/systemd en la segunda máquina?

#### ***Material empleado***. <a name="id3"></a>

Enumeramos el material empleado tanto hardware como software y las conficuraciones que hacemos (configuraciones de red por ejemplo) 

#### ***Desarrollo***. <a name="id4"></a>
Vamos a la máquina virtual 1 y comprobamos que la ip está bien puesta gracias a ponerle la mac.

![](img/b1.png)

Hacemos ping a la otra máquina virtual.

![](img/b2.png)

Le cambiamos el hostname a rsync1 e instalamos el servicio rsync

![](img/b3.png)

En la máquina virtual 2 le ponemos la mac proporcionada por el profedor.

![](img/01.png)

Le cambiamos el hostname.

![](img/02.png)

Comrpobamos ping a la otra máquina virtual.

![](img/03.png)

Instalamos rsync

![](img/04.png)

Instalamos ssh.

![](img/05.png)

Creamos el siguiente fichero y miramos el estado de rsync.

![](img/06.png)

Rsync1 crea la carpeta datos. 

![](img/b4.png)

Pone el siguiente comando para generar 100 archivos.

![](img/b5.png)

Rsync a la otra máquina virtual.

![](img/b6.png)

En rsync2 miramos que se a creado esa carpeta tambien.

![](img/07.png)

Editamos un archivo.

![](img/08.png)

Hacemos rsync a la primera máquina virtual.

![](img/09.png)

Y vemos que se han creado los archivos.

![](img/b7.png)

Con el archivo editado.

![](img/b8.png)

Borrramos el archivo 100.

![](img/b9.png)

Y le mandamos la informacion a la otra máquina virtual para que tambien borre los archivos que ya no estan en nuestra máquina virtual.

![](img/b10.png)

Y vemos que se borra.

![](img/10.png)

![](img/11.png)

Sincronizamos de manera recursiva el directorio /etc/systemd de la primera máquina a ~/systemd en la segunda máquina

![](img/b12.png)

#### ***Conclusiones***. <a name="id5"></a>

Hemos aprendido como instalar rsync y como configurarla para hacerla funcionar.
