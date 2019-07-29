# Kava

- [Repositorio oficial](https://github.com/Kava-Labs/kava)

### configuración para el validador _(puedes encontrar estos tips en la [documentacion](https://kava.network/docs/validators/validator-setup.html#validator-setup) de kava y el cliente [Kvcli](https://kava.network/docs/gaia/kvcli.html#gaia-cli))_:

#### Comandos para `kava-testnet-1.1`:
* **Inicio de un nuevo nodo:**

```
kvd init --moniker <your_custom_moniker>
```

* **Inicio kvd:**
```
kvd start
```

* **Para la resolución de problemas:**
```
kvd start --trace --log_level "*:debug"
```

* **Comprobar el estado de kvd:**
```
kvcli status
```

* **Generar el _`gentx`_ para `kava-testnet-1.1` _(recuerda modificar los valores)_**:
```
kvd gentx --amount 1000000000000ukva --commission-rate "0.10" --commission-max-rate "1.00" --commission-max-change-rate "0.01" --pubkey $(kvd tendermint show-validator) --name $(kvcli keys list | awk 'FNR==2{print $1}')
```

### Configuración del validador _(recuerda modificar los valores)_:
* **Crear validador:**
```
kvcli tx stake create-validator --amount=5STAKE --pubkey=$(kvd tendermint show-validator) --moniker="choose a moniker" --chain-id=<chain_id> --from=<key_name> --commission-rate="0.10" --commission-max-rate="0.20" --commission-max-change-rate="0.01"
```

* **Editar la descripción del validador:**
```
kvcli tx staking edit-validator --commision-rate="<new_rate_to_apply>" --fees="<new-fees-to-apply>" --moniker="<your_moniker>" --website="<your_website>" --identity="<keybase_sig>" --details="<your_description>" --chain-id="<chain_id>" --from="<key_name>"
```

  * Información útil:
  1. Cada parámetro que se omita simplemente no cambiará.
  2. El parámetro 'identity'es la clave pgp generada dentro de keybase ("Add PGP key").
  3. El parámetro 'from' es el nombre de tu cuenta que ves cuando haces `kvcli keys list`.

* **Ver la descripción del validador:**
```
kvcli query stake validator <account_kava>
```

* **Generar la wallet:**
```
kvcli keys add <account_name>
```

* **Mostrar todas las wallets:**
```
kvcli keys list
```

* **Mirar la wallet generada:**
```
kvcli keys show <account_name>
```

* **Address para operar del validador:**
```
kvcli keys show <account_name> --bech=val
```

* **Clave pública para el nodo del validador:**
```
kvd tendermint show-validator
```

* **Ver la descripción del validador:**
```
kvcli query stake validator <account_kava>
```

* **Track validator signing information:**
```
kvcli query slashing signing-info <validator-pubkey> --chain-id=<chain_id>
```

* **_Unjail_ validador:**
```
kvcli tx slashing unjail --from=$(kvcli keys list | awk 'FNR==2{print $1}') --chain-id=<chain_id> --trust-node=true
```

* **Confirmar que el validador está funcionando:**
```
kvcli query tendermint-validator-set | grep "$(kvd tendermint show-validator)"
```

* **Balance:**
```
kvcli query account <account_kava>
```

* **Enviar tokens:**
```
kvcli tx send --amount=10ukva --chain-id=<chain_id> --from=<key_name> --to=<destination_kava>
```

* **Vincular tokens:**
```
kvcli tx stake delegate --amount=10ukva --validator=<validator> --from=<key_name> --chain-id=<chain_id>
```

* **Ver información del validador:**
```
kvcli query stake delegation --address-delegator=<account_kava> --validator=<account_kavaval>
```

* **Comprobar todas las actuales delegaciones de distintos delegadores:**
```
kvcli query stake delegations <account_kava>
```

* **Desvincular tokens:**
```
kvcli tx stake unbond --validator=<account_kavaval> --shares-fraction=0.5 --from=<key_name> --chain-id=<chain_id>
```

* **Mirar información acerca de _`unbonding-delegation`_:**
```
kvcli query stake unbonding-delegation --address-delegator=<account_kava> --validator=<account_kavaval>
```

* **Comprobar todas las actuales _`unbonding-delegations`_ de distintos delegadores:**
```
kvcli query stake unbonding-delegations <account_kava>
```

* **Comprobar todas las _`unbonding-delegations`_ de un validador en particular:**
```
  kvcli query stake unbonding-delegations-from <account_kavaval>
```

* **Redelegar tokens:**
```
kvcli tx stake redelegate --addr-validator-source=<account_kavaval> --addr-validator-dest=<account_kavaval> --shares-fraction=50 --from=<key_name> --chain-id=<chain_id>
```

* **Consultas de las redelegaciones:**
```
kvcli query stake redelegation --address-delegator=<account_kava> --addr-validator-source=<account_kavaval> --addr-validator-dest=<account_kavaval>
```

* **Comprobar todas las actuales _`unbonding-delegations`_ de distintos validadores:**
```
kvcli query stake redelegations <account_kava>
```

* **Todas las redelegaciones salientes para un validador en particular**
```
kvcli query stake redelegations-from <account_kavaval>
```

* **Ajustes actuales de alto nivel para realizar el stake:**
```
kvcli query stake parameters
```

### Governanza:
* **Crear una propuesta de gobernanza:**
```
kvcli tx gov submit-proposal --title=<title> --description=<description> --type=<Text/ParameterChange/SoftwareUpgrade> --deposit=<10ukva> --from=<name> --chain-id=<chain_id>
```

* **Consulta de propuestas _(una vez creadas)_:**
```
kvcli query gov proposal --proposal-id=<proposal_id>
```

* **Consultar todas las propuestas disponibles:**
```
kvcli query gov proposals
```

* **Aumento del depósito de las propuestas _(por defecto `10ukva`)_:**
```
kvcli tx gov deposit --proposal-id=<proposal_id> --deposit=<10ukva> --from=<name> --chain-id=<chain_id>
```

* **Consultar todos los depósitos presentados _(una vez creada una nueva propuesta)_:**
```
kvcli query gov deposits --proposal-id=<proposal_id>
```

* **Depósito de consulta _(dirección específica)_:**
```
kvcli query gov deposit --proposal-id=<proposal_id> --depositor=<account_kava>
```

* **Votar en una propuesta:**
```
kvcli tx gov vote --proposal-id=<proposal_id> --option=<Yes/No/NoWithVeto/Abstain> --from=<name> --chain-id=<chain_id>
```

* **Consulta de votos _(opción enviada)_:**
```
kvcli query gov vote --proposal-id=<proposal_id> --voter=<account_kava>
```

* **Propuesta presentada anteriormente:**
```
kvcli query gov votes --proposal-id=<proposal_id>
```

* **Propuesta de consulta para los resultados**
```
kvcli query gov tally --proposal-id=<proposal_id>
```

### Variables usadas:
* **Id de la rama:**
```
curl -s http://localhost:26657/status | jq -r '.result.node_info.network'
```

* **Wallet kava:**
```
kvcli keys list | awk 'FNR==2{print $3}'
```

* **Nombre de la wallet:**
```
kvcli keys list | awk 'FNR==2{print $1}'
```

* **kavavaloper:**
```
kvcli keys show $(kvcli keys list | awk 'FNR==2{print $1}') --bech=val | awk 'FNR==2{print $3}'
```

* **Balance:**
```
kvcli query account $(kvcli keys list | awk 'FNR==2{print $3}') --chain-id=${chain_id} --trust-node=true | jq -r '.value.coins[0].amount'
```
* **ID de la proposición:**
```
kvcli query gov proposals --trust-node=true | tail -n 1 | cut -d'-' -f1
```

* **Conectarse a los _endpoints_:**
```
ssh -i ~/.ssh/user_rsa -L 26657:localhost:26657 user@[ IP ]
```
