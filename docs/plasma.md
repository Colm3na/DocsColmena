## ¿Qué es Plasma?

Plasma es otra solución de escalado de segunda capa de Ethereum en desarrollo. Se espera que sea la segunda solución de escalado completamente desplegada en la red principal de Ethereum después de los State channels. Plasma se refiere a un marco que permite la creación de cadenas de bloques "hijas" que utilizan la cadena principal de Ethereum como una capa de confianza y arbitraje. En Plasma, las cadenas hijas pueden configurarse para que se ajusten a las demandas de casos de uso específicos, específicamente aquellos que no son factibles en Ethereum hoy en día. Las aplicaciones descentralizadas que obligan a los usuarios a incurrir en altas tarifas de transacción son mucho más adecuadas para ejecutarse en Plasma.

## Plasma vs. State Channels

Plasma es similar a los State channels en el sentido de que el objetivo subyacente es eliminar de la cadena principal la mayor cantidad posible de transacciones. Las actualizaciones estatales realizadas sobre las cadenas hijas siempre pueden ser devueltas a la red Ethereum en caso de disputa o si el usuario desea dejar de realizar transacciones en la cadena de bloques hijas.

Las cadenas hijas pueden adquirir una complejidad variable. Pueden tener sus propios mecanismos de consenso, sus propios tamaños de bloque, y sus propios tiempos de confirmación, el diseño es muy maleable en relación a cada aplicación. Algunos desarrolladores incluso han comenzado a investigar las cadenas hijas dentro de las cadenas hijas... dentro de las cadenas hijas.

El objetivo final de todo esto es simple: si no es necesario que cada transacción sea validada directamente en la cadena de bloques de Ethereum, podemos crear dApps hoy en día que dan servicio a miles, si no cientos de miles de usuarios.

## ¿Es Plasma seguro?

A primera vista, hay muchos agujeros potenciales que hacen que Plasma parezca inseguro. Similar a los State channels, Plasma aprovecha la cadena de bloques Ethereum como una capa de arbitraje. En el caso de una parte maliciosa, los usuarios siempre pueden volver a la cadena principal como una fuente de confianza. La red principal de Ethereum y las cadenas hijas están vinculadas a través de "contratos raíz", que son sólo contratos inteligentes en la cadena de bloques de Ethereum que contienen las reglas que guían cada cadena hija.

## La importancia de los contratos raíz

Los contratos raíz también son extremadamente importantes porque actúan como el puente que permite a los usuarios mover activos entre Ethereum y las cadenas hijas. Todos los activos tienen que ser creados originalmente en Ethereum. Esto hace que ninguna actividad maliciosa en una cadena hija pueda volver a la cadena principal. Si Alice movió tres [NFTs](https://education.district0x.io/general-topics/understanding-ethereum/erc-721-tokens/) criptográficos a una cadena hija y puede probar que nunca los gastó, siempre puede retirarse de la cadena hija y utilizar sus activos en la red principal de Ethereum.

## Plasma como protección contra actividades maliciosas

La mayor parte de las posibles actividades maliciosas se centran en las cadenas hijas, que están controladas en gran medida por entidades centrales. En una cadena de bloques del tipo DPoS o PoA, hay menos partes que producen y validan bloques, lo que los hace más susceptibles a la corrupción. Plasma protege contra ese riesgo al permitir a los usuarios presentar pruebas de fraude contra cualquiera de los trabajos de los productores de bloques, creando así un control económico de sus incentivos.

## Problemas con Plasma

Una de las principales advertencias de Plasma es que los usuarios tardan mucho más tiempo en retirar sus fondos. Mientras que los State channels permiten a los usuarios retirar sus activos en cualquier momento, los usuarios de Plasma tienen que esperar una ventana de arbitraje predeterminada que suele durar de 7 a 14 días. Esto puede ser una experiencia realmente mala para los usuarios que no tienen un gran número de activos y no quieren esperar semanas para acceder a su valor.

## Recapitulación de Plasma

Hagamos un repaso rápido. Usemos un juego de NFT por ejemplo:

1. Un desarrollador de juegos crea un contrato root en Ethereum que estipula las reglas del juego.

2. Los usuarios pueden mover sus NFTs de Ethereum a la cadena hija a través del contrato raíz.

3. Los usuarios realizan transacciones dentro de la cadena hija, conservando copias de sus mensajes criptográficamente firmados.

4. Los usuarios envían solicitudes de retirada.

5. Los usuarios pueden mover sus fondos de la red Ethereum en 1 - 2 semanas.

## Implicaciones

Al igual que los State channels, Plasma es importante debido a lo drástico que puede aliviar la congestión de Ethereum. Los usuarios quieren tarifas más baratas y un mayor rendimiento, mientras que los desarrolladores quieren que sus dApps alcancen una mayor escalabilidad. Esta es una de las mejores oportunidades que tiene la comunidad para llevar a Ethereum más lejos a las masas.

Plasma y los State channels también pueden combinarse para generar efectos combinados. Hay varios grupos de desarrollo que están trabajando en la construcción de implementaciones de State channels dentro de las cadenas hijas. Los usuarios podrían realizar transacciones dentro de las cadenas hijas a un costo mínimo o nulo y no incurrirían en ningún gasto al retirar fondos de un canal.

La segunda capa de Ethereum apenas está comenzando, pero el trabajo preliminar que ya se ha establecido debería hacer que todos los desarrolladores se entusiasmen con el futuro de Ethereum.
