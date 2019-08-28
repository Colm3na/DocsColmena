## ENS meetup Ethereum Sevilla
Repositorio para el workshop del [meetup de Ethereum Sevilla](https://secure.meetup.com/es/register/?ctx=ref) sobre [ENS](https://ens.domains/), y como tokenizar nuestro dominio con [ENS Nifty](https://ensnifty.com/), asi podemos intercambiar el dominio o delegarlo a otra wallet.

ENS es un servicio de nombres de Etherum, distribuido, abierto y extensible basado en la cadena de bloques de Ethereum. ENS mapea nombres legibles por las personas a identificadores legibles por máquinas (direcciones de Ethereum, hashes de contenidos y metadatos),  por ejemplo, en lugar de `0xFls898Klkd……`, usaríamos `miDomino.eth`.

Los objetivos de ENS son parecidos a los de DNS, pero con una arquitectura diferente, debido a las capacidades y restricciones de la cadena de bloques. ENS opera en un sistema de nombres jerárquicos separados por puntos llamados dominios, con el control por parte del propietario sobre la asignación de subdominios, una vez que tiene un dominio puede configurarlo como prefiera, crear subdominios y asignarlos como mejor consideremos. 

Los dominios de nivel superior (`.eth`, `.test`) son propiedad de los contratos inteligentes llamados registradores, que especifican las reglas de asignación de sus subdominios. ENS tiene dos componentes principales: el registro y los resolutores. El registro consta de un contrato inteligente que mantiene una lista de todos los dominios y subdominios y almacena tres datos importantes sobre cada uno:
* El propietario del dominio
* El resolutor para el dominio
* El tiempo de vida para todos los registros bajo el dominio

El propietario de un dominio puede ser una cuenta externa (un usuario) o un contrato inteligente. Un registrador es un contrato inteligente que posee un dominio y emite subdominios de ese dominio a los usuarios que siguen las reglas definidas en el contrato. 

Los propietarios de dominios en el registro ENS pueden:
* Establecer el resolutor y el TTL para el dominio
* Transferir la propiedad del dominio a otra dirección 
* Cambiar la propiedad de los subdominios 

ENS se implementa en la red principal en [0x314159265dd8dbb310642f98f50c066173c1259b](https://etherscan.io/address/0x314159265dd8dbb310642f98f50c066173c1259b) donde los usuarios pueden registrar nombres bajo el eth TLD(_Top Level Domains_), que utiliza un registrador basado en subastas. 

ENS también se implementa en la testnet de Ropsten [0x112234455c3a32fd11230c42e7bccd4a84e02010](https://ropsten.etherscan.io/address/0x112234455c3a32fd11230c42e7bccd4a84e02010). Los usuarios pueden registrar nombres en dos dominios de nivel superior:
* `.eth` para la red principal. 
* `.test` que permite utilizar un nombre no utilizado para fines de prueba, expira en 28 días.

## ¿Por qué adquirir un nombre de ENS?

ENS elimina la necesidad de escribir largas direcciones hexadecimales. Con ENS puedes enviar dinero a `miDominio.eth` en vez de tener que escribir la dirección hexadecimal (0xFhgso0328G…),  interactuar con contratos inteligentes o visitar un sitio alojado en Swarm.

## ¿Cómo funciona la subasta de nombres?

Los nuevos nombres se asignan mediante un proceso de subastas basado en una _“subasta de Vickrey”_ y constan de tres etapas:

1. Primero alguien puja por un nombre que desea comprar y abre el periodo de subastas que dura tres días, en este periodo otras personas podrán realizar sus pujas. Durante este periodo los detalles de la puja se ocultan: nadie puede decir cuanto puja, ni siquiera que nombre está ofertando.

2. Una vez finalizado el periodo de tres días empieza la etapa de revelaciones. Los participantes tienen dos días para revelar sus ofertas, si no lo hacen pierden toda su oferta. Si su oferta no es la más alta, se les reembolsará su oferta menos una tarifa del 0.5% de fee.

3. Al final de la revelación el ganador es la persona que realizó la puja más alta, pero sólo tiene que pagar la cantidad de la segunda puja más alta. La puja quedará bloqueada por un contrato hasta que envíe una transacción de finalización para recibir un reembolso de los fondos adicionales y se le asignará el control del nombre ENS.

Cuando alguien gana una subasta, el nombre es suyo durante la duración del registro inicial. Después de un año puede optar por liberar el nombre y recuperar el monto total de su deposito.



# Creación de una wallet con MyCrypto
> (La parte de usar la App de MyCrypto es opcional, podemos usar cualquier gestor de carteras de Ethereum)

Para registrar nuestro dominio en [ENS](https://ens.domains/) vamos a usar [MyCrypto](https://mycrypto.com/). Para ello nos vamos a su página o usamos su aplicación. Para este workshop he decidido usar la aplicación que podemos descargar desde su [GitHub](https://github.com/MyCryptoHQ/MyCrypto/releases). La versión 1.4.0 es la última a día de hoy.

Para mi caso particular (Linux 64 bits) me descargo el archivo con extensión [.AppImage](https://github.com/MyCryptoHQ/MyCrypto/releases/download/1.4.0/linux-x86-64_1.4.0_MyCrypto.AppImage) correspondiente.
 Un _“.AppImage”_ es un formato de software portable, por lo que no se requiere instalación sino que podemos pasar directamente a su ejecución bien usando el ratón o la propia terminal. Hay que darle permisos de ejecución antes de intentar cualquiera de las dos formas.

 ```
 $ chmod a+x linux-x86-64_1.4.0_MyCrypto.AppImage  # Cambiamos permisos
 $ ./linux-x86-64_1.4.0_MyCrypto.AppImage          # Ejecutamos MyCrypto
 ```
![ens2](/images/ens/ens2.png)


Una vez abierto vemos la aplicación de MyCrypto y podemos proceder a crear una nueva wallet para usarla con ENS. Vamos a la opción del centro _“Create New Wallet”_ y seleccionamos _“Generate a Wallet”_.

![ens3](/images/ens/ens3.png)

Para este caso voy a usar la opción _“Keystore File”_.

![ens4](/images/ens/ens4.png)

Introducimos una contraseña que sea segura y hacemos clic en _“Create New Wallet”_.

![ens5](/images/ens/ens5.png)

Descargamos el archivo en _“Download Keystore File”_ y continuamos. En la siguiente pantalla nos saldrá información sobre nuestra wallet, como la clave privada, la imagen para el _“Paper Wallet”_ por si queremos descargarla y tenerlo apuntado en un papel.

![ens6](/images/ens/ens6.png)

Una vez creada la wallet y con los datos guardados vamos a proceder a usarla. Para ello nos vamos a la página principal de la aplicación de MyCrypto (“View & Send”) y seleccionamos la opción _“Keystore File”_.

![ens7](/images/ens/ens7.png)

Vamos a comprobar que la dirección de ENS que queremos esté disponible. Para ello en la aplicación de MyCrypto seleccionamos _“ENS”_, introducimos el dominio en el cual estamos interesados y hacemos clic en _“Check Availability”_.

![ens8](/images/ens/ens8.png)

Para este ejemplo comprobamos que _“colmenacowork.eth”_ esté disponible, así que hacemos clic en _“Open an auction on MyCrypto v3!”_ que nos llevará a la página de MyCrypto. Repetimos los pasos de introducir el nombre y comprobar que esté libre. Más abajo podemos ver las opciones para acceder a nuestra wallet. Como en pasos anteriores, seleccionamos la opción que deseemos y desbloqueamos nuestra cartera.

![ens9](/images/ens/ens9.png)

Nos aparece un formulario con varios datos modificables. Una vez ajustados (para este caso los dejaré tal como están) hacemos clic en _“Start the Auction”_.

![ens10](/images/ens/ens10.png)

Podemos ver que la siguiente imagen nos da información importante como el día que debemos revelar la oferta, el día que finaliza la subasta y más información. Para confirmar la operación hacemos clic en _“Yes, I am sure! Make transaction”_ **es importante copiar los datos que están dentro de _"Copy and save this"_, pues nos haran falta en un paso posterior**.

![ens11](/images/ens/ens11.png)

Comprobamos en un [explorador de bloques](https://etherscan.io/) que nuestra transacción se ha realizado correctamente sin ningún error.

![ens12](/images/ens/ens12.png)

Después, debemos esperar el tiempo mínimo para revelar nuestra oferta (3 días). Una vez que ha pasado este tiempo abrimos la pagina de MyCrypto, hacemos clic en `“TOOLS” > “ENS Domains”`, introducimos nuestro dominio, nos redirige a la página [legacy de MyCrypto](https://legacy.mycrypto.com/) y desbloqueamos nuestra wallet.
Una vez desbloqueada, debemos introducir en el espacio `“Long string of text you copied”` el texto copiado y hacemos clic en _“Reveal your Bid”_

![ens13](/images/ens/ens13.png)

Cuando hayan pasado los días necesarios podemos entrar en [MyCrypto](https://mycrypto.com/ens) introducir nuestro dominio y veremos que ya es nuestro.

![ens13](/images/ens/ens14.png)

Si hemos seguido estos pasos ya tenemos nuestro dominio `.ens`, asi que desde ahora en lugar de tener que acordarnos de esa dirección tan larga ~~de la que nadie se acuerda~~ sólo debemos recordar el nombre que hemos seleccionado. **Ese nombre será nuestra dirección de Ethereum**.

## Ahora vamos a proceder a tokenizar nuestro dominio
[ENS Nifty](https://ensnifty.com/) nos sirve para tokenizar nuestros dominios de ENS como si fueran tokens ERC-721, de esta manera podemos pasar o transferir más fácilmente nuestro dominio a otra wallet.

En esta ocasión voy a usar el complemento de [Metamask](https://metamask.io/) para [Brave](https://brave.com/) (disponible también en [Firefox](https://addons.mozilla.org/en-US/firefox/addon/ether-metamask/) y [Chrome](https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn)). Debemos importar la clave privada generada anteriormente. Una vez que estamos logueados en Metamask hacemos clic en _”Import Account”_, seleccionamos _”Private key”_, pegamos en el recuadro correspondiente la clave privada de nuestra cuenta generada al comienzo del workshop y hacemos clic en _”Import”_.

![niftyGif](/images/ens/niftyGif.gif)

Ya tenemos nuestra wallet importada en el complemento de Metamask.

![nifty4](/images/ens/nifty4.png)

Una vez que tenemos la sesión iniciada en el complemento de Metamask, abrimos la página de ensnifty y hacemos clic en _”Connect to Metamask”_.

![niftyGif2](/images/ens/niftyGif2.gif)

Como vemos nos dice que no tenemos tokenizados ningún dominio, así que hacemos clic en _”Tokenize Domain”_.

![nifty7](/images/ens/nifty7.png)

Introducimos en el recuadro nuestro dominio y hacemos clic en _”Submit”_ (**es importante poner el .eth, si no nos dará un error**). Los dos pasos que aparecen bajo el recuadro se realizaran de forma transparente para nosotros como resultado de transacciones que nos solicitará automáticamente Metamask mediante notificaciones.

![nifty9](/images/ens/nifty9.png)

Primera notificación con los valores aproximados para la transacción que queremos hacer. No voy a modificar ningún valor.

![nifty10](/images/ens/nifty10.png)

Una vez que esa transacción se haya realizado sin problemas Metamask tendrá una segunda notificación (como antes no voy a modificar los valores). Hacemos clic en ella y aceptamos.

![nifty11](/images/ens/nifty11.png)

Cuando estas transacciones haya finalizado podemos ver ambas operaciones confirmadas en la página.

![nifty12](/images/ens/nifty12.png)

Si refrescamos la página y volvemos a hacer clic en _”Connect to Metamask”_ podemos ver que ya tenemos nuestro **dominio tokenizado**. Si además abrimos nuestra wallet en un explorador de bloques nos aparecerá un **token**.

A partir de este momento si algún día tenemos que mandarlo a otra wallet o queremos regalárselo a otra persona podemos transferirlo muy fácilmente.

>Espero que esta guía les sirva de ayuda.
