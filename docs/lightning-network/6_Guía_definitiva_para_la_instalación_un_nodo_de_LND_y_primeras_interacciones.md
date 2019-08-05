![nodes-map](../images/lightning-network/lightning-network-nodes-map.png?raw=true)

# Nuestro duro caminar por el desierto

Como se puede ver en la guía 6, 'Comandos para desplegar LND', mi compañero Víctor y yo estuvimos probando la testnet de la Lightning Network usando neutrino como cliente de bitcoin. Y aquí viene la serie de intentos fallidos y de horas invertidas en estas pruebas, que espero de veras ahorraros con esta guía.

El gran problema que no tuvimos en cuenta es que en la Lightning Network hay principalmente dos tipos de nodos, los públicos y los privados u ocultos. Pues bien, cuando usamos un proveedor de wallets móviles como por ejemplo es Eclair, lo que nos dan es un nodo privado. Esto quiere decir que ningún nodo se puede conectar directamente a tu nodo, y que la única forma que tienes de comunicarte con el mundo exterior es abriendo canales con hubs o cualquier nodo público. <u>Sólo</u> a través de ellos puedes realizar las transacciones que quieras.

Esto no debería haber sido tanto problema, pero se complicó cuando descubrimos que el nodo que explicamos cómo desplegar en la sección/guía 6 con neutrino también era uno oculto. Por lo tanto, solo podíamos comunicar nuestros nodos a través de otros, y no podíamos abrir canales entre nosotros dos, solo con los públicos de la lightning-community, ACINQ, etc.

Por qué el nodo de la testnet con neutrino estaba oculto por defecto es algo que nos queda por investigar, porque en teoría no debería ser así.

Al final, decidimos cortar por lo sano y hacer un nodo completo (con bitcoin como tal como cliente) en mainnet.

He aquí todos los pasos para hacerlo.

## Más Notas

Puesto que no tenía en ese momento los recursos necesarios y también para asegurarme de tener una IP fija, realicé esta instalación en un VPS de Contabo (https://contabo.com/?show=vps).

No quiero hacerles publicidad pero es verdad que hacen el apaño y tienen buen precio. En cuanto tenga algún problema con ellos actualizaré por aquí.

Escogí el VPS 700, con 700GB de disco duro SSD-boosted (no SSD <i>per se</i>), 4 cores y 10GB de RAM. Aunque en principio el VPS M SSD promete mejor rendimiento. Éste no lo he probado, pero parece una oferta mejor, y aquí también cabría el nodo de bitcoin y la Lightning (tiene 400GB de disco SSD 100%).




# Instalar bitcoin

1. Intalando el cliente

Comandos para instalar bitcoind:
```
sudo apt-add-repository ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get install bitcoind
```

Lo arrancamos una vez con `bitcoind` para que nos genere la carpeta `.bitcoin` en $HOME.

2. El archivo de configuración.
A continuación, creamos nuestro archivo de configuración en esta carpeta. Aquí el template que he usado yo:
```
server=1
txindex=1
daemon=1
externalip=<tu-ip-externa>
maxconnections=10
rpcuser=<tu-nombre-de-usuario>
rpcpassword=<tu-password>
minrelaytxfee=0.00000000
incrementalrelayfee=0.00000010
zmqpubrawblock=tcp://127.0.0.1:28332
zmqpubrawtx=tcp://127.0.0.1:28333
```

hacemos
```
nano ~/.bitcoin/bitcoin.conf
```
y pegamos el template completándolo con nuestros valores.

3. Sincronización.
Ahora tenemos que dejar el nodo sincronizando:
```
bitcoind
```
Podemos seguir el proceso se sincronización (a mí en el VPS 700 me llevó 14 horas aproximadamente) con este comando:
```
tail $HOME/.bitcoin/debug.log
```

4. Bitcoin como un servicio.

Antes o después de que se sincronice, convertimos bitcoin en un servicio de nuestro sistema. Esto es bueno porque así siempre se arrancará bitcoin junto con nuestro equipo, y podemos monitorearlo con `sudo journalctl -f -u bitcoind`.

Para hacerlo, primero paramos el nodo de bitcoin:
```
bitcoin-cli stop
```
Y creamos el archivo de configuración de bitcoin como servicio:
```
sudo nano /etc/systemd/system/bitcoind.service
```
Aquí pegamos esta configuración:
```
[Unit]
Description=Bitcoin daemon
After=network.target

[Service]
Type=forking
User=<tu-nombre-de-usuario>
WorkingDirectory=/home/USERNAME
PIDFile=/home/USERNAME/.bitcoin/bitcoind.pid
ExecStart=/usr/bin/bitcoind -conf=/home/USERNAME/.bitcoin/bitcoin.conf -pid=/home/USERNAME/.bitcoin/bitcoind.pid
KillMode=process
Restart=always
TimeoutSec=120
RestartSec=30

[Install]
WantedBy=multi-user.target
```
Ahora habilitamos bitcoin como servicio y la arrancamos con:
```
sudo systemctl enable bitcoind
sudo systemctl start bitcoind
```

Ya no hace falta que arranquemos el nodo de bitcoin cada vez que encendamos el equipo. Es un servicio que va ligado automáticamente a nuestro sistema.
Si hacemos `sudo systemctl status bitcoind` veremos que está efectivamente activo aunque no hayamos arrancado el nodo con `bitcoind`. Con el comando `journalctl` tenemos acceso a todos los logs.

Así termina el apartado para instalar bitcoin.

Una vez tengamos nuestro nodo sincronizado (14 horas aproximadamente, a fecha de julio del 2019) será el momento de arrancar nuestro nodo de Lightning. Primero lo vamos a instalar.
Aunque antes de nada necesitamos go instalado.




# Instalar GO (necesario para LND)

Instalar go es muy sencillo. Básicamente nos descargamos el archivo tar que contiene todo lo necesario y luego lo metemos en nuestro PATH, en el archivo `~/.profile`.

Vamos a verlo.

1. Descargamos el archivo tar:
```
wget https://dl.google.com/go/go1.12.7.linux-amd64.tar.gz
```
y lo abrimos
```
tar xvf go1.12.7.linux-amd64.tar.gz
```
La 1.12.7 es la versión más reciente en el momento en que se escribe esta guía. Comprobad la última versión estable de go en su página oficial: https://golang.org/

Ahora podemos borrar el tar, ya no lo queremos para nada.
```
rm go1.12.7.linux-amd64.tar.gz
```

2. Copiamos la carpeta go a /usr/lib/.
```
sudo cp -r go /usr/lib/
```
También se suele copiar a /usr/local/ como alternativa.

3. Metemos go en nuestro path.
```
nano ~/.profile
```

Como últimas líneas, pegamos:
```
export GOROOT=/usr/lib/go
export GOPATH=$HOME/go
export GOBIN=$GOPATH/bin
export PATH=$PATH:$GOROOT/bin:$GOBIN
```

Guardamos, salimos, y hacemos
```
source ~/.profile
```

Comprobamos la instalación con `go version`. Deberíamos recibir el siguiente output: `go version go1.12.7 linux/amd64`




# Instalar Lightning Network (ahora sí)

Vamos a usar de nuevo el cliente `lnd` de Lightning, escrito en go (de ahí el paso anterior).

Otro cliente muy popular es `c-lightning`, de Blockstream, escrito naturalmente en C y que solo funciona en Linux. También haremos pruebas con este cliente pero de momento nos ceñiremos a `lnd`.

Nos lo descargamos y lo instalamos:
```
go get -d github.com/lightningnetwork/lnd
cd $GOPATH/src/github.com/lightningnetwork/lnd
make && make install
```

Ya está. Este paso era el más sencillo.

Comprobamos la instalación con
```
lnd --version
```



# Usando la Lightning Network

1. Arrancar el nodo y parámetros a tener en cuenta (mainnet)

Para arrancar correctamente nuestro nodo de Lightning con todos sus parámetros tenemos dos opciones. O bien creamos un archivo lnd.conf en la carpeta `~/.lnd` o lo arrancamos directamente con todos los parámetros. 

```
lnd --bitcoin.active --bitcoin.mainnet --debuglevel=debug --bitcoin.node=bitcoind --bitcoind.rpcuser=REPLACEME --bitcoind.rpcpass=REPLACEME --externalip=X.X.X.X --bitcoind.zmqpubrawblock=tcp://127.0.0.1:28332 --bitcoind.zmqpubrawtx=tcp://127.0.0.1:28333
```

Si lo hiciéramos con el archivo `lnd.conf`:
```
nano ~/.lnd/lnd.conf
```
y dentro escribimos:

```
[Application Options]
debuglevel=debug
externalip=x.x.x.x

[Bitcoin]
bitcoin.active=1
bitcoin.node=bitcoind
bitcoin.mainnet=1

[Bitcoind]
bitcoind.rpcuser=<tu-nombre-de-usuario>
bitcoind.rpcpass=<tu-password>
bitcoind.zmqpubrawblock=tcp://127.0.0.1:28332
bitcoind.zmqpubrawtx=tcp://127.0.0.1:28333
```

Otra opción sería crear un script con el comando anterior y todos sus parámetros. Cualquiera de estas opciones dará el mismo resultado.

2. Crear una wallet.

Por último, solo nos falta crear nuestra wallet en nuestro nodo de Lightning para empezar a hacer uso de él. Hacemos `lncli create` y pasamos por el siguiente proceso, en el cual se nos pide una contraseña para encriptar nuestra wallet y también si queremos usar una <i>seed phrase</i> que ya tengamos o, por el contrario, que nos la cree de cero.

```
Input wallet password
Confirm password

Do you have an existing cipher seed mnemonic you want to use? (Enter y/n):
Input your cipher seed passphrase (press enter if your seed doesn't have a passphrase):
Input an optional address look-ahead used to scan for used keys (default 2500): 

!!!YOU MUST WRITE DOWN THIS SEED TO BE ABLE TO RESTORE THE WALLET!!!

lnd successfully initialized
```

Una vez tengamos el último mensaje, `lnd successfully initialized`, ya está todo preparado. Lo único a tener en cuenta es que, cada vez que paremos el nodo de Lightning, será necesario hacer `lncli unlock` y meter esa contraseña con la que hemos encriptado nuestra wallet de Lightning.

Por eso, aunque en realidad podemos hacer con `lnd` igual que hemos hecho con `bitcoind` y configurarlo también como un servicio, en realidad no es posible hacerlo igual porque el nodo, al arrancar, siempre nos va a pedir esta contraseña, y tendremos que hacer manualmente `lncli unlock`.

De todas formas, existe una forma de hacer esto a través del correo electrónico, pero lo explicaré en la sección `Bonus Track`.

3. Conectarnos, abrir un canal, crear y enviar invoices.

Después de todos estos pasos por fin hemos llegado a donde queríamos estar. Ya tenemos nuestro nodo de Lightning Network y estamos preparados para empezar a jugar con él.

Antes de nada, al ser nosotros un nodo público, podemos pedir a los demás que se conecten a nosotros, en lugar de como hicimos en la guía 6, que nos teníamos nosotros que conectar forzosamente a los demás.

Los pasos que voy a explicar ahora son haciendo la parte contraria que no se explicó en la guía 6. Es decir, en vez de conectarnos nosotros a un nodo, dejamos que se conecten a nosotros. Y, en lugar de enviar un pago para abrir un canal, creamos nosotros el invoice y se lo pasamos a nuestros peers para que sean ellos los que lo paguen y abran el canal.

1. Dejar que se conecten a nosotros.
Para conectarse a nuestro nodo, solo tenemos que pasar nuestra URI. La consultamos haciendo:
```
lncli getinfo
```
y es el valor último del JSON que aparece, `uris`.

La node-uri se compone por: id-del-nodo@ip:puerto

El puerto por defecto es el 9735 para el cliente `lnd`.

Una vez se conecten a nosotros, podemos ver nuestros nuevos peers con `lncli listpeers`.

2. Crear el invoice o factura y compartirlo.

Creamos el invoice con `lncli addinvoice`. Este comando acepta muchísimos parámetros, que podemos analizar con `lncli addinvoice -h`, pero si queremos dejar al libre albedrío de quien reciba nuestra factura cuánto pagar, hacemos simplemente:
```
lncli addinvoice --memo "Tutorial de Lightning Network"
```
Para poner un mínimo a pagar añadiremos `--amt` y el número de satoshis a pagar.

Para compartir nuestro invoice el valor clave es `"payment-request"`. Aparece en el JSON que se genera con el comando anterior, `lncli addinvoice`, o bien lo podemos consultar posteriormente con el comando `lncli listinvoices`. Siempre empieza por `ln`.

Esto sirve si a quien se lo quieres pasar también está usando un terminal o alguna interfaz gráfica que lo permita. Sin embargo, si es una wallet de móvil lo que usa, lo más sencillo es convertir `payment-request` en un código QR. Para ello, instalamos qrencode con `sudo apt install qrencode` y lo pegamos el hash de `payment-request` en un archivo de texto vacío: 
```
nano ~/payment-request-1
```
y hacemos
```
cat <payment-request-1> | qrencode -l L -o qr.png
```

Ese `qr.png` servirá para que todos aquellos que tienen wallets móviles puedan responder solo escaneándolo a nuestro invoice.

Una vez ellos realicen el pago de ese invoice, podremos ver cómo se está formando el canal entre ambos nodos haciendo `lncli pendingchannels`.

Por último, una vez esté creado, podemos consultar toda la infomación de ese canal con `lncli listchannels`.

En el valor de `local balance` podemos ver cuánto nos ha pagado ese nodo. Así como la capacidad total del canal, que es el saldo de la address de bitcoin detrás de ese nodo de Lightning.


![local-balance](../images/lightning-network/local-balance.jpg?raw=true "Local Balance")

Tened en cuenta este importante detalle. Vuestra address de bitcoin se mantiene en el anonimato, pero su balance será visible para los nodos a los que os conectéis directamente (aunque no a todos los lo hagáis indirectamente).

Para pagar nosotros un invoice, tal y como se explicó en la guía anterior, haremos simplemente:
```
lncli sendpayment --pay_req=<hash_del_invoice>
```

Para cerciorarnos de la cantidad que estamos mandando, antes de hacer `sendpayment` podemos ejecutar
```
lncli decodepayreq <hash_del_invoice>
```

Y para ver la lista de todos los pagos realizados, haremos, como resulta intuitivo, `lncli listpayments`.



# Bonus Track



1. Configurar `lnd` como un servicio gracias a supervisor.

Primero paramos `lnd` e instalamos supervisor.
```
sudo apt install supervisor
```
A continuación creamos otro archivo de configuración de `lnd` como configuración añadida para supervisor (tal y como se hace con apache o nginx, si los conocéis):
```
cd /etc/supervisor/conf.d
sudo nano lnd.conf
```
Añadimos esto a `lnd.conf`:
```
[program:lnd]
user=REPLACE-WITH-YOUR-USERNAME
command=/home/USERNAME/go/bin/lnd --configfile=/home/USERNAME/.lnd/lnd.conf
startretries=999999999999999999999999999
autostart=true
autorestart=true
```

Y volvemos a abrir supervisor:
```
sudo supervisorctl reload
```
Todos los logs los podemos ver haciendo
```
sudo tail /var/log/supervisor/lnd-std...
```
Si hay algún error encontraremos un lnd-stderr en este directorio que nos explicará qué error ha habido.

Si todo va bien, tendremos que hacer `lncli unlock` para arrancar `lnd` con supervisor.

Para ser notificados por e-mail cada vez que se reinicie supervisor (en caso de que algo falle en la máquina y se reinicia, por ejemplo), instalamos el plugin `superlance`:
```
sudo apt-get install python-pip
sudo -H pip install superlance
```
Editamos el archivo de configuración principal de supervisor:
```
sudo nano /etc/supervisor/supervisord.conf
```
Añadimos, cambiando por nuestro e-mail:
```
[eventlistener:crashmail]
command=/usr/local/bin/crashmail -p lnd -m TU@CORREO.ELECTRÓNICO
events=PROCESS_STATE
```
A continuación actualizamos supervisor para que recoja la nueva configuración, lo cual también reiniciará `lnd`:
```
sudo supervisor update
```
Y volvemos a hacer, por supuesto, `lncli unlock`.

Así, aunque no podamos automatizar realmente el reinicio de `lnd` porque hay que introducir la clave de la wallet, pero al menos seremos notificados por mail cuando haya que hacerlo y podemos quedarnos más tranquilos, sabiendo que, si cae nuestro nodo, recibiremos un mail de alerta.



## Notas finales

Hasta aquí de momento esta guía definitiva. Con estos pasos ya tendríais lo básico para empezar a moveros dentro de la Lightning Network. Pero por supuesto aún queda mucho por investigar. Iremos sacando más y mejores guías.

Tan solo señalar algunos de los recursos que han ayudado muchísimo en la creación de esta guía.

Por un lado, [la guía clásica y mítica de bretton](https://gist.github.com/bretton/0b22a0503a9eba09df86a23f3d625c13)

Esta guía me ayudó muchísimo a la hora de instalar bitcoin. Por supuesto, hay cosas que ya están desactualizadas, pero sigue siendo una gran referencia.

También [este artículo de Medium donde se dan todas las claves para enviar y recibir pagos](https://medium.com/@marcdown/lightning-payments-with-lnd-25a3b7764bcb)

Y también gracias al equipo de Locha Mesh por su ayuda en todo momento, sobre todo cuando no conseguíamos que se conectasen el nodo de neutrino y en de Eclair en el móvil ¡Gracias chicos!