# DAppNode-WIFI

- [Repositorio oficial](https://github.com/dappnode/DAppNode)

En este repositorio están los pasos necesarios para usar el wifi del [DAppNode](https://github.com/dappnode/DAppNode) de la [Colm3na](https://www.coworkingcolmena.com) como nodo.

El primer paso es conectarse al wifi del DAppNode, su `SSID` es `DAppNodeColm3na` para saber la contraseña pásate por la Colmena :honeybee: .

Para utilizarlo es necesario tener [Metamask](https://metamask.io) instalado.

<sumary>
<h1 align="center"> Red principal de Ethereum: </h1>

</sumary>
<details>

**1.** Desbloqueamos Metamask:

<p align="center"><img src="/images/dappnodewifi/image1.png"></p>

**2.** Hacemos clic en `Red principal de Ethereum` para modificar el nodo:

<p align="center"><img src="/images/dappnodewifi/image2.png"></p>

**3.** En el desplegable seleccionamos `RPC personalizado`:

<p align="center"><img src="/images/dappnodewifi/image3.png"></p>

**4.** Rellenamos los datos necesarios para conectarnos.
 En `Network Name` ponemos el nombre que queramos (es simplemente un identificador para nosotros), y en `New RPC URL` añadimos el nodo `http://my.ethchain.dnp.dappnode.eth:8545`, los demás valores son opcionales, y hacemos clic en `Guardar`. 

<p align="center"> 
<img src="/images/dappnodewifi/image4.png">
</p>

**5.** Como podemos comprobar vemos que estamos conectados a nuestro propio nodo:

<p align="center"> 
<img src="/images/dappnodewifi/image5.png">
</p>
</details>

<sumary>
<h1 align="center"> Testnet Rinkeby: </h1>

</sumary>
<details>

**1.** Desbloqueamos Metamask:

<p align="center"> 
<img src="/images/dappnodewifi/image1.png">
</p>

**2.** Hacemos clic en `Red principal de Ethereum` para modificar el nodo:

<p align="center"> 
<img src="/images/dappnodewifi/image2.png">
</p>

**3.** En el desplegable seleccionamos `RPC personalizado`:

<p align="center"> 
<img src="/images/dappnodewifi/image3.png">
</p>

**4.** Rellenamos los datos necesarios para conectarnos.
 En `Network Name` ponemos el nombre que queramos (es simplemente un identificador para nosotros), y en `New RPC URL` añadimos el nodo `http://my.rinkeby.dnp.dappnode.eth:8545`, los demás valores son opcionales, y hacemos clic en `Guardar`. 

<p align="center"> 
<img src="/images/dappnodewifi/image6.png">
</p>

**5.** Como podemos comprobar vemos que estamos conectados a nuestro propio nodo:

<p align="center"> 
<img src="/images/dappnodewifi/image7.png">
</p>
</details>


<sumary>
<h1 align="center"> Nodo de Cosmos y wallet Lunie: </h1>

</sumary>
<details>

> Como en pasos anteriores necesitamos estar conectados al wifi del DAppNode.

En este caso simplemente cuando estemos conectados al wifi de la Colmena podemos acceder a la siguiente URL para usar los RPC endpoints y la wallet de Lunie.

[https://cosmos.public.dappnode/lunie](https://cosmos.public.dappnode/lunie)

>La primera vez que nos conectamos, nos avisa del certificado, al ser autofirmado necesitamos aceptarlo.

>Hacemos clic en `Configuración avanzada`

<p align="center"><img src="/images/dappnodewifi/image8.png"></p>

Y después en  `Acceder a cosmos.public.dappnode (sitio no seguro)`

<p align="center"><img src="/images/dappnodewifi/image9.png"></p>

Comprobamos que estamos conectados a nuestro nodo pasando el ratón por encima de `cosmoshub-2` (situado abajo a la izquierda), podemos firmar nuestras transacciones si tenemos una Ledger conectándola a nuestro portátil. 

<p align="center"><img src="/images/dappnodewifi/image10.png"></p>

</details>

<br>

**Gracias al equipo de [DAppNode](https://dappnode.io) por su proyecto!!**

**Recordad que estos pasos sólo se pueden seguir si estamos conectados al wifi del DAppNode de la Colmena, desde otro punto no conectaría con el.**
