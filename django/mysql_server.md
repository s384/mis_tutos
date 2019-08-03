
# Mysql server en Deepin

## Mysql-server
Tenemos la opcion de descargar mysql-server desde la pagina de mysql o instalarlo desde los repositorios, este ultimo es el recomendado y el que vamos a explicar.
~~~
	sudo apt update && sudo apt install mysql-server
~~~

## Post instalacion

Ejecutamos para establecer la contraseña de root, **leer todo lo que pregunta**.
~~~
	mysql_secure_installation
~~~

## No puedo acceder con el usuario root

### Opcion 1

- Abrimos el `archivo 50-server.cnf` ubicado en `/etc/mysql/mariadb.conf.d/`

** Puedes abrirlo como administrador en el gestor de archivos o por consola, lo que te acomode, yo lo explicare por consola **

~~~
    sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf
~~~

- Agregamos `skip-grant-tables` bajo [mysqld]
~~~
    # this is only for the mysqld standalone daemon
    [mysqld]
    skip-grant-tables
~~~

- Guardamos los cambios `Ctrl + O` y cerramos el archivo `Ctrl + X`
- Reiniciamos el servicio de mysql
~~~
    sudo service mysql restart
~~~

- Nos conectamos a la terminal de mysql, en caso de pedir pass, solo damos enter
~~~
    mysql -u root -p
~~~

- Actualizamos los privilegios
~~~
    flush privileges;
~~~

- Cambiamos el medio de autenticacion del usuario root
~~~
    update mysql.user set plugin = 'mysql_native_password' where User='root';
~~~

- Actualizamos la password
~~~
    ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';
    Reemplazar new_password por la contraseña deseada
~~~

* Si esta orden falla, probamos esta otra
~~~
    UPDATE mysql.user SET authentication_string = PASSWORD('new_password') WHERE User = 'root' AND Host = 'localhost';
    Reemplazar new_password por la contraseña deseada
~~~

- Actualizamos los privilegios
~~~
    FLUSH PRIVILEGES;
~~~

- Abrimos nuevamente el archivo 50-server.cnf ubicado en /etc/mysql/mariadb.conf.d/

~~~
    sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf
~~~

- Eliminamos la linea `skip-grant-tables`, guardamos `Ctrl + O` y cerramos `Ctrl + X`
~~~
    # this is only for the mysqld standalone daemon
    [mysqld]
    skip-grant-tables
~~~

- Reiniciamos el proceso de mysql
~~~
    sudo service mysql restart
    En caos de esto no funcionar. Reiniciar el pc
~~~

- Probamos que funciono y listo, ahora podemos accesder como root
~~~
    mysql -u root -p
~~~



### Opcion 2

- Detenemos el servicio de mysql
~~~
    sudo systemctl stop mysql
    o
    sudo systemctl stop mariadb
~~~

- Iniciamos el servicio en modo seguro
~~~
    sudo mysqld_safe --skip-grant-tables --skip-networking &

    Al ejecutar este comando nos iniciara un servicio de mysql en segundo plano, por lo que le damos enter y seguimos usando la terminal
~~~

- Accedemos a la consola de mysql para realizar el cambio de password
~~~
    mysql -u root
~~~

- Realizamos el cambio de password
~~~
    ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';
   Reemplazar new_password por la contraseña deseada
~~~

* Si esta orden falla, probamos esta otra
~~~
    UPDATE mysql.user SET authentication_string = PASSWORD('new_password') WHERE User = 'root' AND Host = 'localhost';
    Reemplazar new_password por la contraseña deseada
~~~

- Actualizamos los privilegios
~~~
    FLUSH PRIVILEGES;
~~~

- Reiniciamos el proceso de mysql
~~~
    sudo service mysql restart
    En caos de esto no funcionar. Reiniciar el pc
~~~

- Probamos que funciono y listo, ahora podemos accesder como root
~~~
    mysql -u root -p
~~~

## Ahora si estas dos maneras no os han funcionado, puedes pasar a la opcion tres
# Prender fuego al ordenador
