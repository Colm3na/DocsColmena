# Instalación de Ghost en el servidor de la colmena

En [su página oficial](https://ghost.org/docs/install/ubuntu/) podéis encontrar más información acerca de la instalación en varias plataformas, en este caso lo explicaremos para [Ubuntu 18.04LTS](https://ubuntu.com).

## Instalación con node

`sudo apt-get install -y nodejs` 

`sudo npm install ghost-cli@latest -g`

## Vamos a configurar la base de datos MySQL:

<pre style="background-color: #bbbbbb; color: green;">
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

Ahora vamos a crear el usuario y las carpetas necesarias.
Necesitamos 2 usuarios. El usuario que hará la instalación y el usuario que ejecutará el servicio.

<pre>
root@web2:/var/www# adduser ghost
root@web2:/var/www# mkdir ghost
root@web2:/var/www# chown user.ghost ghost
root@web2:/var/www# su user
user@web2:/var/www$ chmod 775 ghost
user@web2:/var/www$ cd ghost
user@web2:/var/www/ghost$ ghost install
</pre>

Tras la instalación ghost nos creará un servicio de sistema y tratará de arrancarlo.
En nuestro caso podemos ver el status del servicio de esta manera:

<pre>
root@web2:~# systemctl status ghost_localhost.service 
● ghost_localhost.service - Ghost systemd service for blog: localhost
   Loaded: loaded (/var/www/ghost/system/files/ghost_localhost.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2019-08-02 14:53:23 CEST; 2 days ago
     Docs: https://docs.ghost.org
 Main PID: 648 (ghost run)
    Tasks: 18 (limit: 2294)
   CGroup: /system.slice/ghost_localhost.service
           ├─648 ghost run
           └─679 /usr/bin/node current/index.js
</pre>

Y el contenido del archivo del servicio es el que sigue. Se ha generado automáticamente, así que no tenemos
nada que modificar.

<pre>
root@web2:~# cat /lib/systemd/system/ghost_localhost.service
[Unit]
Description=Ghost systemd service for blog: localhost
Documentation=https://docs.ghost.org

[Service]
Type=simple
WorkingDirectory=/var/www/ghost
User=999
Environment="NODE_ENV=production"
ExecStart=/usr/bin/node /usr/bin/ghost run
Restart=always

[Install]
WantedBy=multi-user.target
</pre>

Ya sólo nos queda configurar un virtualhost para servir el blog en un subdominio:

<pre>
root@web2:~# cat /etc/apache2/sites-available/blog.colmenalabs.org-le-ssl.conf 
<IfModule mod_ssl.c>
    <VirtualHost *:443>
        ServerName blog.colmenalabs.org
        Alias /.well-known /var/www/ghost
	#DocumentRoot /var/www/ghost
        ServerAdmin webmaster@example.com
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

	#RequestHeader set X-Forwarded-Proto https
        ProxyRequests Off
        <Proxy *>
          Order deny,allow
          Allow from all
        </Proxy>
        
        ProxyPass / http://127.0.0.1:2368/
        ProxyPassReverse / http://127.0.0.1:2368/
        ProxyPreserveHost   On

        RequestHeader set X-Forwarded-Proto "https"
        <Location />
          Order allow,deny
          Allow from all
        </Location>


    
SSLCertificateFile /etc/letsencrypt/live/www.colmenalabs.org/fullchain.pem
SSLCertificateKeyFile /etc/letsencrypt/live/www.colmenalabs.org/privkey.pem
Include /etc/letsencrypt/options-ssl-apache.conf
</VirtualHost>
</IfModule>
</pre>

Cómo podéis observar este subdominio funciona mediante un proxy inverso al
puerto 2368, que es donde nuestro servicio Ghost está esperando conexiones.

También hemos necesitado configurar un servidor de correo para que gestione
las altas de usuarios, recuperaciones de claves etc...

En este caso hemos utilizado el servicio MailGun, que ofrece hasta 10k emails/més
de forma gratuita.

El archivo de configuración que tenemos que tocar en este caso está en la carpeta
/var/www/ghost/

<pre>
{
  "url": "http://localhost:2368/",
  "server": {
    "port": 2368,
    "host": "127.0.0.1"
  },
  "database": {
    "client": "mysql",
    "connection": {
      "host": "localhost",
      "user": "ghostuser",
      "password": "CONTRASEÑA-DE-MYSQL",
      "database": "ghost_prod"
    }
  },
  "mail": {
    "transport": "SMTP",
    "options": {
      "service": "Mailgun",
      "host": "smtp.eu.mailgun.org",
      "auth": {
        "user": "postmaster@mg.colmenalabs.org",
        "pass": "CONTRASEÑA-DEL-SMTP"
      }
    },
    "from": "'Colmena Blog' <blog@colmenalabs.org>"
  },
  "logging": {
    "transports": [
      "file",
      "stdout"
    ]
  },
  "process": "systemd",
  "paths": {
    "contentPath": "/var/www/ghost/content"
  },
  "bootstrap-socket": {
    "port": 8000,
    "host": "localhost"
  }
}
</pre>


