# Mysqlclient

## Requisitos

Para poder instalar mysqlclient debemos instalar unos paquetes.
~~~
	sudo apt update && sudo apt install python3-dev default-libmysqlclient-dev 
~~~

## Mysql-server
Tenemos la opcion de descargar mysql-server desde la pagina de mysql o instalarlo desde los repositorios, este ultimo es el recomendado y el que vamos a explicar.
~~~
	sudo apt update && sudo apt install mysql-server
~~~

Post instalacion debemos ejecutar para establecer la contraseña de root, **leer todo lo que pregunta**.
~~~
	mysql_secure_installation
~~~
**Si esto no le funciona. Revisar el archivo mysql_server**

## Instalacion Mysqlclient

Ahora estamos en condiciones de instalar mysqlclient.
~~~
	pip install mysqlclient
    pip install mysqlclient==1.3.2 #si deseas una version especifica
~~~

## Configurando nuestro proyecto

En el archivo settings.py debemos dirigirnos a la seccion **DATABASES** y modificar lo que viene por defecto que es sqlite.
~~~
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'db_name', #Nombre de la base de datos
        'USER': 'user_mysql', #Usuario de mysql
        'PASSWORD': 'user_password', #Clave del usuario
        'HOST': 'localhost', #Ip del servidor
        'PORT': '3306', #Puerto establecido /por defecto 3306
    }
}
~~~