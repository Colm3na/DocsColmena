## ¿Qué son los State Channels?

Los State channels se refieren al proceso en el que los usuarios realizan transacciones entre sí directamente fuera de la cadena de bloques, u _"off-chain"_, y minimizan en gran medida el uso de operaciones _"on-chain"_. Es una de las soluciones de escalado para Ethereum más interesantes en el desarrollo y el avance más cercano a estar listo para la producción.

Los state channels son muy similares al concepto de canales de pago en la Red de Lightning de Bitcoin, pero en lugar de sólo apoyar los pagos, también soportan 'actualizaciones de estado' generales. Por ejemplo, los votos realizados en el [District Registry](https://education.district0x.io/district0x-specific-topics/understanding-distict0x/the-district-registry/) podrían ser actualizados en un canal estatal y sólo transmitidos a la red Ethereum una vez que todos los votos hayan sido recopilados. Esto aumenta el número de desarrolladores de computación que pueden salir de la cadena.

## ¿Por qué es tan emocionante?

Aunque a primera vista pueda parecer que las transacciones dentro de los State channels no están respaldadas por el mismo nivel de seguridad que las transacciones en la cadena, lo mágico es que podemos alcanzar el mismo nivel de seguridad sin utilizar tanto de los recursos de la red. Al poder volver siempre a la cadena principal como mecanismo de arbitraje, los usuarios se ven incentivados teóricamente por el juego para actuar racionalmente. Además, cada transacción se firma de la misma manera que una transacción válida de Ethereum.

Las transacciones en cadena no se eliminan por completo, sino que se reducen a las secuencias necesarias. Los usuarios tienen que crear y pagar por una transacción de Ethereum cuando abren el canal por primera vez. Cuando están listos para cerrar el canal, de nuevo tienen que pagar cuotas para procesar una transacción en la cadena de bloques Ethereum. Reducir a dos el número de transacciones necesarias en la cadena reduce drásticamente los costes y aumenta la velocidad asociada con el uso de Ethereum.

Piense en los State channels como una tarjeta de tiempo que usaría en el trabajo. Se marca cuando se empieza a trabajar _(Transacción nº 1)_ y se marca al final del turno _(Transacción nº 2)_. Cada acción que ocurre en el medio no necesita ser registrada en la tarjeta de tiempo.

## State channels bajo la cubierta

Los State channels suenan muy bien en teoría, pero son aún más interesantes cuando se observan en la práctica. He aquí un breve ejemplo para ilustrar cómo funcionan correctamente:

1. Los usuarios bloquean una parte del estado enviando fondos a un contrato multi-firma que tiene la capacidad de aceptar Ether y pagar a todas las partes que lo han enviado.

2. Los usuarios firman las transacciones y se las envían unos a otros, cada uno haciendo una copia de la firma para su posterior consulta.

3. Cada transacción contiene un nonce para que el contrato inteligente pueda conocer el orden cronológico de las transacciones.

4. Una vez que ambas partes han terminado, cierran el estado enviando una transacción a la cadena de bloques de Ethereum.

## ¿Por qué es importante?

Se puede decir que el escalado es el mayor obstáculo al que se enfrentan las cadenas de bloques cuando se trata de lograr la adopción generalizada. Aunque algunas aplicaciones pueden prosperar hoy en día, la mayoría siguen siendo demasiado lentas y caras para los usuarios habituales.

Los State channels aumentan el rendimiento de las cadenas de bloques públicas porque disminuyen la carga computacional que los nodos tienen que gastar al procesar y almacenar transacciones. Esto facilitará el funcionamiento de un nodo, lo que hace que la tarea de validar el trabajo de los mineros sea más descentralizada. De manera similar, los State channels reducen los costos requeridos para usar la red Ethereum. En lugar de pagar por cada transacción, los usuarios sólo tienen que pagar por gas cuando abren y cierran un canal.

Los State channels también ayudan a proteger la privacidad del usuario. Las transacciones dentro de un canal sólo son conocidas por los participantes en el canal. Esto contrasta con las transacciones en la cadena de bloques de Ethereum, donde cada transacción se registra en un libro mayor auditable públicamente.

Por último, las transacciones dentro de los State channels obtienen la irreversibilidad instantánea. Los usuarios no tienen que esperar a que cada transacción se confirme en la cadena de bloques porque cada transacción firmada cumple con las reglas de la red. Esto hace que la experiencia de usuario sea perfecta y se asemeje más a la forma en que operan las aplicaciones en línea más populares en la actualidad.
