# Preparación del equipo para ver la documentación.

En [su página oficial](https://www.mkdocs.org/#installation) podéis encontrar más información acerca de la instalación en varias plataformas, en este caso lo explicaremos para [Ubuntu 18.04LTS](https://ubuntu.com).

## Instalación con [APT](https://es.wikipedia.org/wiki/Advanced_Packaging_Tool).
`sudo apt install -y mkdocs` 

## Instalación con [PIP](https://pypi.org/project/pip/).
`pip install mkdocs --user`

#### Apunte:

La versión de pip debe ser la más actual, la 19.2.1. Si no `pip install mkdocs` no funcionará correctamente.
Cuando instalamos pip en Ubuntu 18.04+ hay que tener en cuenta que lo ideal es seguir la guía oficial, https://pip.pypa.io/en/stable/installing/, descargando `get-pip.py` y luego con el comando `python get-pip.py --user`.

Instalando pip con `sudo apt install python-pip` podemos tener problemas a la hora de hacer upgrade (`sudo pip install pip --upgrade`).

Comprobamos la instalación con `pip --version`. Si no encuentra el PATH lo más probable es que el ejecutable de pip se encuentre en `$HOME/.local/bin`. Lo añadimos a nuestros PATHs en `~/.profile` agregando la línea: `export PATH=$PATH:/$HOME/.local/bin`. Guardamos el archivo y ejecutamos `source ~/.profile`.
Comprobamos la instalación con `pip --version`.

Ahora ya deberíamos tener la versión más actual de pip instalada. 

## Comprobamos la versión instalada:
`mkdocs --version`

>mkdocs, version 1.0.4

## En este caso usamos la versión ReadTheDocs [Dropdown](https://github.com/cjsheets/mkdocs-rtd-dropdown), la instalamos:
`pip install mkdocs-rtd-dropdown --user`

## Instalamos dependencias:
`pip install md-tooltips --user`

## Clonamos el repositorio:
`git clone https://github.com/Colm3na/DocsColmena.git`

## Nos dirigimos a la carpeta del proyecto, e iniciamos el servidor de desarrollo:
`cd $HOME/DocsColmena/` 

`mkdocs serve`

> Si abrimos el navegador y nos vamos a la página [http://127.0.0.1:8000/](http://127.0.0.1:8000/) podemos ver la documentación.
