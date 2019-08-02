# Instalación de Ghost en el servidor de la colmena

En [su página oficial](https://ghost.org/docs/install/ubuntu/) podéis encontrar más información acerca de la instalación en varias plataformas, en este caso lo explicaremos para [Ubuntu 18.04LTS](https://ubuntu.com).

## Instalación con node

`sudo apt-get install -y nodejs` 

`sudo npm install ghost-cli@latest -g`

## Vamos a configurar la base de datos MySQL:

<pre>
root@web2:/var/www/ghost# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 54
Server version: 5.7.27-0ubuntu0.18.04.1 (Ubuntu)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> create database ghost_prod;
Query OK, 1 row affected (0.00 sec)

mysql> grant all privileges on ghost_prod.* TO 'ghostuser'@'localhost' identified by 'SECRET_PASSWORD';
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)
</pre>

Ahora vamos a crear el usuario y las carpetas necesarias

<pre>
root@web2:/var/www# mkdir ghost
root@web2:/var/www# chown user.ghost ghost
root@web2:/var/www# su user
user@web2:/var/www$ chmod 775 ghost
user@web2:/var/www$ cd ghost
user@web2:/var/www/ghost$ ghost install
</pre>

>mkdocs, version 1.0.4

## Usamos [Material](https://squidfunk.github.io/mkdocs-material/) como tema, lo instalamos:
`pip install mkdocs-material --user`

## Instalamos dependencias:
`pip install md-tooltips --user`

## Clonamos el repositorio:
`git clone https://github.com/Colm3na/DocsColmena.git`

## Nos dirigimos a la carpeta del proyecto, e iniciamos el servidor de desarrollo:
`cd $HOME/DocsColmena/` 

`mkdocs serve`

> Si abrimos el navegador y nos vamos a la página [http://127.0.0.1:8000/](http://127.0.0.1:8000/) podemos ver la documentación.
