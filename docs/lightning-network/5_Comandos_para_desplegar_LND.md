## Notas:

Si sólo estamos haciendo pruebas y queremos que todos los archivos (wallets, contraseñas, blockchain...) desaparezcan una vez terminemos nuestra sesión (reiniciemos el ordanor), entonces podemos usar el parámetro `--lnddir=/tmp/lnd` con cada uno de los comandos del `lncli`.

Durante esta guía vamos a trabajar todo el tiempo en la testnet de Bitcoin & Lightning Network. Para ello, emplearemos continuamente el parámetro `--network=testnet` con el `lncli`.

_______________________________
## Instalación:

Para descargarnos el daemon y el cliente vamos a [https://github.com/lightningnetwork/lnd](https://github.com/lightningnetwork/lnd)

Aunque lo más fácil y rápido para empezar a trabajar es descargar directamente los binarios de releases:
[https://github.com/lightningnetwork/lnd/releases](https://github.com/lightningnetwork/lnd/releases)

Si, de todos modos, preferís hacerlo más manual, en este enlace encontráis toda la información para poder instalaros lo necesario desde el código fuente: [https://github.com/lightningnetwork/lnd/blob/master/docs/INSTALL.md](https://github.com/lightningnetwork/lnd/blob/master/docs/INSTALL.md)

aparte proporciona información extra sobre qué son los macaroons en la Lightning Network y otras especificaciones.
_______________________________
## Primeros pasos y conectar a la Lightning Network

Todos los pasos se realizan en la testnet.

__1. Arrancar el `lnd`__
```
lnd \
  --logdir=/tmp/lnd \
  --bitcoin.active \
  --bitcoin.testnet \
  --bitcoin.node=neutrino \
  --neutrino.addpeer=faucet.lightning.community \
  --neutrino.addpeer=lnd.bitrefill.com:18333 \
  --autopilot.maxchannels=0 \
  --autopilot.allocation=0 \
  --debuglevel=debug
```

__2. Creamos nuestra wallet (apuntad bien la contraseña que la bloquea)__
```
lncli --network=testnet create
```

__3. Mientras se sincroniza el `lnd` podemos hacer__
```
lncli --network=testnet getinfo
```
Para ver nuestra identity dentro de la LN e información como el número de peers y el bloque por el que va nuestro nodo.

De todas formas, la sincronización tarda muy poco porque estamos usando neutrino para conectarnos a la blockchain.
Esto sólo es posible en la testnet.

__4. Creamos nuestra address de testnet de Bitcoin con__
```
lncli --network=testnet newaddress np2wkh
```
Lo que antes creamos fue una wallet de Lightning, pero aún no teníamos wallet de Bitcoin.

__5. Nos conectamos a un nodo de la Lightning__
```
lncli --network=testnet connect 0270685ca81a8e4d4d01beec5781f4cc924684072ae52c507f8ebe9daf0caaab7b@159.203.125.125
```
Aquí nos conectamos al nodo de la Lightning Network Community. Vemos que la estructura para identificarlos es `pubkey@IP` y a veces también `pubkey@IP:PORT`, siendo pubkey a `identity` que nos aparece con `getinfo`.

__6. Consultamos los peers actuales con__
```
lncli --network=testnet listpeers
```

__7. Abrimos un canal con ese nodo al que nos hemos conectado__
```
lncli --network=testnet openchannel 0270685ca81a8e4d4d01beec5781f4cc924684072ae52c507f8ebe9daf0caaab7b 20000
```
Aunque es preferible ir a la página del faucet porque hay unos requisitos mínimos en este caso: https://faucet.lightning.community/

__8. Aquí vemos el channel creándose__
```
lncli --network=testnet pendingchannels
```
y, una vez creado, la lista de todos los canales activos
```
lncli --network=testnet listchannels
```

_______________________________
## Multi-Hop Payments

Para mandar pagos pasándolos a través de varios nodos, primero vemos con cuántos nodos puede comunicarse el nuestro haciendo:
```
lncli --network=testnet getnetworkinfo
```
"num_nodes" es ese número de nodos que el nuestro 'conoce'.

Con el comando
```
lncli --network=testnet queryroute --dest=<id_del_nodo_receptor> --amt=<monto_a_pagar>
```
Podemos ver si existe una ruta posible entre nosotros y el nodo al que queremos mandarle fondos.

Una vez obtenemos la payment request o solicitud de pago del nodo receptor, le mandaremos fondos con el comando
```
lncli sendpayment --pay_req=<hash_de_la_solicitud_de_pago>
```
