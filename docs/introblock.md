# ¿Qué es la tecnología blockchain?

Antes de explicar qué es [Ethereum](https://es.wikipedia.org/wiki/Ethereum), vamos a explicar qué es la [blockchain](https://es.wikipedia.org/wiki/Cadena_de_bloques) y algunas características e información básica sobre ellas.

## ¿Qué es la blockchain?
Es un **libro de contabilidad distribuido** que **garantiza la seguridad** y la **facilidad de uso**, permitiendo a todos conectarse directamente **sin necesidad de un tercero**. _Pero aclaremos esto un poco mejor._

* **Libro de contabilidad:**
_Como_ una [base de datos](https://es.wikipedia.org/wiki/Base_de_datos), un lugar donde se escriben cosas que pueden ser, letras, números y código de programación.

* **Distribuido:**
No está en un sólo lugar, hay una copia exactamente igual en muchos ordenadores conectados a la vez (nodos), un cambio en uno de ellos afecta a todos.

* **Garantiza la seguridad:**
Usa la criptografía para mantener los intercambios digitales seguros, cualquier cambio en la blockchain debe ser aprobado antes de ser registrados, y todo el mundo puede verla

### Propiedades de la blockchain

* **Redes P2P:**
Redes P2P, o redes entre pares. Son ordenadores conectados entre sí (se suelen llamar nodos) que permiten el intercambio de información sin pasar por un servidor central, es decir, actúan como clientes y servidores.

* **Descentralización:**
Significa que la red funciona entre nodos sin nada central que controle el tráfico de datos, de manera que la plataforma está gestionada por toda la red y no por alguna autoridad central.

* **Irreversibilidad e inmutabilidad:**
Una vez que se ha grabado una información en la cadena de bloques, es imposible de eliminar, solo se podría anular si el resto de nodos estuviese de acuerdo con esta modificación.

* **Criptografía y seguridad:**
La red puede verificar que una transacción fue enviada por la persona que posee la clave privada sin que esta revele su identidad.

* **Privacidad y transparencia:**
La blockchain proporciona verificabilidad pública de su estado general sin filtrar información sobre el estado de cada participante.

---

::Según Vitalik Buterin, creador de Ethereum::

_“Las cadenas de bloques están políticamente descentralizadas (no hay nadie que las controle) y arquitectónicamente descentralizadas (no hay punto central de fallo de infraestructura) pero están lógicamente centralizadas (hay un estado comúnmente acordado y el sistema se comporta como una sola computadora)”_

---

### Tipos de blockchains

#### Según el acceso a los datos

* **Públicas:**
Aquellas en las que no hay limitaciones para participar, ni en la lectura ni en la escritura. 

* **Privadas:**
Aquellas en las que están limitadas tanto la escritura como la lectura a una lista predefinida de participantes o pares de confianza.

#### Según los permisos

* **Permissioned-blockchains (blockchain con permisos):**
En estas, las tareas de procesar transacciones son a través de una lista de participantes conocidos.

* **Permisionless-blockchains (blockchain sin permisos):**
En estas, no existen restricciones a la hora de procesar transacciones y crear bloques. Estas cadenas necesitan tokens para proveer incentivos a los usuarios y que estos mantengan el sistema. 

>**Algunos ejemplos de blockchains privadas son:** [Hyperledger](https://www.hyperledger.org/), [Ripple.](https://ripple.com/)

>**Algunos ejemplos de blockchains públicas son:**[Ethereum](https://ethereum.org/), [Bitcoin](https://bitcoin.org/es/)

### Hard-Fork

Consiste en cambiar el protocolo en el que se basa la blockchain, es un metodo de actualizacion qué no es compatible con las versiones anteriores. Un hardfork requiere que todos los nodos de la red actualicen a la nueva versión (la antigua version no es compatible), si alguno de los nodos sigue en la rama antigua estará procesando transacciones y bloques que serán inválidos y no se añadirán a la cadena de bloques. Si la versión anterior sigue teniendo nodos que la apoyen, este hardfork produciría una bifurcación completa, así, tendríamos una nueva cadena de bloques.

### Soft-Fork

Es una diferencia de carácter temporal, causada por nodos no actualizados, es un metodo de actualizacion de software que es compatible con versiones anteriores de la blockchain. En el caso de implementar el soft-fork se dará un margen temporal de algunos bloques para que todos los nodos actualicen las nuevas reglas, si pasa ese número de bloques y la mayoría de nodos de la red se han actualizado, entonces se llevará a cabo y se dará consenso para las nuevas reglas. Si por el contrario en ese margen de tiempo de bloques la mayoría no actualiza, el fork no se llevará a cabo y la cadena seguirá sin cambios.

#### Criptomonedas

* **Definición de criptomoneda:**
Una moneda digital que emplea técnicas de cifrado para reglamentar la generación de unidades de moneda y verificar la transferencia de fondos, y que opera de forma independiente de un banco central, utilizando la criptografía para asegurar que los pagos se envían y reciben de forma segura, basada únicamente en la matemáticas.

* **¿Qué es una moneda virtual?:**
El Banco central Europeo (BCE) definió en 2012 ‘moneda virtual’ como “un tipo de dinero no regulado, digital, que se emite y por lo general controlado por sus desarrolladores, y utilizado y aceptado entre los miembros de una comunidad virtual específica.

* **¿Qué es una moneda digital?**
Es una forma de moneda virtual que se crea y se almacena electrónicamente. Las criptomonedas son un tipo de moneda digital, pero no las únicas. Las criptomonedas son, por tanto, un subconjunto de las monedas digitales basadas en la criptografía. El prefijo cripto, proviene de la palabra griega _kruptos_, que significa oculto, secreto. Criptografía es el estudio de métodos de encriptación de información, principalmente utilizados para enviar un mensaje de manera segura y privada, y para la seguridad y autentificación de datos. En lugar de la moneda fiduciaria, que se imprime, una criptomoneda se produce mediante la resolución de problemas matemáticos basados en criptografía.

* **Origen de las criptomonedas:**
El origen de las criptomonedas viene del movimiento _Cypherpunk_, originado en la década de los 80, que aboga por el uso extendido de la criptografía como herramienta de cambio social y político. En 1990. David Chaun crea Digicash, un sistema centralizado de dinero electrónico que permitía transacciones más anónimas y seguras. En 1997, Adam Black propone Hashcash, un sistema basado en prueba de trabajo para limitar el spam y los ataques de denegación de servicio (DoS). En 2009, una persona o grupo de personas bajo el seudónimo Satoshi Nakamoto pública Bitcoin, la primera criptomoneda completamente descentralizada, utilizando una cadena de bloques (blockchain en inglés) con prueba de trabajo. Bitcoin utiliza el algoritmo SHA-256, una función hash criptográfica, como su esquema de prueba de trabajo (Proof-of-Work en inglés).

* **¿Cómo funcionan las criptomonedas?**
La gran mayoría de las operaciones funcionan a través de esta red descentralizada de minería de criptomonedas que asegura la validez de las operaciones a través de algoritmos criptográficos. Cada nueva operación se va sumando a esa cadena de bloques a la que se  incorporan todas las operaciones anteriores de forma sucesiva lo que garantiza que, pase lo que pase, la información no se perderá y será completa.
De esta manera, se crea un inmenso libro virtual de contabilidad, cuyas operaciones son validadas y registradas por la red de agentes independientes que se encargan de la minería de criptomonedas y que obtienen una recompensa en criptomonedas por su trabajo.

* **¿Qué es una wallet o monedero?**
Un monedero (wallet) es cualquier vía que nos permita guardar, recibir y transferir nuestros fondos, existen wallets físicas, servicios online, apps para el móvil o incluso podemos usar un papel para guardarla, generalmente en un mismo monedero no pueden haber diferentes monedas.
Esta es una de las curiosidades más grandes de las criptomonedas: no existen como tal, son sólo los registros que tienen asociado un balance.
Lo que en realidad se registra y confirma en la Blockchain son los cambios de propiedad de las cantidades correspondientes entre diferentes direcciones, las alteraciones del balance.
Cada wallet tiene una clave de seguridad propia (private key) para poder acceder a ella.

* **Tipos de wallets:**

* Wallet online en los que tú tienes las claves _(My Crypto, MyEtherWallet)_:
Hay algunos servicios que te permiten registrarte y comprar criptomonedas de forma muy sencilla, como es el caso de Coinbase. Coinbase es una de las mejores formas de empezar en este mundillo, ya que te permite comprar monedas con tu tarjeta de crédito/débito o transferencia en cuenta bancaria. El problema es que en caso de guardar tus criptomonedas en Coinbase, tú no eres el que tiene el control sobre las claves privadas de tu monedero, puedes comprar y vender criptomonedas sin problema, sacar y poner dinero cuando quieras. A nivel práctico no hay ninguna diferencia. Pero si por ejemplo la empresa cerrara sin previo aviso, tu no tendrías manera de acceder a esos fondos.
Hay otro tipo de monederos online, como por ejemplo MyEtherWallet o Mycrypto, que sí te permiten tener el control de tus claves privadas y guardar tokens distintos.

* Wallet en Software _(Windows, Mac, Linux…)_:
Tanto si utilizas Windows, Mac o Linux, otra opción muy válida a la hora de guardar tus criptomonedas es utilizar un monedero de escritorio. Es simplemente un programa que se instala en tu ordenador y que automáticamente crea tu monedero, muchas veces sin necesidad de ningún tipo de registro ni proporcionar información personal.

* Wallet en Exchanges _(casas de cambio o exchanges)_:
Hay algunos servicios que te permiten registrarte y comprar criptomonedas de forma muy sencilla, como es el caso de Coinbase. Coinbase es una de las mejores formas de empezar en este mundillo, ya que te permite comprar monedas con tu tarjeta de crédito/débito o transferencia en cuenta bancaria. El problema es que en caso de guardar tus criptomonedas en Coinbase, tú no eres el que tiene el control sobre las claves privadas de tu monedero, puedes comprar y vender criptomonedas sin problema, sacar y poner dinero cuando quieras. A nivel práctico no hay ninguna diferencia. Pero si por ejemplo la empresa cerrara sin previo aviso, tu no tendrías manera de acceder a esos fondos.

* Wallet en extensión de navegador _(Chrome, Firefox…)_:
Otra manera curiosa mediante la cual puedes tener un wallet en el que guardar tus Ether es a través de una extensión del navegador llamada Metamask.
Es posible utilizar Metamask junto con MyEtherWallet para tener más seguridad (ya que no hace falta que descargues tu clave privada) e incluso es esencial tenerlo instalado para poder acceder a algunas aplicaciones descentralizadas (ÐApps) como es el caso del famoso juego CryptoKitties.

* Wallet físicos _(Hardware)_:
Un monedero o wallet físico es un pequeño dispositivo parecido a una llave USB, pero diseñado especialmente para guardar criptomonedas.
Los precios varían, pero los más recomendables (por este orden) son Trezor , Ledger Nano S, Trezor Model T y KeepKey.

* Wallet en apps para smartphone _(Android, iOS)_:
Este tipo no se suele recomendar por la poca seguridad que proporcionan, pero ya hay algunas que dejan gestionar nosotros las claves privadas.

* Wallet en papel _(paper wallet)_
Wallet en papel:
Es un registro de las claves privadas y públicas que necesitas para acceder a tu billetero y realizar transacciones, Proporcionan una ventaja extraordinaria sobre otras técnicas de almacenamiento de criptomonedas convencionales. Los monederos en papel no están en Internet y por lo tanto ningún hacker puede tener acceso a tus criptomonedas.
Por otro lado, sin embargo, con una wallet de papel la velocidad para realizar transferencias e intercambios, así como la disponibilidad se reducen enormemente. Esto se debe a que las monedas tienen que ser devueltas a una billetera online como MyEtherWallet antes de poder ser utilizadas.

* **¿Qué son los tokens?:**

Unidad digital que representa la propiedad o el derecho a usar una red basada en blockchain.
Estos derechos de propiedad pueden aplicarse tanto a entidades del mundo digital como a entidades del mundo real.
Los tokens, al igual que las criptomonedas, están protegidos criptográficamente contra la falsificación y a menudo no son emitidos ni controlados por ninguna autoridad centralizada.
[Aquí](https://etherscan.io/tokens) podemos encontrar una lista de ellos.

* **¿Qué son los tokens ERC-20?**

Es una lista continua de estándares sugeridos en Ethereum que los desarrolladores de aplicaciones descentralizadas deben tener en cuenta para hacer que los tokens compatibles con ERC-20 sean intercambiables con Ether u otros tokens ERC-20.
En algunas situaciones, los tokens ERC-20 pueden presentar dificultades de cara a los usuarios. Por ejemplo, si alguien utiliza un token ERC-20 para enviar 3 ETH a un contrato que no es compatible con ERC-20, la transacción no será rechazada porque el contrato no reconocerá la transacción entrante. El ETH podría quedarse atascado en el limbo y acabar perdiéndose.
Un nuevo estándar de token (el ERC-223 propuesto) resuelve este problema rechazando una transacción si no es compatible con ERC.
Por otra parte, otro estándar propuesto llamado ERC-721, permite crear tokens que no sean fungibles. Ésto quiere decir que cada token será totalmente único y no serán intercambiables entre sí.
Un token ERC-721 tendrá valor debido a su singularidad y cualidades extrañas y ya hemos visto algunos proyectos que los utilizan, como el famoso CryptoKitties, en el que se coleccionan cripto-gatos, cada uno con sus propias cualidades únicas y distintas a todos los demás.

>Un ejemplo claro serían los palets, la medida de los palets suele ser igual para todos, pero lo que alberga puede er distinto, el ERC-20 sería como el palet, y el nombre del token seria como el contenido del palet.

* **¿Qué son las ICOs?**

Una oferta inicial de monedas (ICO en inglés) es un tipo de financiamiento usando criptomonedas. Mayoritariamente el proceso es llevado a cabo mediante un crowdfunding, pero las ICOs privadas se están volviendo muy comunes. En una ICO, las criptomonedas son vendidas en forma de "tokens" a especuladores o inversores a cambio de dinero tradicional u otras criptomonedas como Bitcoin o Ethereum. Los tokens son vendidos como "futuras" unidades de la moneda cuando la ICO llegue a su objetivo y el proyecto se lance. En algunos casos como Ethereum los tokens son requeridos por el sistema.
La primera ICO fue realizada por Mastercoin en julio de 2013. Ethereum hizo una oferta en 2014, llegando a conseguir 3,700 BTC en las primeras 12 horas, aproximadamente 2.3 millones en aquel momento.  En mayo de 2017, la ICO para un nuevo navegador web llamado Brave generó cerca de 35 millones de dólares en 30 segundos.

### Plataformas descentralizadas

Las redes p2p son una serie de ordenadores conectados entre sí (nodos), los cuales intercambian información directamente sin necesidad de un ordenador central. Algunos ejemplos de redes p2p son Utorrent, Ares, BitTorrent… qué son usadas para compartir archivos.

>Como anécdota, en 1999 Shawn Fanning creó la aplicación para compartir música y archivos Napster, está fue el comienzo de las redes peer-to-peer.

**Características**
* Escalabilidad.
* Robustez.
* Descentralización.
* Distribución de costes entre los usuarios.
* Anonimato.
* Seguridad.

>[Aquí](https://es.wikipedia.org/wiki/Anexo:Comparativa_de_clientes_peer-to-peer) una comparativa de clientes peer-to-peer.

### Minería

La palabra minería se origina en el contexto de la analogía del oro para las monedas criptográficas. El oro o los metales preciosos son escasos, al igual que los tokens digitales, y la única manera de aumentar el volumen total es a través de la minería. Esto es apropiado en la medida en que también en Ethereum, el único modo de emisión posterior al lanzamiento es a través de la minería. Sin embargo, a diferencia de estos ejemplos, la minería es también la forma de asegurar la red creando, verificando, publicando y propagando bloques en la cadena de bloques.
La minería, es el proceso de agregar repetidamente transacciones, construir un bloque y probar nonces diferentes hasta que se encuentre un nonce que satisfaga la condición de la prueba de trabajo. Si un minero tiene suerte y produce un bloque válido, se le premia con un cierto número de monedas como recompensa, así como todas las tarifas de transacción en el bloque, y todos los mineros comienzan a tratar de crear un nuevo bloque que contenga el hash del nuevo bloque generado como el anterior.
En la blockchain el proceso de la “minería” es la validación de las transacciones, por ello los mineros tienen una recompensa en la moneda de la blockchain (Bitcoin=BTC, Ethereum=ETH, Monero=XMR, Zcash=ZEC…), los mineros tienen así un incentivo  para ayudar a la red.

>La minería cumple la función de verificar transacciones de criptomonedas en una blockchain.

Los mineros desempeñan el papel de los cajeros bancarios, comprueban que las firmas y números de cuentas están correctos, asegurando la identidad y las pruebas de la existencia de los fondos para realizar la transacción. 
Estas firmas digitales operan mediante el uso de las funciones “hash“: ecuaciones matemáticas que toman cualquier entrada dada y crean una salida única para esa entrada en particular.

#### Mecanismos de elección de bloques

Proof of Work:
Una propiedad importante de un bloque en Ethereum, Bitcoin y muchas otras criptomonedas debe ser menor que algún valor objetivo. La razón por la cual esto es necesario, es que, en un sistema descentralizado, cualquiera puede producir bloques, por tanto, para evitar que la red se llene de bloques, y para proporcionar una forma de medir cuánto consenso hay detrás de una versión particular de la cadena de bloques, de alguna manera debe ser difícil producir un bloque. Debido a que los hashes son pseudoaleatorios, encontrar un bloque cuyo hash es menor que `0000000100000000000000000000000000000000000000000000000000000000` requiere un promedio de 4.3 mil millones de intentos. En todos estos sistemas, el valor objetivo se autoajusta de modo que, en promedio, un nodo en la red, encuentra un bloque cada N minutos (por ejemplo, N=10 en Bitcoin y 1 para Ethereum).

>Mining ether = Securing the Network = Verifying Computation

El algoritmo de prueba de trabajo (PoW) utilizado en Ethereum se llama [Ethash](https://github.com/ethereum/wiki/wiki/Ethash) (una versión modificada del algoritmo [_Dagger-Hashimoto_](https://github.com/ethereum/wiki/wiki/Dagger-Hashimoto)) y consiste en encontrar una entrada de nonce al algoritmo para que el resultado esté por debajo de un cierto umbral de dificultad. El punto en los algoritmos PoW es que no hay mejor estrategia para encontrar tal cosa que enumerar las posibilidades, mientras que la verificación de una solución es trivial y barata. Dado que las salidas tienen una distribución uniforme (ya que son el resultado de la aplicación de una función de hash), podemos garantizar que, en promedio, el tiempo que se necesita para encontrar tal valor depende del umbral de dificultad. Esto permite controlar el tiempo de búsqueda de un nuevo bloque simplemente manipulando la dificultad.

Ethash PoW (el que usa _Ethereum_) es resistente a ASIC. Se logra con un algoritmo de prueba de trabajo que requiere la selección de subconjuntos de un recurso fijo que depende del encabezado del bloque y del nonce. Este recurso (unos pocos datos de tamaño de gigabytes) se llama [DAG](https://github.com/ethereum/wiki/wiki/Ethash-DAG). La DAG es totalmente diferente cada 30000 bloques, una ventana de 125 horas llamada época (aproximadamente 5.2 días) y toma un tiempo para generarse. Dado que el DAG sólo depende de la altura del bloque, puede ser pre-generado, pero si no es así, el cliente necesita esperar hasta el final de este proceso para producir un bloque. Si los clientes no generan y almacenan en caché los DAG con antelación, la red puede sufrir un retraso masivo de bloques en cada transición de época. Tenga en cuenta que no es necesario generar el DAG para verificar el PoW, lo que esencialmente permite la verificación con una CPU baja y una memoria pequeña.

Cada vez que un minero resuelve esta ‘prueba de trabajo’, transmitirá el bloque a toda la red. El resto de mineros deberán comprobar que, tanto las operaciones incluidas en el bloque como la firma digital son válidas. Si la gran mayoría lo aprueba, el bloque se añadirá a la cadena de bloques de forma inmutable.

Para evitar que los bloques se completen demasiado rápido o demasiado lento, el protocolo se reajusta después de añadir cada bloque para hacer más fácil o más difícil de adivinar el valor Nonce.

**Tipos de hardware para minería**

- Los chips **ASICs** _(Application-Specific Integrated Circuit)_ o también llamados Circuitos Integrados de Aplicación Específica, son chips cuya función es realizar una tarea concreta y particular. Estas máquinas son las más extendidas en la minería de Bitcoin.

- Las **CPUs** _(Central Processor Unit)_ o Unidad Central de procesamiento es lo que conocemos como el procesador de un ordenador. De las tres opciones, esta es la menos potente y prácticamente no se utiliza para la minería

- Las **GPUs** _(Graphic Processor Unit)_ o Unidad Gráfica de procesamiento es lo que conocemos como la tarjeta gráfica de un ordenador. Éstas tienen un ‘hash rate’ o potencia minera más alta que las CPUs, lo que significa que pueden resolver los problemas matemáticos más rápido.

**Un resumen de los mineros sería:**
1. Reciben las solicitudes de transacción
2. Verifican que éstas se pueden llevar a cabo
3. Almacenan las transacciones válidas en un bloque
4. Compiten realizando cálculos para encontrar el valor Nonce
5. El que lo consigue, propaga su bloque al resto de los mineros
6. Si la mayoría lo da por válido, éste se añade a la cadena de bloques
7. El minero ganador recibe la recompensa del bloque

## Proof of Stake

**Prueba de participación** _(PoS)_ es una categoría de algoritmos de consenso para blockchains públicas que dependen del interés económico de un validador en la red. En las blockchains públicas basadas en prueba de trabajo _(PoW)_  _(por ejemplo, Bitcoin y la implementación actual de Ethereum)_, el algoritmo recompensa a los participantes que resuelven encriptaciones criptográficas para validar transacciones y crear nuevos bloques _(es decir, minería)_. En las blockchains públicas basadas en PoS _(por ejemplo, la próxima implementación de Casper de Ethereum, Polkadot, Cosmos)_, un grupo de validadores se turnan para proponer y votar el siguiente bloque, y el peso del voto de cada validador _(es decir, la validación)_ depende del tamaño de su depósito. Las ventajas significativas de PoS incluyen seguridad, menor riesgo de centralización y eficiencia energética.

La cadena de bloques realiza un seguimiento de un conjunto de validadores, y cualquiera que tenga la criptomoneda base de la cadena de bloques (en el caso de Ethereum, el Ether "Ξ") puede convertirse en un validador al enviar un tipo especial de transacción que bloquea su Ether en un depósito. El proceso de crear y aceptar nuevos bloques se realiza a través de un algoritmo de consenso en el que pueden participar todos los validadores actuales.

Hay muchos tipos de algoritmos de consenso y muchas formas de asignar recompensas a los validadores que participan en el algoritmo de consenso, por lo que hay muchos _"sabores"_ de prueba de participación. Desde una perspectiva algorítmica, hay dos tipos principales: **prueba de participación basada en la blockchain** y **prueba de participación al estilo [BFT.](https://en.wikipedia.org/wiki/Byzantine_fault_tolerance)**

En la **prueba de participación basada en blockchain**, el algoritmo selecciona pseudoaleatoriamente un validador durante cada intervalo de tiempo (por ejemplo, cada período de 10 segundos puede ser un intervalo de tiempo) y asigna ese validador al derecho de crear un solo bloque, y este bloque debe apuntar a un bloque anterior _(normalmente el bloque al final de la cadena que anteriormente era más larga)_, y con el tiempo la mayoría de los bloques convergen en una sola cadena en constante crecimiento.

En la **prueba de participación al estilo BFT**, a los validadores se les asigna _aleatoriamente_ el derecho de proponer bloques, pero acordar qué bloque es canónico se realiza a través de un proceso de múltiples rondas donde cada validador envía un "voto" para un bloque específico durante cada ronda, y al final del proceso, todos los validadores _(honestos y en línea)_ acuerdan permanentemente si un bloque determinado es parte de la cadena o no. Tenga en cuenta que los bloques aún pueden estar encadenados juntos; la diferencia clave es que el consenso en un bloque puede venir dentro de un bloque, y no depende de la longitud o el tamaño de la cadena después de él.

**Principales beneficios del PoS frente al PoW:**

· No es necesario consumir grandes cantidades de electricidad para asegurar una cadena de bloques (por ejemplo, se estima que tanto Bitcoin como Ethereum queman más de $ 1 millón en costos de electricidad y hardware por día como parte de su mecanismo de consenso).

· Debido a la falta de alto consumo de electricidad, no hay la necesidad de emitir tantas monedas nuevas para motivar a los participantes a seguir participando en la red. En teoría, incluso es posible tener una emisión neta negativa, en la que una parte de las tarifas de transacción se "quema" y, por lo tanto, el suministro disminuye con el tiempo.

· La prueba de participación abre la puerta a una gama más amplia de técnicas que utilizan el diseño de mecanismos teóricos de juegos para desalentar mejor a los grupos centralizados de formarse y, si se forman, actuar de maneras que son perjudiciales para la red (por ejemplo, interesados en la minería en prueba de trabajo).

· Reducción de los riesgos de centralización, ya que las economías de escala son mucho menos problemáticas. $ 10 millones de monedas le darán ganancias exactamente 10 veces más altas que $ 1 millón de monedas, sin ganancias adicionales desproporcionadas, porque en el nivel más alto puede permitirse un mejor equipo de producción en masa.

· La capacidad de utilizar sanciones económicas para hacer que varias formas de ataques del 51% sean mucho más costosas que la prueba de trabajo, parafraseando a Vlad Zamfir, "es como si tu granja de ASIC se hubiera quemado si participas en un ataque del 51%"
