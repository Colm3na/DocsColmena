# Aquí puedes encontrar la traducción del glosario de Polkadot

## Alexander

La cuarta testnet (ahora sin funcionar), una prueba de concepto (PoC-4) para Polkadot.

## Attestation

En el sistema de validación de Polkadot, un atestado es un tipo de mensaje que los validadores emiten e indican si creen que un bloque de Parachain candidato es válido o no.

## Authority

La autoridad es un término genérico que designa la función en una cadena de bloques que puede participar en los mecanismos de consenso. En GRANDPA, las autoridades votan sobre las cadenas que consideran definitivas. En BABE, las autoridades son productores de bloques. Los conjuntos de autoridades pueden ser elegidos como mecanismos similares al algoritmo NPoS de Polkadot.

## BABE

**B**lind **A**ssignment of **B**lock **E**xtension es el mecanismo para la producción de bloques de Polkadot.

## Bloque

Un conjunto de datos, como las transacciones, que juntos indican una transición de estado de la cadena de bloques.

## Block explorer

Una aplicación que permite al usuario visualizar los diferentes bloques de una blockchain.

>_Un buen ejemplo es el explorador de bloques desarrollado desde [Colmenalabs_svq](https://www.colmenalabs.org/) para Polkadot llamado [Polkastats](https://polkastats.io/)_

## BLS

Las firmas de Boneh-Lynn-Shacham (BLS) tienen una firma lenta, una verificación muy lenta, requieren curvas simples de emparejamiento lentas y mucho menos seguras, y tienden hacia una maleabilidad peligrosa. Sin embargo, BLS permite un conjunto diverso de opciones de agregación de firmas mucho más allá de cualquier otro esquema de firma conocido, lo que hace de BLS un esquema preferido para votar en algoritmos de consenso y para firmas de umbral.

## Bonding

Un proceso por el cual los tokens pueden ser "congelados" a cambio de algún otro beneficio. Por ejemplo, el "staking" es una forma de vinculación por la que se reciben recompensas a cambio de asegurar la red. También puede vincular tokens a cambio de un espacio de parachain.

## Bridge

Una Parachain que actúa como intermediaria entre la relay chain de Polkadot y una cadena externa, de tal modo que a la relay chain le parece que la cadena externa es una parachain (es decir, cumple con los requisitos de las parachains de Polkadot). Los puentes permiten la interacción entre otras cadenas de bloques, como Ethereum y Bitcoin, que no son en principio compatibles con Polkadot.

## Byzantine Fault Tolerance

La propiedad de un sistema que es tolerante a los fallos Bizantinos; es decir, un sistema en el que no sólo pueden fallar subsistemas individuales, sino que puede no estar claro si un subsistema en particular ha fallado o no. Es decir, los diferentes actores del sistema pueden no estar de acuerdo en si el sistema ha fallado o no. Garantizar la tolerancia a los fallos Bizantinos es una parte importante del desarrollo de cualquier sistema distribuido.

## Collator

Un nodo que mantiene una parachain recolectando transacciones de parachain y produciendo pruebas de transición de estado para los validadores.

## Consensus

El proceso de un grupo de entidades para acordar un determinado valor de datos (como el orden y la composición de los bloques en una cadena de bloques). Existen diversos algoritmos utilizados para determinar el consenso. El algoritmo de consenso utilizado por Polkadot es GRANDPA.

## Dapps

Término genérico para una aplicación descentralizada, es decir, que funciona como parte de una red distribuida en lugar de funcionar en un sistema o conjunto de sistemas específicos.

## DOTs

El token nativo de Polkadot. Los DOTs tienen tres propósitos: la gobernanza de la red (permitiéndoles votar sobre las mejoras de la red y otros eventos excepcionales), el funcionamiento general (recompensando a los buenos actores y castigando a los malos), y la vinculación (añadiendo nuevas parachains "congelando" los DOTs mientras están conectados a la relay chain).

## Duty Roster

Una tabla de consulta que especifica el trabajo que debe hacer un validador determinado (es decir, dar fe de la validez de una parachain específica). La tabla de tareas cambia periódicamente el conjunto de validadores en diferentes subconjuntos por parachain.

## Epoch

Una época es una duración de tiempo en el protocolo BABE que se rompe en franjas de tiempo más pequeñas. Cada espacio tiene al menos un líder de espacios que tiene el derecho de proponer un bloque. En Kusama, es la misma duración que una sesión.

## Era

Un número (entero) de sesiones, que es el período en que se recalcula el conjunto de validadores (el conjunto de nominadores activos de cada validador) y en el que se pagan las recompensas.

## Equivocation

Proporcionar información conflictiva a la red. La equivocación de BABE implica crear múltiples bloques en la misma posición. La equivocación GRANDPA consistiría en firmar múltiples cadenas conflictivas.

## Extrinsic

Los cambios de estado que vienen del mundo exterior, es decir, no son parte del sistema en sí. Extrinsics puede adoptar dos formas, ["heredadas"](#Inherent) y ["transacciones"](#Transaction).

## Finality

La propiedad de un bloque que no puede ser revertido. Generalmente, los bloques creados no son definitivos hasta algún momento en el futuro - tal vez nunca, en el caso de la "finalidad probabilística". La relay chain de Polkadot utiliza un elemento de finalidad determinista conocido como GRANDPA.

## Finality Gadget

Un mecanismo que determina la finalidad.

## Fisherman
Nodos que monitorean la red para buscar validadores o collators que se comporten mal. Los fisherman deben comprometerse con una pequeña cantidad de DOTs pero pueden ser recompensados en gran medida si encuentran un mal comportamiento.

## Frame

La colección de paletas proporcionadas por Substrate (Substrate Runtime Modules).

## Genesis
El origen de una cadena de bloques, también conocida como bloque 0. Además, puede utilizarse para referirse al estado inicial de la cadena de bloques en su origen.
Ejemplo: "En el genesis Alice, Bob, y Charlie tenían 30 tokens cada uno."

## Governance

El proceso de determinar qué cambios en la red son permitidos, como las modificaciones del código o el movimiento de fondos. El sistema de gobierno en Polkadot está encadenado y gira en torno a la votación de los involucrados.

## Governance Council

Una entidad en cadena que consiste en varias cuentas en cadena (comenzando en 6, pasando eventualmente al valor final de 24). El Consejo puede actuar como representante de los involucrados "pasivos" (sin derecho a voto). Los miembros del Consejo tienen dos tareas principales: proponer referéndums para que el grupo de interesados en general vote y cancelar los referéndums malintencionados.

## GRANDPA Finality Gadget

GHOST-based Recursive ANcestor Deriving Prefix Agreement. Es el instrumento para la finalización de Polkadot, que permite una finalización asincrónica, responsable y segura para la cadena de bloques. Para una visión general del GRANDPA, vea [este post](https://medium.com/polkadot-network/polkadot-proof-of-concept-3-a-better-consensus-algorithm-e81c380a2372) en Medium.

## Hard Fork

Una desviación permanente de una cadena de bloques que puede ocurrir rápidamente debido a un cambio de alta prioridad en una regla de consenso. Los clientes que siguen un hard fork siempre necesitan actualizar sus clientes para continuar siguiendo la cadena actualizada. Los hard fork se consideran divergencias permanentes de una cadena para la cual los clientes no actualizados siguen reglas de consenso incompatibles con las que siguen los clientes actualizados.

## Hard Spoon

Definido por Jae Kwon de Cosmos como "una nueva cadena que tiene en cuenta el estado de una cadena existente; no para competir, sino para proporcionar un acceso más amplio". Una cadena de bloque no conflictiva que hereda el estado de la cadena de bloque subyacente y crea una nueva rama de la misma cadena de bloques.

## Inherent

Extrinsics que son " intrínsecamente verdaderos". Los Inherents no se hablan en la red y son puestos en bloques por el autor del bloque. No son probadamente verdaderos de la manera que el envío de fondos, por lo tanto no llevan una firma. El runtime de una cadena de bloques debe tener reglas para validar los inherentes. Por ejemplo, las marcas de tiempo son hereditarias. Se validan estando dentro de algún margen que cada validador considere razonable.

## KSM

La abreviatura de los tokens de la red de Kusama.

## Kusama

La "red canaria" de Polkadot. Consiste en una versión anticipada y no auditada del software Polkadot. No es una red de prueba - después de la transición a NPoS, la red queda totalmente en manos de la comunidad (es decir, de los poseedores de tokens).

## LIBP2P

Una biblioteca de código abierto para comunicaciones cifradas entre pares y otras funciones de red. Más información en: [https://libp2p.io/](https://libp2p.io/)

## Liveness

La propiedad de un sistema distribuido que eventualmente llegará a algún tipo de consenso. Un sistema atascado en un bucle infinito no se consideraría vivo, incluso si se están realizando cálculos; un sistema que finalmente proporciona un resultado, aunque sea incorrecto o lleve mucho tiempo, se considera que tiene vida.

## Message

En el protocolo XCMP de Polkadot, un mensaje es un dato arbitrario que se envía de una parachain (la cadena de salida) a otra (la cadena de entrada) a través de un canal y se asegura la entrega por el conjunto de validadores.

## Message Queue

En el protocolo XCMP de Polkadot, message queue es la lista de mensajes en espera de ser procesados por una parachain receptora particular a través de un canal.

## Node explorer

Una herramienta que le da información sobre un nodo, como los últimos bloques cerrados, finalizados y el estado actual de la cadena, tal como lo conoce ese nodo.

## Nominated Proof of Stake (NPoS)

Un sistema de prueba de participación donde los nominadores respaldan a los validadores con su propia aportación como muestra de fe en el buen comportamiento del validador. La prueba de participación nominada difiere del concepto más genérico de prueba de participación delegada en que los nominadores están sujetos a la pérdida de la participación si nominan a un mal validador; los delegados no están sujetos a la pérdida de la participación basada en el comportamiento del validador. Obsérvese que algunas otras tecnologías de cadenas de bloques pueden utilizar el término prueba de participación delegada, incluso si los delegados pueden ser sometidos a una penalización. Polkadot utiliza el método Phragmen para asignar la participación a los nominados.

## Nominator

Cuentas que seleccionan un conjunto de validadores para nominar, uniendo sus tokens. Los nominadores reciben algunas de las recompensas de los validadores, pero también son responsables de la penalización si sus validadores nominados se comportan mal.

## On-chain governance

Un sistema de gobierno de una cadena de bloques que está controlado por mecanismos en la cadena de bloques. El gobierno de la cadena permite que las decisiones se tomen de manera transparente. Nótese que hay una variedad de algoritmos diferentes para tomar estas decisiones, como la votación por mayoría simple, el sesgo de quórum adaptable o la votación cuadrática basada en la identidad.

## Pallet

Un módulo Substrate de tiempo de ejecución.

## Parachain

Una cadena de bloques que reúne varias características que le permiten trabajar dentro de los límites de Polkadot. También conocida como "cadena paralela."

## Parachain Registry

Una base de datos relativamente simple que contiene información estática y dinámica de cada cadena.

## Parity Technologies

Una compañía, fundada por el Dr. Gavin Wood, que está desarrollando Substrate y Polkadot. También ha publicado varios otros proyectos, entre ellos Parity Ethereum y Parity Secret Store.

## Polkadot

Una red heterogenea y multicadena que permite a varias blockchains de diferentes características realizar comunicaciones arbitrarias de cadena cruzada bajo una seguridad compartida.

## Polkadot Host

El entorno en el que se puede ejecutar un módulo de tiempo de ejecución. Las Parachains deben ser compatibles con Polkadot - cadenas externas que no tienen que usar un puente. Anteriormente conocido como Polkadot Runtime Environment o PRE.

## Polkadot Runtime Environment

El nombre anterior para Polkadot.

## Proof of Stake (PoS)

Método de selección de la participación en un sistema de consenso, en el que los participantes se eligen en función de la cantidad de tokens que tienen en juego (con riesgo de penalización por mal comportamiento). Normalmente, los sistemas de prueba de participación limitan el número de participantes.

## Proof of Validity

Una prueba producida por los collators de parachain. Basándose en esta prueba y en el registro de parachain, un validador puede verificar que una parachain ha ejecutado correctamente su función de transición de estado. Las pruebas de validez van en los bloques de la relay chain.

## Proof of Work (PoW)

Un método de selección de participantes en un sistema de consenso, típicamente la regla de la cadena más larga, en el que los participantes tratan de resolver un rompecabezas como encontrar una imagen previa parcial de un hash. Normalmente, un sistema de prueba de trabajo puede tener cualquier número de participantes.

## Proposal

Una posible llamada de función para ser votada en un referéndum. Las propuestas modifican el comportamiento de la red Polkadot, desde el ajuste de parámetros menores hasta la sustitución del código de tiempo de ejecución.

## Protocol

Sistema de reglas que permite a dos o más entidades de un sistema de comunicaciones transmitir información. El protocolo define las reglas, la sintaxis, la semántica y la sincronización de la comunicación y los posibles métodos de recuperación.

## Random Seed

Una semilla al azar es un número pseudo-aleatorio disponible en la cadena. Se utiliza en varios lugares del protocolo Polkadot, sobre todo en BABE el mecanismo de producción de bloques.

## Referendum

Una votación sobre si una propuesta debe ser aceptada o no por la red. Los referéndums pueden ser iniciados por el Consejo de Gobierno, por un miembro del público o como resultado de una propuesta anterior. Los interesados votan en los referéndums, ponderados tanto por el tamaño de su participación (es decir, el número de DOTs que tienen) como por la cantidad de tiempo que están dispuestos a bloquear sus tokens.

## Relay chain

La cadena que coordina el consenso y la comunicación entre las parachains (y las cadenas externas, a través de puentes).

## Runtime

La función de transición de estado de una cadena de bloques. Define un algoritmo válido para determinar el estado del siguiente bloque dado el estado anterior.

## Runtime Module

Un módulo que implementa funciones y características de transición específicas que uno podría querer tener en su tiempo de ejecución. Cada módulo debe tener una lógica específica de dominio. Por ejemplo, un módulo de saldos tiene una lógica para tratar con cuentas y saldos. En Substrate, los módulos se denominan "pallets".

## Safety

La propiedad de un sistema distribuido que indica que no se revertirá una transición de estado particular. El GRANDPA proporciona seguridad determinística. Es decir, para un cambio de estado marcado como "seguro" o "final", se requeriría un hard fork para revertir ese cambio.

## Sealing

El proceso de añadir un bloque a la relay chain. Tenga en cuenta que la finalización es un proceso separado - los bloques se finalizan algún tiempo después de ser cerrados.

## Session

Una sesión es un plazo de aplicación de Substrate durante un período de tiempo que tiene un conjunto constante de validadores. Los validadores sólo pueden entrar o salir del conjunto de validadores en un cambio de sesión.

## Session Certificate

Un mensaje que contiene una firma en la concatenación de todas las claves de la Sesión. Firmado por el Controller.

## Session Key

Teclas de acceso directo que se utilizan para realizar operaciones de red por parte de los validadores, por ejemplo, firmar mensajes de confirmación GRANDPA.

## Shared Security

El modelo de seguridad que Polkadot utiliza por el cual todas las cadenas están igualmente aseguradas. Esto se logra colocando pruebas de la validez de los bloques de parachains en la relay chain de tal manera que, para revertir la finalización de una sola parachain, un atacante tendría que atacar todo el sistema Polkadot.

## Slashing

La eliminación de un porcentaje de los DOTs de una cuenta como penalización para un validador que actúa de forma maliciosa o incompetente (por ejemplo, equivocarse o permanecer fuera de línea durante un período de tiempo prolongado).

## Soft Fork

Un cambio compatible con el código de cliente que hace que los clientes mejorados empiecen a trabajar en una nueva cadena. Requiere un "voto por porcentaje" de la mayoría de los mineros para que se lleve a cabo con éxito. Las bifurcaciones simples se consideran divergencias temporales en una cadena, ya que los clientes no actualizados no siguen las nuevas reglas de consenso, pero los clientes actualizados siguen siendo compatibles con las antiguas reglas de consenso.

## Staking

El acto de vincular los tokens (para Polkadot, DOT) que se ponen como "garantía" para tener la oportunidad de producir un bloque válido (y así obtener una recompensa por el bloque). Los validadores y nominadores ponen en juego sus DOTs para asegurar la red.

## State transition function

Una función que describe cómo se puede transformar el estado de una cadena de bloques. Por ejemplo, puede describir cómo se pueden transferir tokens de una cuenta a otra.

## Substrate

Un conjunto de herramientas modular para construir cadenas de bloques. Polkadot se construye usando Substrate. Las cadenas construidas con Substrate serán fáciles de conectar como parachains.

## Tabling

En el sistema de gobernanza de Polkadot, llevar una propuesta a votación por medio de un referéndum. Nótese que este es el significado británico de "presentar", que es diferente de la versión estadounidense, que significa "posponer" una medida.

## Transaction

Un extrinsic que está firmado. Las transacciones se divulgan en la red e incurren en una tarifa de transacción. Las transacciones son "probadamente verdaderas", a diferencia de las heredadas. Por ejemplo, se puede probar que Alice quiere enviar fondos a Bob por el hecho de que firmó un mensaje de transferencia de fondos con su clave privada.

## Validator
Un nodo que asegura la relay chain mediante la vinculación de los DOTs, validando las pruebas de los collators en las parachains y votando el consenso junto con otros validadores.

## Voting

El proceso de los involucrados para determinar si debe aprobarse o no un referéndum. Los votos se ponderan tanto por el número de DOTs que la cuenta de los interesados controla como por la cantidad de tiempo que están dispuestos a bloquear sus DOTs.

## Wallet

Un programa que permite almacenar claves privadas y firmar transacciones para Polkadot u otras redes de cadenas de bloques.

## Wasm

Un formato de instrucciones para una máquina virtual basada en secuencias. Los módulos de ejecución de Polkadot están compilados en Wasm.

## Watermark

En el esquema de mensajes de parachains de Polkadot, la marca de agua es la altura mínima de envío procesada de la parachain receptora. Todos los mensajes de todos los canales que se envían a esta parachain en o antes de la marca de agua están garantizados para ser procesados.

## Web3 Foundation

Una fundación con sede en Suiza que fomenta y administra tecnologías y aplicaciones en los ámbitos de los protocolos de programas informáticos descentralizados de la web, en particular los que utilizan métodos criptográficos modernos para salvaguardar la descentralización, en beneficio y para la estabilidad del ecosistema de la web3.

## WebAssembly

Un formato de instrucciones para una máquina virtual basada en secuencias. Los módulos de ejecución de Polkadot se compilan en WebAssembly. También conocido como Wasm.

## Witness

Declaraciones de prueba criptográfica de la validez de los datos.