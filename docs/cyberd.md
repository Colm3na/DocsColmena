# Cyberd

![alt text](images/logo.png?raw=true "Logo Cyberd")


En este repositorio puedes encontrar algunos scripts para gestionar el nodo de [Cyberd](https://github.com/cybercongress/cyberd/blob/master/docs/cyberd.md) .

Si quieres saber algo más [este](https://github.com/cybercongress/cyberd) es su repositorio, [aquí](https://github.com/cybercongress/cyberd/tree/master/docs) puedes encontrar más documentación de Cyberd, [aquí](https://github.com/cybercongress/cyberd/blob/master/docs/run_validator.md) como ser validador en Cyberd, y este es su [hub oficial](https://hub.docker.com/r/cyberd/cyberd) de Docker.

[Este](https://t.me/fuckgoogle) es su grupo de telegram, [esta](https://twitter.com/cyber_devs) es su cuenta de Twitter y [esta](https://cybercongress.ai/) su web y el blog.

Con estos scripts puedes manejar el docker del validador.

> **Recuerda que necesitas cambiar los valores de los scripts por los tuyos**.

> **Si necesitas algún script y no esta en este repositorio, puedes hacer un PR o abrir una ISSUE con lo que necesites**.

> _Si tienes algún problema siempre puedes pasar por la [Colmena](https://www.coworkingcolmena.com) para preguntar y aprender lo que necesites_.


## Cómo usar el repositorio: 

- Necesitas instalar <a href="https://github.com/stedolan/jq/wiki"> jq</a>:

`sudo apt install -y jq`

- Clona el repositorio:

`git clone https://github.com/Colm3na/Cyberd.git`

- Dirígete a la carpeta [scripts](https://github.com/Colm3na/Cyberd/tree/master/scripts), y dale permisos de ejecución:

`cd scripts/`

`chmod +x *`

- Usa el script que necesites:

`./balance`


## Creating a new validator in Cyberd

**WARNING: This technique should only be used in TESTNET. NEVER FOLLOW THESE INSTRUCTIONS IN MAINNET. You would lose all your delegators and reputation.**

Imagine that you have been jailed and that you are in buggy testnet like `euler-4`. This was my case. And I was being the most jailed validator in history, spending more time in jail than `The Shawshank Redemption`'s protagonist.

Imagine you are in this desperate situation or maybe some other one I cannot think of, the point being: you need/want to create a new validator. 

How do you that?

Well, in this mini-guide I hope to show you how to do this in a simple manner (thank you Save The Ales for showing me the wisdom).

**1.** Go to you cyberd folder located in the root directory.

`cd /cyberd`

_This is where the cyberd docker container is taking the information from. Basically, the files that determine our validator's identity are `node_key.json` and `priv_validator_key.json`._

**2.** Making sure that we create a new validator.
If now we run

`docker exec cyberd cyberd tendermint show-validator`

**_Write down our validator identifier (should start with_** `cybervalconspub`**_), we will be sure that we are creating a new validator._**

**3.** Remove the `node_key.json` and `priv_validator_key.json` files.
In my case I just changed their name.

`mv daemon/config/node_key.json daemon/config/node_keyold.json`

`mv daemon/config/priv_validator_key.json daemon/config/priv_validator_keyold.json`
</pre>

**4.** Restart the docker container.

`docker restart cyberd`

It will take a little while until you can connect again with the `cyberdcli`.
You can check when the cli is avaliable again using `docker exec cyberd cyberdcli status` repeatedly. It doesn't take too long.

**5.** Check your new validator's pubkey!

`docker exec cyberd cyberd tendermint show-validator`

>If everything went well you should have now a new validator pubkey and are ready to create your fresh new validator.

>Nevertheless, I would keep the old `node_key.json` and `priv_validator_key.json` in some backup folder just in case.

**6.** Create your new validator.
Just like you created the old one, do 

<pre>
docker exec -ti cyberd cyberdcli tx staking create-validator \
  --amount=10000000cyb \
  --min-self-delegation "1000000" \
  --pubkey=<your_node_pubkey> \
  --moniker=<your_node_nickname> \
  --trust-node \
  --from=<your_key_name> \
  --commission-rate="0.10" \
  --commission-max-rate="0.20" \
  --commission-max-change-rate="0.01" \
  --chain-id=<testnet_chain_id>
</pre>

and <em>voilà!</em> You have your new validator running.

You can check it with 
```
docker exec cyberd cyberdcli query staking validator <cybervaloper...>
```
and see those wonderful `Jailed: false` and `Status: Bonded`  🤩

**I hope this mini-guide was helpful for you all! Any comments and improvements please, don't hesitate.**