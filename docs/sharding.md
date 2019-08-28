## ¿Qué es el Sharding?

>_Esta información esta traducida del [portal de educacion de Distric0x](https://education.district0x.io/) en concreto el apartado de [Sharding](https://education.district0x.io/general-topics/understanding-ethereum/ethereum-sharding-explained/), así pues **muchas gracias [Distric0x](https://district0x.io)** por esta maravillosa documentación!!_

>_Shard_ en español es algo así como fragmentar, trocear...

Sharding se refiere a la división de toda la red Ethereum en múltiples porciones llamadas _"fragmentos"_. Cada _fragmento_ contendría su propio estado independiente, es decir, un conjunto único de saldos de cuentas y contratos inteligentes.

Sharding es definitivamente la solución para escalar Ethereum más compleja. También es el último que se espera que se publique, lo que da a los desarrolladores el tiempo necesario para poder analizarlo y probarlo en entornos de producción.

Antes de entrar en detalles técnicos, es importante conocer el papel que desempeñan los nodos en la red Ethereum. Los nodos son responsables de verificar el trabajo de los mineros y asegurar que se cumplan las reglas de consenso. La mejor manera de hacer esto es mantener una copia completa del libro de contabilidad de Ethereum, de esta manera es fácil verificar el trabajo de un minero. Pero la cadena de bloques Ethereum se está acercando a 1 TB de almacenamiento, por lo que no es práctico que una persona normal ejecute un nodo.

## El gran problema

Esto presenta un gran problema: si los nodos de Ethereum se vuelven demasiado caros para funcionar, la red será más susceptible a la centralización. Al mismo tiempo, requerir que cada transacción sea procesada por cada nodo hará que Ethereum nunca pueda escalar. Sharding es una posible solución a este problema.

Sharding se diferencia tanto de los State Channels como de Plasma en que no intenta mover las transacciones fuera de la cadena de bloques. Lo que está haciendo es intentar dividir la cadena de bloques en múltiples partes, de modo que los nodos no son responsables de procesar cada transacción emitida en la red Ethereum. Sharding plantea la pregunta, ¿necesita cada nodo de la red procesar cada transacción para que una cadena de bloques sea considerada segura?

Más importante aún, Sharding es la opción más formidable de Ethereum para resolver el trilema de escalabilidad. Hasta la fecha, ninguna red de cadenas de bloques puede exhibir los tres rasgos siguientes sin tener que sacrificar uno de ellos:

* Descentralizado
* Escalable
* Seguro

Dentro de un fragmento, los _notarios_ son elegidos al azar para votar periódicamente sobre la validez de los bloques, pensad en los mineros en una cadena de bloques regular. Estos votos son revisados por un comité de la cadena principal de Ethereum y se fusionan a través de lo que se llama un contrato de sharding manager. Estos bloques de fragmentos se denominan collations y se encadenan de la misma manera que los bloques de una cadena de bloques.

De hecho, cada fragmento está vinculado a la cadena principal de Ethereum en forma de árboles de merkle, creando una conexión criptográfica entre los dos. Podemos probar ciertas cosas sobre el shard en relación a cuando fue creado. Cada fragmento actúa como su propia cadena de bloques independiente. Los usuarios de cada fragmento tienen sus propios saldos de cuenta fuera de la red principal de Ethereum y sólo pueden realizar transacciones con otros usuarios del shard.

Una manera fácil de pensar en ello es imaginarse si Ethereum se dividiera en miles de islas. Cada isla puede hacer su propia tarea, puede tener sus propias características y todos los que pertenecen a esa isla pueden disfrutarla. Si quieren contactar con otras islas, tendrán que utilizar algún tipo de protocolo. Eso es lo que Sharding permite. Crea una forma para que cada fragmento almacene los recibos individuales de cada transacción. Dado que son criptográficamente seguros, pueden ser llevados de vuelta a la cadena principal en cualquier momento.

## Desafíos de Sharding

Aunque Sharding suena muy bien en teoría, hay una serie de vectores de ataques potenciales. Un ataque específico es el ataque de toma de control de un solo fragmento. En este esquema, un atacante se apodera de la mayoría de los productores de bloques en un fragmento para crear un fragmento malicioso que puede presentar transacciones no válidas. Los desarrolladores del núcleo de Ethereum apuntan al muestreo aleatorio como una solución, pero aún está en desarrollo activo.

Sharding también es mucho más fácil de implementar en una cadena con Proof of Stake que en una cadena con Proof of Work. Ya hay validadores activos dentro del Proof of Stake que pueden ser asignados aleatoriamente a diferentes fragmentos. En Proof of Work, no se puede hacer nada para detener completamente a un minero de contribuir con el poder de hash a un fragmento en particular. Si conocen el fragmento que están validando, podrían intentar orquestar alguna colusión.
