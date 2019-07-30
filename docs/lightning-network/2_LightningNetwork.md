# __[Lightning Network](https://lightning.network/): la capa de _Cash_ sobre Bitcoin__

__LN__ es la primera implementación de __Segwit__, que ha llevado más de 3 años _(un poco como el huevo y la gallina)_ en el que han participado no solo la Start-Up que la pensó llamada ___Lightning Labs___. Sino muchas otras empresas. _Como dato curioso, se creó un consorcio temporal a principios de año entre los departamentos de calculo computacional de las 70 universidades más potentes del mundo con la intención de valorar la viabilidad del proyecto._

El funcionamiento es el siguiente: utilizando el espacio, del campo de notas, que nos da __SegWit__, abrímos una transacción y metemos un trozo de Smart contract. En un bloque futuro cerraremos la transacción con el resto del Smart contract. Eso significa que gastaremos el doble en tasas para realizar una transacción. Lógicamente esto solo es perder dinero y encima de manera más complicada.

La primera utilidad viene porque: entre uno y otro paso, podremos hacer múltiples transacciones, en una u otra dirección, en lugar de realizar una transacción única. _Por ejemplo imaginemos un contrato dónde se paga por comisión y se cobra algún tipo de material gastado durante el proceso. Se abriría un canal por ejemplo de 1000 € y cada vez que se cumplirá el objetivo se traspasaría el beneficio directamente y cada vez que se rompiera una herramienta por ejemplo se cobraría en la dirección contraria la cantidad de la reparación. Al terminar un periodo se cerraría el contrato quedando ajustado al final la cantidad exacta que se ha traspasado de una dirección a la otra y eliminando todas las transacciones intermedias que no son necesarias para terceros._

La utilidad real, viene dada, por el enrutamiento de todos los canales entre sí. De esta forma, al crear un canal entre dos personas, no solo pueden transmitir dinero entre ellas, sino entre las comunidades que ambas personas tienen detrás. Además el dinero no tiene que ir por un solo camino, de manera que si el canal no permite transmitirlo todo, se dividirá y parte recorrerá caminos más largos para transmitirlo completamente.

Todo el dinero que pase por un canal que tú has creado te da unas tasas por hacerlo. De esta forma, se están creando núcleos que están muy bien conectados y qué esperan cobrar un buen dinero en tasas, de una manera similar a como ocurre con las empresas de minería. Sin embargo, en este caso, no estamos hablando de la necesidad de comprar equipo o gastar electricidad, pues solo es necesario tener cantidades congeladas haciendo ___stake___ en forma de canales.

Como creador de un canal: aseguras que como máximo moverás esa cantidad de dinero que tienes en ___stake___, a la cual se le deben restar la apertura y cierre del __State Channel__. En caso de que hagas algo malicioso, es ese dinero el que responderá en tu lugar.

Son los mineros de la Capa 1, es decir de __Bitcoin__, los que aseguran mediante __Proof of Work__ la apertura y cierre de canal.

Esto significa que tenemos una capa 1 con una seguridad desproporcionada y una capa 2 con una seguridad completamente disgregada y asegurada. No hay necesidad de montar capas de proof of work encima o detener nuevos dispositivos haciendo caros procesos.

Lightning es permissionless:
- No se necesita pedir por una cuenta
- No pueden cerrarte la encuentra
- No hay cierra ningún días
- Ni tiene limitaciones geográficas

Aún así, correr un nodo público de Lightning Network tiene requisitos:
- __High Uptime:__ se requiere estar online para poder enrutar los pagos
- __Hot Wallet:__ necesitaremos tener la clave secreta en dicho dispositivo para firmar
- __Continuous Backups:__ si perdemos la BD de tx, perdemos los fondos

_______________________________
## __PRÁCTICA__

Hay dos formas de usarlo la  y más fácil es la que vamos a utilizar hoy qué consiste en descargarse una aplicación llamada [Eclair](https://github.com/ACINQ/eclair/releases) que permite usarlo directamente tirando de un nodo completo que está en otra parte.

### Con nodo ligero
1. Descargaremos la aplicación de [Eclair](https://github.com/ACINQ/eclair/releases) en nuestro móvil y la abriremos para que se sincronice
2. Cargamos la cuenta con unos 2 € en bitcoin _(bloqueando BTC y obteniendo LBTC)_
3. Creamos un canal con la dirección de la __Colm3na__
4. Transmitimos unos pocos ___satoshis___ _(que van a ser milésimas de céntimo)_  
5. Nos pasamos la dirección por __Telegram__
6. Y listo, ya podemos hacer transacciones entre nosotros _(todo ello lightning)_
7. En el futuro cuando queramos, solo tenemos que cerrar el canal __unidireccionalmente__ para volver a cambiar los __lightning bitcoin__ por __bitcoin normales__.

### Con nodo completo
La otra forma es la versión purista, os la dejo aquí desarrollada para el que le interese despegarla después, qué viene desglosado en la siguiente [Guía de Lightning Network](https://medium.com/coinmonks/guide-setup-a-lightning-network-node-on-windows-8475206807f). Cuyos pasos principales son:
1. Descargarse el cliente de [Bitcoin Core](https://bitcoin.org/en/download)
2. Sincronizar la blockchain de Bitcoin en nodo completo _(2-3 días, unos 240 GB)_
3. Alterar la configuración del nodo:
        Bitcoin Core Configuration:

        testnet=0
        server=1
        rpcuser=your-rpc-user-here
        rpcpassword=your-rpc-password-here
        txindex=1 zmqpubrawblock=tcp://127.0.0.1:29000
        zmqpubrawtx=tcp://127.0.0.1:29000
        addresstype=p2sh-segwit
        deprecatedrpc=signrawtransaction

- También podemos crear una configuración para la Tesnet y la Mainnet en el mismo archivo de configuración

        server=1
        txindex=1
        addresstype=p2sh-segwit
        deprecatedrpc=signrawtransaction
        [main]
        rpcuser=<your-mainnet-rpc-user-here>
        rpcpassword=<your-mainnet-rpc-password-here>
        zmqpubrawblock=tcp://127.0.0.1:29000
        zmqpubrawtx=tcp://127.0.0.1:29000
        [test]
        rpcuser=<your-testnet-rpc-user-here>
        rpcpassword=<your-testnet-rpc-password-here>
        zmqpubrawblock=tcp://127.0.0.1:29001
        zmqpubrawtx=tcp://127.0.0.1:29001
4. Descargarse el cliente de Lightning Network también de [Eclair desde Github](https://github.com/ACINQ/eclair/releases)
5. Alterar la configuración del nodo:
        Eclair Configuration:

        eclair.chain=mainnet
        eclair.bitcoind.rpcport=8332
        eclair.bitcoind.rpcuser=yourusername
        eclair.bitcoind.rpcpassword=yourpassword
        eclair.node-alias=”your alias here (must be in double quotes)”
        eclair.node-color=ff9900
5. Operar desde ahí _(seguir desde el paso 2 anterior)_

#### _Por una cuestión de tiempo, realizaremos lo primero hoy y así podremos poner en marcha canales y probar cómo funciona._
