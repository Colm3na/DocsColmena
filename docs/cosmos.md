<h1 align="center"> Repositorio con varios scripts y guias para Cosmos</h1>

<p align="center"> 
<img src="/images/cosmos/CosmosSvQ.png">
</p>

<p align="center"> Esta información ha sido traducida del repositorio oficial de <a href="https://github.com/cosmos/cosmos-sdk/tree/develop/docs">Cosmos.</a> </p>

<p align="center">
Puedes encontrar información para los <a href="https://github.com/Colm3na/Cosmos-Validators/tree/wimelTesting/delegadores">delegadores</a> y los <a href="https://github.com/Colm3na/Cosmos-Validators/tree/wimelTesting/validadores"> validadores.</a>
</p>

<p align="center">
Recuerda que si tienes alguna duda siempre puedes venir a la <a href="https://www.coworkingcolmena.com">Colmena</a> para resolverla juntos.
</p>

---

## Delegador


<p align="center"> 
<img src="/images/cosmos/cosmosLogo.png">
</p>


_Esta información ha sido traducida del repositorio de [Cosmos](https://cosmos.network/docs/gaia/delegator-guide-cli.html#table-of-contents)_

#### Guía para el Delegador (CLI):
 
Este documento contiene toda la información necesaria para que los delegadores interactúen con el Cosmos Hub a través de la Interfaz Comando-Línea (CLI).

_También contiene instrucciones sobre cómo administrar las cuentas, restaurar las cuentas desde la recaudación de fondos y usar un dispositivo LedgerNano._


#### Cuentas de Cosmos:

En el centro de cada cuenta del Cosmos, hay una semilla, que toma la forma de una mnemotecnia de 12 o 24 palabras. Desde esta mnemotecnia, es posible crear cualquier número de cuentas Cosmos, es decir, pares de claves privadas/llaves públicas. Esto se denomina billetera HD (ver <a href="https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki">BIP32</a> para más información sobre la especificación de la billetera HD)

_Los fondos almacenados en una cuenta son controlados por la clave privada. Esta clave privada se genera utilizando una función unidireccional de la mnemotécnica. Si pierde la clave privada, puede recuperarla usando la mnemotécnica. Sin embargo, si pierde la mnemotécnica, perderá el acceso a todas las claves privadas derivadas. Del mismo modo, si alguien obtiene acceso a tu mnemotécnica, obtiene acceso a todas las cuentas asociadas._

#### Restaurar una cuenta de la recaudación de fondos:

_Si usted participó en la recaudación de fondos, debe tener en su poder una mnemotécnica de 12 palabras. Los mnemónicos recién generados usan 24 palabras, pero los mnemónicos de 12 palabras también son compatibles con todas las herramientas de Cosmos._

#### En una Ledger:

En el núcleo de un dispositivo Ledger, hay una mnemotécnica utilizada para generar cuentas en múltiples cadenas de bloques (incluyendo el Cosmos Hub). Normalmente, creará una nueva mnemotécnica cuando inicialice el dispositivo Ledger. Sin embargo, es posible decirle al dispositivo Ledger que utilice un mnemotécnico proporcionado por el usuario. Sigamos adelante y veamos cómo puedes introducir la mnemotécnica que obtuviste durante la recaudación de fondos como la semilla de tu dispositivo Ledger.

Los siguientes pasos deben realizarse en un dispositivo de ledger no inicializado:

1. Conecte su dispositivo Ledger al ordenador a través de USB

2. Presione ambos botones

3. NO elija la opción `"Configurar como nuevo dispositivo"`. En su lugar, elija `"Restaurar configuración"`.

4. Elija un PIN

5. Elija la opción de 12 palabras

6. Ingrese cada una de las palabras que recibió durante la recaudación de fondos, en el orden correcto.

_Su ledger está ahora correctamente configurado con su mnemotécnico de recaudación de fondos! No pierdas este mnemotécnico! Si su Ledger está comprometida, siempre puede restaurar un nuevo dispositivo utilizando la misma mnemotécnica._

#### Creando una cuenta:

_Para crear una cuenta, sólo necesitas tener instalado `gaiacli`. Antes de crearlo, necesita saber dónde desea almacenar e interactuar con sus claves privadas. Las mejores opciones son almacenarlas en un ordenador dedicado sin conexión o en una Ledger wallet. Almacenarlas en su computadora en línea implica más riesgo, ya que cualquiera que se infiltre en su computadora a través de Internet podría extraer sus claves privadas y robar sus fondos._

#### Usando una Ledger wallet:

Al inicializar la Ledger, se genera una mnemotécnica de 24 palabras que se almacena en el dispositivo. Esta mnemotécnica es compatible con Cosmos y de ella se pueden derivar cuentas del Cosmos. Por lo tanto, todo lo que tienes que hacer es hacer tu libro de contabilidad compatible con gaiacli. Para ello, debe seguir los siguientes pasos:

1. Descargue la aplicación Ledger [aquí](https://www.ledger.com/pages/ledger-live).

2. Conecte su Ledger a través de USB y actualícelo con el firmware más reciente.

3. Vaya a la tienda de aplicaciones de Ledger y descargue la aplicación "Cosmos" (_esto puede tardar un poco_). Nota: Para poder descargar la aplicación "Cosmos", es posible que tenga que habilitar el `modo de desarrollo` en la `configuración` del Ledger Live.

4. Navegue hasta la aplicación Cosmos en su Ledger.

Luego, para crear una cuenta, use el siguiente comando:

`gaiacli keys add <NombreDeLaCuenta> --ledger`

* `NombreDeLaCuenta` es el nombre de la cuenta. Es una referencia al número de cuenta utilizado para derivar el par de claves de la mnemotécnica. Usted usará este nombre para identificar su cuenta cuando quiera enviar una transacción.

* Puede añadir el indicador opcional `--account` para especificar la ruta (`0`, `1`, `2`,...) que desea utilizar para generar su cuenta. Por defecto, se genera la cuenta `0`.

#### En un ordenador:

Para restaurar una cuenta utilizando una nemotécnica de recaudación de fondos y almacenar la clave privada cifrada asociada en un ordenador, utilice el siguiente comando:

`gaiacli keys add --recover <NombreDeWallet>`

Se le pedirá que introduzca una frase de contraseña que se utiliza para cifrar la clave privada de la cuenta `0` en el disco. Cada vez que desee enviar una transacción, se le solicitará esta contraseña. Si pierdes la contraseña, siempre puedes recuperar la clave privada con la mnemotécnica.

* `<NombreDeWallet>`  es el nombre de la cuenta. Es una referencia al número de cuenta utilizado para derivar el par de claves de la mnemotécnica. Usted usará este nombre para identificar su cuenta cuando quiera enviar una transacción.

* Puede añadir el indicador opcional `--account` para especificar la ruta (0, 1, 2,...) que desea utilizar para generar su cuenta. Por defecto, se genera la cuenta `0`.

<br>

**En [este](https://github.com/Colm3na/Cosmos/tree/master/delegadores/scripts_testnets) directorio se pueden encontrar algunos scripts para usar en la testnet que ayudan a gestionar los fondos de Cosmos.**

**En [este](https://github.com/Colm3na/Cosmos/tree/master/delegadores/scripts_mainnet) directorio se pueden encontrar algunos scripts para usar en la mainnet que ayudan a gestionar los fondos de Cosmos.**

#### ¿Como usar los scripts?

* Para poder usar los scripts necesitamos clonar el repositorio y darle permisos de ejecución a los mismos.

1. Clonamos el repositorio en nuestro ordenador:

    `git clone https://github.com/Colm3na/Cosmos-Delegators.git`

2. Entramos en el directorio que contiene los scripts y le damos permisos de ejecución a los scripts(`chmod +x`):

    `cd Cosmos-Delegators/scripts/`

    `chmod +x *`

3. Ejecutamos los scripts poniendo `./` + el nombre del script (debemos estar en el directorio scripts):

    > Ej:
    `./balance`


--- 

## Validador

### configuración para el validador _(puedes encontrar estos tips en la [documentacion](https://cosmos.network/docs/validators/validator-setup.html#validator-setup) de Cosmos y el cliente [Gaia](https://cosmos.network/docs/gaia/gaiacli.html#gaia-cli))_:

### Comandos:
* **Inicio de un nuevo nodo:**
```
gaiad init --moniker <your_custom_moniker>
```

* **Inicio gaiad:**
```
gaiad start
```

* **Para la resolución de problemas:**
```
gaiad start --trace --log_level "*:debug"
```

* **Comprobar el estado de gaiad:**
```
gaiacli status
```

* **Generar el _`gentx`_ para `GoS` _(recuerda modificar los valores)_**:
```
gaiad gentx --amount 10000STAKE --commission-rate "0.10" --commission-max-rate "1.00" --commission-max-change-rate "0.01" --pubkey $(gaiad tendermint show-validator) --name $(gaiacli keys list | awk 'FNR==2{print $1}')
```

# Configuración del validador _(recuerda modificar los valores)_:
* **Crear validador:**
```
gaiacli tx stake create-validator --amount=5STAKE --pubkey=$(gaiad tendermint show-validator) --moniker="choose a moniker" --chain-id=<chain_id> --from=<key_name> --commission-rate="0.10" --commission-max-rate="0.20" --commission-max-change-rate="0.01"
```

* **Editar la descripción del validador:**
```
gaiacli tx stake edit-validator --moniker="choose a moniker" --website="https://cosmos.network" --identity=6A2265E29A4CBC8E --details="To infinity and beyond!" --chain-id=<chain_id> --from=<key_name> --commission-rate="0.10"
```

* **Ver la descripción del validador:**
```
gaiacli query stake validator <account_cosmos>
```

* **Generar la wallet:**
```
gaiacli keys add <account_name>
```

* **Mostrar todas las wallets:**
```
gaiacli keys list
```

* **Mirar la wallet generada:**
```
gaiacli keys show <account_name>
```

* **Address para operar del validador:**
```
gaiacli keys show <account_name> --bech=val
```

* **Clave pública para el nodo del validador:**
```
gaiad tendermint show-validator
```

* **Ver la descripción del validador:**
```
gaiacli query stake validator <account_cosmos>
```

* **Track validator signing information:**
```
gaiacli query slashing signing-info <validator-pubkey> --chain-id=<chain_id>
```

* **_Unjail_ validador:**
```
gaiacli tx slashing unjail --from=$(gaiacli keys list | awk 'FNR==2{print $1}') --chain-id=game_of_stakes_5 --trust-node=true
```

* **Confirmar que el validador está funcionando:**
```
gaiacli query tendermint-validator-set | grep "$(gaiad tendermint show-validator)"
```

* **Balance:**
```
gaiacli query account <account_cosmos>
```

* **Enviar tokens:**
```
gaiacli tx send --amount=10STAKE --chain-id=<chain_id> --from=<key_name> --to=<destination_cosmos>
```

* **Vincular tokens:**
```
gaiacli tx stake delegate --amount=10STAKE --validator=<validator> --from=<key_name> --chain-id=<chain_id>
```

* **Ver información del validador:**
```
gaiacli query stake delegation --address-delegator=<account_cosmos> --validator=<account_cosmosval>
```

* **Comprobar todas las actuales delegaciones de distintos delegadores:**
```
gaiacli query stake delegations <account_cosmos>
```

* **Desvincular tokens:**
```
gaiacli tx stake unbond --validator=<account_cosmosval> --shares-fraction=0.5 --from=<key_name> --chain-id=<chain_id>
```

* **Mirar información acerca de _`unbonding-delegation`_:**
```
gaiacli query stake unbonding-delegation --address-delegator=<account_cosmos> --validator=<account_cosmosval>
```

* **Comprobar todas las actuales _`unbonding-delegations`_ de distintos delegadores:**
```
gaiacli query stake unbonding-delegations <account_cosmos>
```

* **Comprobar todas las _`unbonding-delegations`_ de un validador en particular:**
```
  gaiacli query stake unbonding-delegations-from <account_cosmosval>
```

* **Redelegar tokens:**
```
gaiacli tx stake redelegate --addr-validator-source=<account_cosmosval> --addr-validator-dest=<account_cosmosval> --shares-fraction=50 --from=<key_name> --chain-id=<chain_id>
```

* **Consultas de las redelegaciones:**
```
gaiacli query stake redelegation --address-delegator=<account_cosmos> --addr-validator-source=<account_cosmosval> --addr-validator-dest=<account_cosmosval>
```

* **Comprobar todas las actuales _`unbonding-delegations`_ de distintos validadores:**
```
gaiacli query stake redelegations <account_cosmos>
```

* **Todas las redelegaciones salientes para un validador en particular**
```
gaiacli query stake redelegations-from <account_cosmosval>
```

* **Ajustes actuales de alto nivel para realizar el stake:**
```
gaiacli query stake parameters
```

# Governanza:
* **Crear una propuesta de gobernanza:**
```
gaiacli tx gov submit-proposal --title=<title> --description=<description> --type=<Text/ParameterChange/SoftwareUpgrade> --deposit=<40STAKE> --from=<name> --chain-id=<chain_id>
```

* **Consulta de propuestas _(una vez creadas)_:**
```
gaiacli query gov proposal --proposal-id=<proposal_id>
```

* **Consultar todas las propuestas disponibles:**
```
gaiacli query gov proposals
```

* **Aumento del depósito de las propuestas _(por defecto `10STAKE`)_:**
```
gaiacli tx gov deposit --proposal-id=<proposal_id> --deposit=<200STAKE> --from=<name> --chain-id=<chain_id>
```

* **Consultar todos los depósitos presentados _(una vez creada una nueva propuesta)_:**
```
gaiacli query gov deposits --proposal-id=<proposal_id>
```

* **Depósito de consulta _(dirección específica)_:**
```
gaiacli query gov deposit --proposal-id=<proposal_id> --depositor=<account_cosmos>
```

* **Votar en una propuesta:**
```
gaiacli tx gov vote --proposal-id=<proposal_id> --option=<Yes/No/NoWithVeto/Abstain> --from=<name> --chain-id=<chain_id>
```

* **Consulta de votos _(opción enviada)_:**
```
gaiacli query gov vote --proposal-id=<proposal_id> --voter=<account_cosmos>
```

* **Propuesta presentada anteriormente:**
```
gaiacli query gov votes --proposal-id=<proposal_id>
```

* **Propuesta de consulta para los resultados**
```
gaiacli query gov tally --proposal-id=<proposal_id>
```

# Variables usadas:
* **Id de la rama:**
```
curl -s http://localhost:26657/status | jq -r '.result.node_info.network'
```

* **Wallet Cosmos:**
```
gaiacli keys list | awk 'FNR==2{print $3}'
```

* **Nombre de la wallet:**
```
gaiacli keys list | awk 'FNR==2{print $1}'
```

* **Cosmosvaloper:**
```
gaiacli keys show $(gaiacli keys list | awk 'FNR==2{print $1}') --bech=val | awk 'FNR==2{print $3}'
```

* **Balance:**
```
gaiacli query account $(gaiacli keys list | awk 'FNR==2{print $3}') --chain-id=${chain_id} --trust-node=true | jq -r '.value.coins[0].amount'
```
* **ID de la proposición:**
```
gaiacli query gov proposals --trust-node=true | tail -n 1 | cut -d'-' -f1
```

* **Conectarse a los _endpoints_:**
```
ssh -i ~/.ssh/user_rsa -L 26657:localhost:26657 user@[ IP ]
```

