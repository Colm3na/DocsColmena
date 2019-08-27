## ¿Qué es el Gas?

>_Esta información esta traducida del [portal de educacion de Distric0x](https://education.district0x.io/) en concreto el apartado de [Gas](https://education.district0x.io/general-topics/understanding-ethereum/what-is-gas/), así pues **muchas gracias [Distric0x](https://district0x.io)** por esta maravillosa documentación!!_

Si alguna vez ha enviado una transacción en la cadena de bloques de Ethereum, ha tenido que seleccionar alguna cantidad de Gas que vaya con ella para que pueda ser confirmada. Sin una cantidad apropiada de Gas, su transacción no será seleccionada por los mineros de la red e incluida en un bloque posterior.

## Vale muy bien, pero ¿qué es el Gas?

El gas es esencial para la red Ethereum, es literalmente el combustible que le permite funcionar. Más específicamente, Gas se refiere a la unidad que mide la cantidad de esfuerzo computacional requerido para ejecutar operaciones específicas en la red Ethereum. Cuando usted quiere participar en una venta de tokens o jugar a CryptoKitties, necesita Gas para incentivar a los mineros a incluir sus transacciones en la cadena de bloques.

Esta tarifa de Gas se paga en ETH, que en la mayoría de los casos se convierte en GWEI para una mejor experiencia del usuario.

Una analogía simple para entender la función del gas en la red Ethereum es compararlo con la forma en que los automóviles necesitan gasolina para funcionar. De la misma manera que los individuos van a la gasolinera y pagan para llenar sus coches, los usuarios de la red Ethereum pagan para que sus contratos inteligentes sean ejecutados por los mineros. Esta es la razón por la que a tantos en la comunidad de la cadena de bloques les gusta referirse al ETH como el _"combustible para la economía digital"_. ETH literalmente se convierte en combustible, lo que incentiva a los mineros a realizar cálculos en una red global.

El gas es vital porque sirve como el principal mecanismo de incentivo en la red de Ethereum. Recuerde que los mineros tienen que utilizar su propia potencia de cómputo para llevar a cabo operaciones de contratos inteligentes, no lo hacen por su buena voluntad, sino porque pueden ganar comisiones por proporcionar un servicio valioso.

Como en cualquier sistema de Proof of Work, la seguridad de la red depende del hashrate de los mineros, que depende principalmente del incentivo monetario para asegurar la red. Cuanto más gas puedan ganar los mineros de Ethereum, más segura será la red.

Cuando se piensa en el gas, hay dos componentes principales: **Gas Limit** y **Gas Price**. El coste total de realizar una operación es el producto de _Gas Limit_ y _Gas Price_ (gas limit x gas price).

## Gas Limit

El _Gas Limit_ se refiere al número máximo de Gas que un usuario está dispuesto a gastar en un cálculo. Algunos cálculos básicos requieren un número predeterminado de Gas y es fácil para las wallets proporcionar estas estimaciones basadas en el tipo de operación que el usuario está tratando de realizar. Por ejemplo, el Ethereum yellow paper afirma que cada transacción requiere 21.000 de Gas. Esta es la razón por la que la mayoría de las interfaces de usuario mostrarán 21.000 como límite de gas de forma predeterminada.

## Gas Price

El precio por unidad de Gas está representado en GWEI, que es una versión más fácil para el usuario de WEI. WEI es equivalente a ETH de la misma manera que un céntimo es equivalente al Euro, es la denominación más pequeña de la moneda. Un GWEI es 10^9 WEI y proporciona una experiencia de usuario mucho mejor para calcular los gastos de gas.

Como era de esperar, cuanto más alto sea el precio propuesto del gas, mayores serán las posibilidades de que la transacción se incluya en el próximo bloque, ya que esto es lo que incentiva a los mineros. El precio por defecto del gas en la mayoría de las interfaces es de 20 GWEI, lo que debería ser suficiente para obtener una transacción en los próximos dos minutos. Aumentar el precio a 40 GWEI probablemente lo llevará al siguiente bloque.
