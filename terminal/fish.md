# Fish para Deepin Os

## Instalacion de Fish

Si ya tienes instalado el repositorio de deepines es solo ejecutar los siguientes comandos, caso contrario lo primero que debes hacer es instalar el repositorio siguiendo los pasos indicados en [Deepines](https://xn--deepinenespaol-1nb.org/repositorio/)

~~~
sudo apt  update  && sudo apt  install  fish
~~~


## Configurar como predeterminado

Basta con ejecutar el siguiente codigo

~~~
chsh -s /usr/bin/fish
~~~

Si quieres recuperar tu terminal predeterminada debes ejecutar

~~~
chsh /bin/bash
~~~
## Instalando Oh-my-fish (omf)

Ejecutamos

~~~
curl -L https: //get.oh-my.fish | fish
~~~
## Comando de omf

Los comandos a utilizar son

~~~
omf update /actualiza los paquetes oh-my-fish instalados/
omf theme /repositorio muestra los temas  instalados  y  disponibles  para descargar/
omf install  <nombre-paquete-a-instalar>
omf remove <nombre-paquete-a-borrar>
omf theme <nombre-theme> /Para activar el theme/
~~~
## Alias en fish

Un alias en una manera de abreviar un comando, veamos el siguiente ejemplo

~~~
sudo apt update && sudo apt full-upgrade
~~~

Para abreviarlo debemos ejecutar 

~~~
alias nombre_abreviacion='comando a abreviar'
alias upgrade='sudo apt update && sudo apt full-upgrade'
~~~

Una vez echo esto, grabamos el comando para que al reiniciar la terminal, este siga funcionando, ejecutamos

~~~
funcsave nobmre_abreviacion
funcsave upgrade
~~~

Ahora para ejecutar el comando solo basta tipear upgrade

Tambien podemos darle parametros a los comandos

~~~
sudo apt update && sudo apt install dexter-icon-theme
~~~

Ahor debemos agregar el $1 al comando, esto quiere decir que recibira un parametro

~~~
alias install='sudo apt update && sudo apt install $1'
funcsave install
~~~

Entonces al ejecutar el comando solo debemos tipear

~~~
install dexter-icon-theme
~~~

## Shortcut en fish

- Flecha izquierda: autocompleta la linea completa que estas escribiendo
- alt + Flecha izquierda: Completa solo la palabra que estas escribiendo
- Ctrl+Shift+C:	para copiar 
- Ctrl+Shift+V: para pegar
- Ctrl+A: lleva el cursor al inicio de la línea de comandos.
- Ctrl+E: lleva el cursor al final de la línea de comandos.
- Ctrl+W: borra la palabra inmediatamente antes del cursor.
- Ctrl+Z: suspende la ejecución del proceso que se está ejecutando y lo pone en segundo plano, con el comando fg podremos volver a continuar su ejecución.
- Ctrl+Shift+F: Buscar alguna palabra en la pantalla del terminal.
- Ctrl+Shift+J: Dividir pantalla del terminal verticalmente.
- Ctrl+Shift+H: Dividir pantalla del terminal horizontalmente.


## Entornos virtuales (python)

Debemos instalar pip de manera global para utilizar virtualfish

~~~
sudo apt install python3-pip
sudo pip3 install virtualfish
~~~

Reiniciamos la terminal
~~~
exec fish
~~~

Procedemos a crear los entornos

~~~
vf new <nombre-del-entorno>
~~~

Si es el primer entorno, nos consultara si queremos crear el directorio .virtualenvs, confirmamos y creamos el directorio

### Comandos de vf

~~~
vf new [<options>] <envname> - Crea un entorno virtual.
vf ls - Lista los entornos virtuales disponibles.
vf activate <envname> - Activa el entorno virtual.
vf deactivate - Desactiva el entorno virutal.
vf rm <envname> - Elimina el entorno virtual.
~~~
