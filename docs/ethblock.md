# ¿Qué es Ethereum?

> Mucha información está sacada de la [wikipedia](https://es.wikipedia.org/wiki/Ethereum) de Ethereum, así que **muchas gracias [wikipedia](https://es.wikipedia.org/wiki/Wikipedia:Portada)!**

Ethereum es una blockchain pública que fué creada por Vitalik Buterin, en Diciembre de 2013 Vitalik comenzó el desarrollo de una prueba de concepto y fué publicada en Febrero del 2014. Tiene la particularidad de permitir a los desarrolladores crear smart contracts e implementar aplicaciones descentralizadas _(DApps)_.

En la blockchain de Ethereum la _gasolina_ para que todo funcione correctamente es el **Ether** o **ETH** y su símbolo es **Ξ**.

Las unidades del Ether son _(de mayor a menor)_:

| Unidad | Nombre |
|--------|--------|
|   1    |  ether |
| 10 <sup>3</sup> | finney |
| 10 <sup>6</sup> |  szabo |
| 10 <sup>9</sup> | shannon |
| 10<sup>12</sup> | babbage |
| 10 <sup>15</sup>| lovelace|
| 10 <sup>18</sup>|   wei   |

> Simplificando, **Ethereum** es la **tecnología blockchain** y el **Ether** es **su criptodivisa**.

## Smart contracts

Un smartcontract o contrato inteligente, es un programa informático que ejecuta acuerdos establecidos entre dos o más partes, estas acciones son el resultado de que se cumplan una serie de condiciones específicas. Estos se ejecutan en un sistema no controlado por ninguna de las partes, en un sistema descentralizado.

::Por lo tanto::

- Se programan las condiciones.

- Se firma por ambas partes.

- Se coloca en la blockchain para impedir su modificación.

::Sus objetivos son::

- Sumar un estado de seguridad mayor al del contrato tradicional.
- Reducir costes.
- Reduce el tiempo con las interacciones.

En resumen, los _SmartContracts_ buscan mejorar los contratos actuales siendo más seguros, más baratos, ahorrándonos tiempo y evitándonos fraudes.

## Oráculos

Es un software o hardware que permite actualizar el estado de los contratos inteligentes con información externa a la blockchain, es decir, funcionan como un nexo entre el mundo real y la blockchain para proporcionar información a los smartcontracts.

## Tokens

 Los tokens originalmente eran fichas o vales que se podían utilizar como sustituto de una moneda real. Un buen ejemplo de ello serían las fichas de un casino, sustituyen al dinero real, pero únicamente se pueden usar en el casino.

 Cuando hablamos de tokens en blockchain, nos referimos a un activo digital implementado dentro de la misma; se hicieron muy famosos con las [ICOs](https://es.wikipedia.org/wiki/Oferta_inicial_de_monedas), usadas para realizar financiaciones de start-ups para obtener el capital necesario para iniciar el proyecto.

Los tokens en Ethereum son activos digitales que se construyen en la parte superior de la blockchain de Ethereum, de esta forma, los desarrolladores se benefician de toda la infraestructura de Ethereum para sus aplicaciones.

**Dentro de tokens podemos encontrar tres tipos:**

· Security Token (STO).

· Utility Token.

· Equity token.

### Security Token(STO)

Los security tokens están respaldados por algo, como activos o beneficios de una compañía, asi pues, están considerados como inversiones.  Los emisores de security tokens tienen que cumplir con los requisitos legales allí donde los tokens están siendo emitidos y comercializados.

La SEC establece que para que un token sea considerado “security” tiene que pasar un test ([Howey test](https://medium.com/bittrust/passing-the-howey-test-how-to-regulate-blockchain-tokens-d218da93a8b6)), qué consiste en verificar que:

- NO es una inversión de dinero.

- NO tiene expectativas de lucro.

- NO está basado principalmente en el esfuerzo de otros.

### Utility Token

Representan el acceso futuro al producto o servicio de una empresa, estos no están diseñados como inversiones, si no qué son como _“cupones”_ para el servicio que esté desarrollando la empresa.

Dentro de esta categoría podemos encontrar dos tipos de tokens, fungibles y no fungibles.

- **_Fungible_**:  Intercambiables, uniformes y divisibles.

- **_No fungible_**: No intercambiables, únicos y no divisibles.

### Equity token

Representa la propiedad de una parte de la organización.

### Estándar ERC-20

El estándar [ERC-20](https://github.com/ethereum/EIPs/issues/20) es un estándar para tokens fungibles en Ethreum, define una lista común de reglas para todos los tokens creados encima de Ethereum, así facilita la tarea a los desarrolladores al permitirles predecir como funcionaran esos tokens dentro del sistema. Para cumplir con los estándares, se debe incorporar unas funciones que permitirán realizar las siguientes acciones:

- Obtener el suministro total de tokens.

- Obtener el saldo de la cuenta.

- Transferir el token.

- Gastar el token.

**El token debe estar formado por nueve métodos y dos eventos:**

**Métodos:**

· Name(opcional): Nombre del Token.

· Symbol(opcional): Símbolo del token.
    
· Decimals(opcional): El número de decimales que utiliza el token.
    
· TotalSupply: Suministro total de tokens que existirán.
    
· BalanceOf: Saldo de la cuenta del propietario.
    
· Transfer: Transferencia a …
    
· TransferFrom: Transferencia desde …
    
· Approve:  Permite la retirada de fondos.

· Allowance: Devuelve la cantidad que se puede retirar.

**Eventos:**

· Transfer: Activado cuando se transfieren los tokens.

· Approval: Activado cuando se apruebe la transferencia.

### Estándar ERC-721

El estándar [ERC-721](https://eips.ethereum.org/EIPS/eip-721) es un estándar para tokens no fungibles, describe cómo construir tokens no fungibles o únicos en Ethereum. Aunque la mayoría de los tokens son fungibles (cada token es igual que cada otro token), todos los tokens ERC-721 son únicos, el mejor ejemplo de token ERC-721 es el famoso [CryptoKitties](https://www.cryptokitties.co/), esto permite que cada token tenga su identidad propia y características únicas, las cuales hacen posible la fijación de un precio especial para su intercambio, según sus parámetros adicionales. De esta forma la red puede contener ciertos tokens más deseables que otros y de mayor valor para los miembros de la comunidad. Los tokens ERC721 se mantienen en su estado original y se compran, venden o intercambian de esa forma.

>[Aquí](https://github.com/OpenZeppelin/openzeppelin-solidity/blob/master/contracts/token/ERC721/ERC721.sol) un ejemplo por [OpenZeppelin](https://openzeppelin.org) de un token ERC721.

---

_Resumiendo, las criptomonedas son una forma de dinero digital y los tokens representan un activo o utilidad. Mientras que las criptomonedas cuentan con su propia blockchain, los tokens operan “encima” de otra blockchain. La finalidad de las criptomonedas es ser una unidad de valor en cambio y los tokens pueden representar cualquier activo._

---
