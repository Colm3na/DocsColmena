#Pasos para instalar un nodo en la red de [Kusama](https://kusama.network/es/index.html)

##Actualizamos el sistema:

`sudo apt update && sudo apt -y upgrade`

##Instalamos Rust:

`curl https://sh.rustup.rs -sSf | sh`

##Instalamos dependencias:

`sudo apt install -y make clang pkg-config libssl-dev build-essential`

##Actualizamos Rust:

`rustup update`

##Instalamos Polkadot:

```
git clone https://github.com/paritytech/polkadot.git && cd polkadot/

cargo clean

./scripts/init.sh

cargo install --path ./ --force

cd ..

mv polkadot /usr/local
```

##Creamos un archivo de configuración para el servicio de sistema del nodo

`sudo vim /etc/systemd/system/kusama.service`

>Dentro copiamos lo siguiente:

>**Recuerda cambiar NAME por el nombre de tu nodo**

```
[Unit]
Description=Kusama full node

[Service]
ExecStart=/usr/local/polkadot/target/release/polkadot --name NAME
Restart=on-failure
RestartSec=3
LimitNOFILE=4096

[Install]
WantedBy=multi-user.target
```

##Activamos el servicio en el arranque del sistema:

`sudo systemctl enable kusama.service`

##Iniciamos el servicio:

`sudo systemctl start kusama.service`

##Puedes comprobar que esta funcionando con:

`systemctl status kusama.service`

##Para ver los logs del nodo:

`journalctl -f -u kusama`

##Podemos crear un script para ver los logs del nodo:

`vim checkKusama`

>Dentro copiamos lo siguiente:

```
#!/bin/bash
#
#
sudo journalctl -f -u kusama.service
```

>Le damos permisos de ejecución:

`chmod +x checkKusama`

>Podemos ejecutarlo en una ventana de tmux para tenerlo visualizado:

`./checkKusama`

- En [esta](https://telemetry.polkadot.io/#list/Kusama%20CC1) web puedes comprobar algunas métricas.

- [Este](https://github.com/kusamanetwork) es el repositorio de Kusama.

- [Aquí](https://guide.kusama.network/en/latest/) puedes encontrar su documentación.