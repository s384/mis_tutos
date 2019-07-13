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

. ~/Documents/Entornos/laboon/bin/activate.fish

Para abreviarlo debemos ejecutar 
~~~
alias nombre_abreviacion='comando a abreviar'
alias vir_laboon='. ~/Documents/Entornos/laboon/bin/activate.fish'
~~~
Una vez echo esto, grabamos el comando para que al reiniciar la terminal, este siga funcionando, ejecutamos
~~~
funcsave nobmre_abreviacion
funcsave vir_kalem
~~~
Ahora al reiniciar la terminal solamente ejecutamos vir_laboon

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
