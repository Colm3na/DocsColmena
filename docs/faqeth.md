# FAQs Validadores ETH2.0

_Este documento es una traducción realizada por [wimel](https://github.com/ethereum/eth2.0-deposit/pull/292) del [FAQ en inglés](https://launchpad.ethereum.org/faq) para la comunidad de habla hispana._

## Introducción

### ¿Qué es exactamente un validador?

Un validador es una entidad que participa en el consenso del protocolo de Ethereum 2.0.

O, en lenguaje llano, un humano ejecutando un proceso informático. Este proceso propone y asegura que se añadan nuevos bloques a la cadena de bloques.

En otras palabras, **puedes pensar en un validador como un candidato para los nuevos bloques**. Cuantos más votos tenga un bloque, más probable es que se añada a la cadena.

Es importante que el voto de un validador sea ponderado por la cantidad que está en juego.

### ¿Qué es el contrato de depósito?

Puedes pensar en ello como una transferencia de fondos entre las cuentas de Ethereum y los validadores de eth2.

Especifica quién participa, quién valida, con cuánto participa y quién puede retirar los fondos.

### ¿Por qué los validadores necesitan tener fondos en juego?

Los validadores necesitan tener fondos en juego para poder ser penalizados por su comportamiento deshonesto.

En otras palabras, para que sean honestos, sus acciones deben tener consecuencias financieras.

### ¿Cuánto ETH necesita depositar un validador?

Antes de que un validador pueda empezar a asegurar la red, necesita depositar 32 ETH. Esto forma el balance inicial del validador.

### ¿Hay alguna ventaja en tener más de 32 ETH en juego?

No. No hay ninguna ventaja en tener más de 32 ETH en juego.
Limitar la participación máxima a 32 ETH fomenta la descentralización del poder, ya que impide que un solo validador tenga un voto excesivamente grande sobre el estado de la cadena.

Recuerda que el voto de un validador es ponderado por la cantidad que tiene en participación.

### ¿Puedo parar mi validador por unos días y luego volver a iniciarlo?

Sí, pero, en condiciones normales, perderá una cantidad de ETH aproximadamente equivalente a la cantidad de ETH que habría ganado en ese período. En otras palabras, si usted ganara ≈0.01 ETH, sería penalizado con ≈0.01 ETH.

### ¿Cuándo debo actualizar el balance de mi validador?

La respuesta a esta pregunta depende en gran medida de la cantidad de ETH que tenga a su disposición.

Ciertamente debes aumentar tu balance si está cerca de 16 ETH: esto es para asegurarte de que no te echen del conjunto de validadores (lo cual ocurre automáticamente si tu balance cae por debajo de 16 ETH).

En el otro extremo del escenario, si tu balance está más cerca de 31 ETH, probablemente no valga la pena añadir los ETHs extras necesarios para alcanzar 32.

### ¿Cuándo puedo retirar mis fondos, y cuál es la diferencia entre salir y retirarlos?

Puede indicar su intención de dejar de validar firmando un mensaje de salida voluntaria con su validador.

Sin embargo, ten en cuenta que en la fase 0, una vez que has salido, no hay vuelta atrás.

No hay forma de que puedas habilitar tu validador de nuevo, y no podrás transferir o retirar tus fondos hasta por lo menos la fase 1.5 (lo que significa que tus fondos permanecerán inaccesibles hasta entonces).

## Responsabilidades

### ¿Cómo se incentivan los validadores para que se mantengan activos y honestos?

Además de ser sancionados por estar fuera de línea, los validadores son sancionados por comportarse de manera maliciosa - por ejemplo, mediante la certificación de bloques inválidos o contradictorios.

Por otro lado, son recompensados por proponer / dar fe de los bloques que se incluyen en la cadena.

El concepto clave es el siguiente:
- Se recompensan las acciones que ayudan a la red a llegar a un consenso
- Se imponen sanciones menores por acciones descuidadas (o inexistentes) que impiden el consenso
- Y se dan penalizaciones importantes - o recortes - por acciones maliciosas

En otras palabras, los validadores que maximizan sus recompensas también proporcionan el mayor beneficio a la red en su conjunto.

### ¿Cómo se establecen las recompensas/penalizaciones?

Recuerde que cada validador tiene su propio balance - con el balance inicial indicado en el contrato de depósito.

Este balance se actualiza periódicamente mediante las reglas de la red Ethereum a medida que el validador cumple (o deja de cumplir) sus responsabilidades.

Dicho de otra manera, las recompensas y penalizaciones se reflejan en el balance del validador a lo largo del tiempo.

### ¿Con qué frecuencia se emiten recompensas/penalizaciones?

Aproximadamente cada seis minutos y medio, un período de tiempo conocido como una época.

En cada época, la red evalúa las acciones de cada validador y emite recompensas o penalizaciones de manera adecuada.

### ¿Qué cantidad de recompensas y penalizaciones hay?

No hay una respuesta fácil a esta pregunta ya que hay muchos factores que entran en este cálculo.

Podría decirse que el factor de mayor impacto en las recompensas obtenidas por la validación de las transacciones es la cantidad total de participación en la red. En otras palabras, la cantidad total de validadores. Dependiendo de esta cifra, la tasa máxima de retorno anual para un validador puede estar entre el 2 y el 20%.

Dado un número total fijo de validadores, las recompensas/penalizaciones se escalan principalmente con el balance del validador - asegurar un balance más alto resulta en mayores recompensas/penalizaciones mientras que asegurar un balance más bajo resulta en menores recompensas/penalizaciones.

>Sin embargo, hay que tener en cuenta que este mecanismo de escalado funciona de una manera no obvia. Para entender los detalles precisos de su funcionamiento es necesario comprender un concepto llamado **equilibrio efectivo**. Si aún no está familiarizado con este concepto, le recomendamos que lea [este excelente post](https://www.attestant.io/posts/understanding-validator-effective-balance/).

### ¿Por qué las recompensas dependen del número total de validadores en la red?

Las recompensas de bloque se calculan usando una escala gradual basada en la cantidad total de ETH depositada en la red.

En pocas palabras: si la cantidad total de ETH depositada es baja, la recompensa (tasa de interés) es alta, pero a medida que la cantidad total depositada aumenta, la recompensa (interés) pagada a cada validador comienza a disminuir.

¿Por qué una escala gradual? Aunque no entraremos en detalles escabrosos aquí, la intuición básica es que se necesita un número mínimo de validadores (y por lo tanto una cantidad mínima de ETH en juego) para que la red funcione correctamente. Por lo tanto, para incentivar a más validadores que se unan, es importante que la tasa de interés se mantenga alta hasta que se alcance este número mínimo.

Posteriormente, se sigue alentando a los validadores a que se unan (cuantos más validadores más descentralizada está la red), pero no es absolutamente esencial que lo hagan (para que el tipo de interés pueda bajar).

### ¿Qué tan grave será la penalización de un validador por estar desconectado?

Depende. Además del [impacto del equilibrio efectivo](https://www.attestant.io/posts/understanding-validator-effective-balance/#the-impact-of-effective-balance-on-validating) hay dos escenarios importantes que hay que tener en cuenta:

1. Estar fuera de la red mientras una gran mayoría (2/3) de los validadores está todavía en línea conduce a penalizaciones relativamente pequeñas ya que todavía hay suficientes validadores en línea para que la cadena finalice. **Este es el escenario esperado**.

2. Estar fuera de línea al mismo tiempo que más de 1/3 del número total de validadores conduce a penalizaciones más fuertes, ya que los bloques no finalizan. **Este escenario es muy extremista y es poco probable que ocurra**.

>Nótese que en el segundo (improbable) escenario, los validadores perderán progresivamente hasta el 50% (16 ETH) de su participación a lo largo de 21 días. Después de 21 días son expulsados de la lista de validadores. Esto asegura que los bloques empiecen a finalizar de nuevo en algún momento.

### ¿Qué tan excelente debe ser el tiempo de actividad de un validador honesto para que sea rentable?

En general, se espera que los validadores sean rentables, siempre y cuando su tiempo de funcionamiento sea
superior al 50%.

Esto significa que los validadores no necesitan llegar a extremos con clientes de respaldo o conexiones de internet redundantes ya que las repercusiones de estar fuera de línea no son tan severas.

### ¿Cuánto se sancionará a un validador por actuar de manera maliciosa?

De nuevo, depende. Comportarse maliciosamente - por ejemplo, demostrando bloques inválidos o contradictorios, conducirá a que la participación de un validador sea recortada.
La cantidad mínima que puede ser recortada es 1 ETH, pero **este número aumenta si otros validadores son penalizados al mismo tiempo**.

La idea detrás de esto es minimizar las pérdidas por errores honestos, pero desanimar en gran medida los ataques coordinados.

### ¿Qué es exactamente la penalización?

La penalización tiene dos propósitos: (1) hacer que sea prohibitivamente caro atacar eth2, y (2) evitar que los validadores sean perezosos comprobando que realmente cumplen con sus obligaciones. Penalizar a un validador es destruir (una porción de) la participación del validador si actúa de una manera destructiva.

A los validadores que son penalizados se les impide seguir participando en el protocolo y se les expulsa por la fuerza.

## Claves

### ¿Qué pasa si pierdo mi clave de firma?

Si se pierde la clave de firma, el validador ya no puede proponer o confirmar.
Con el tiempo, el balance del validador disminuirá a medida que se le penalice por no participar en el proceso de consenso. Cuando el balance del validador llegue a 16 Eth, él o ella saldrá automáticamente del grupo de validadores.

>Sin embargo, no todo está perdido. Suponiendo que los validadores deriven sus claves usando EIP2334 (según el esquema de integración por defecto), **los validadores siempre pueden volver a calcular su clave de firma a partir de su clave de retirada**.

Los 16 Eth pueden ser retirados - con la clave de retirada - después de un plazo de alrededor de un día.

>Tenga en cuenta que este plazo puede ser más largo si muchos otros salen o son expulsados al mismo tiempo.

### ¿Qué pasa si pierdo mi clave de retirada?

Si se pierde la clave de retirada, no hay forma de obtener acceso a los fondos en posesión del validador.
Por lo tanto, es una buena idea crear tus claves a partir de mnemotécnicos que actúan como otra copia de seguridad. Este será el método predeterminado para los validadores que se unan a través del proceso de incorporación de este sitio.

### ¿Qué pasa si me roban la clave de retirada?

Si la clave de retirada es robada, el ladrón puede transferir el saldo del validador, pero sólo una vez que el validador haya salido.
Si la clave de firma no está bajo el control del ladrón, éste no puede sacar el validador.
El usuario con la clave de firma podría intentar sacar rápidamente al validador y luego transferir los fondos - con la clave de retirada - antes que el ladrón.

### ¿Por qué dos claves en vez de una?

En resumidas cuentas, por seguridad. La clave de firma debe estar disponible en todo momento. Como tal, tendrá que ser mantenida online. Como todo lo que está online es vulnerable a ser hackeado, no es una buena idea usar la misma clave para las retiradas.
