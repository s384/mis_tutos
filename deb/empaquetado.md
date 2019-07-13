# Empaquetado .deb

## Desempaquetar

~~~
dpkg-deb --extract <Nombre-paquete> <Ubicacio-extraccion>
dpkg-deb --extract laboon-access.deb ./laboon
dpkg-deb --control laboon-access.deb ./laboon
~~~
`--extract` nos extraera todo el contenido del paquete en la carpeta laboon

`--control` nos extraera el archivo de configuracion que es requisito para empaquetar un .deb, este se extrae en una carpeta llamada DEBIAN dentro del directorio

## Empaquetar
Lo primero que debemos hacer es crear un directorio para crear la estructura.
### Estructura del directorio
~~~ 
mkdir empaquetado 
~~~
Dentro de este directorio debemos colocar los archivos tal cual queremos que esten ubicados en el sistema.

En este ejemplo empaquetaremos Laboon Access, para esto tenemos que crear el directorio dentro de empaquetado, por lo que quedaria de la siguiente manera:
- empaquetado
	- DEBIAN
	- usr
		- share
			- applications
			- doc
				- laboon-access
			- icons
				- `<Directorio-tema-iconos>`
			- Laboon

`DEBIAN`	Directorio que almacena el archivo de configuracion del deb.

`applications`	Directorio donde se almacenan los accesos directos a los programas.

`doc`	Directorio donde se almacenara el copyright de la aplicacion, este esta almacenado en un subdirectorio con el nombre de la app.

`icons`	Directorio con los iconos de los temas instalados, en esta seccion debemos crear el directorio para el tema que llevara el icono de la app.

`Laboon`	Directorio con los archivos de la app.

### Creando el archivo de control

Dentro del directorio DEBIAN debemos crear un archivo de texto plano, sin extencion. Esto puede ser por medio de la consola `nano CONTROL` o bien con el explorador de archivos.

Dentro de este archivo debemos colocar lo siguiente:
~~~
Package: laboon-access
Version: 1.3
Installed-Size: 126600
Maintainer: SebTrujillo <correo@correo.com>
Section: admin
Homepage: https://github.com/s384/LaboonAccess
Architecture: amd64
Description: Bloqueo de paginas web por medio del archivo host
 Aplicacion para el bloqueo de sitios web mediante el archivo host, este tambien puede activar el dns de opendns para agregar una capa de proteccion mas amplia.
~~~

Aqui tenemos varios campos que son obligatorios:

`Package`	Nombre del paquete, si este sera subido a un repositorio, no colocar mayusculas

`Version`	Version del paquete

`Maintainer`	Nombre del mantenedor de la app, el formato es `Nombre <correo>`

`Description`	Descripcion de lo que hace la app, la primera linea es una descripcion corta, la segunda linea debe comenzar con un espacio en blanco y esta corresponde a una descripcion larga de la app

Los demas campos son opcionales, puedes encontrar mas info en el [siguiente enlace](https://linux.die.net/man/5/deb-control)

### Empaquetando
Una vez lista la estructura del directorio y el archivo control dentro de DEBIAN, procedemos a empaquetar.
~~~
dpkg-deb --build <directorio-a-empaquetar> <nombre-paquete>
dpkg-deb --build ./empaquetado Laboon-Access.deb
~~~

Una vez termine, veremos el paquete.deb listo para ser distribuido.