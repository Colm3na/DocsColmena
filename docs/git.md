# Primeros pasos con git

Git es un software para el control de versiones, su función es llevar un registro de las modificaciones y organizar el trabajo de varias personas desde varios dispositivos en un mismo proyecto.

> _Una cosa es Github y otra Git, Githab es una interface grafica para gestionar los repositorios, pero tambien existen otras interfaces como [Gitlab.](https://gitlab.com)_

[Aquí](https://git-scm.com) puedes encontrar más información de git.

Vamos a explicar algunos pasos _"básicos"_ para la gestion de git desde la terminal.

**En esta guía explicaremos:**

- [git clone](https://git-scm.com/docs/git-clone): Para clonar repositorios en nuestra máquina.

- [git pull](https://git-scm.com/docs/git-pull): Para actualizar el repositorio en nuestra máquina.

- [git checkout](https://git-scm.com/docs/git-checkout): Para usar una rama o una version específica.

- [git commit](https://git-scm.com/docs/git-commit): Para poner comentarios.

- [git push](https://git-scm.com/docs/git-push): Para subir nuestros cambios.

> Usaremos el repositorio de la documentación de la Colmena como ejemplo.

**El primer paso es instalar git**

`sudo apt install git -y`

## git clone

* Nos dirigimos al repositorio que queramos clonar, podemos ver que a la derecha hay un botón verde que es un desplegable. Hacemos clic y copiamos la url del repositorio.

![gitClone](/images/git/git1.png)

* En nuestra terminal clonamos el repositorio con:

`git clone https://github.com/Colm3na/DocsColmena.git`

![gitClone](/images/git/git2.png)

* Entramos en la carpeta del repositorio clonado:

`cd DocsColmena/`

![entramosEnCarpeta](/images/git/git3.png)

* Una vez que hemos clonado el repositorio, creamos una rama _(podemos ponerle el nombre que queramos)_ y trabajamos en ella:

`git checkout -b demo`

![gitcheckout](/images/git/git4.png)

> Como podemos observar hemos creado una rama llamada `demo` y nos hemos pasado a ella.

> Ahora podemos hacer los cambios que queramos en los archivos, modificar o añadir lo que necesitemos, para el ejemplo hemos modificado el README.md.

![gitmod](/images/git/git5.png)

* Lo siguiente es guardar los cambios que hemos hecho en git, ahora mismo los cambios solo estan en nuestra maquina, pero la idea es que git guarde el registro de lo que hemos ido haciendo _(importante poner el punto después de `git add` para que nos guarde todo los cambios)_:

`git add .`

![gitadd](/images/git/git6.png)

* Ponemos un comentario y hacemos el commit _(entre las comillas ponemos el comentario que queramos)_:

`git commit -m "primer commit"`

![gitcommit](/images/git/git7.png)

> Hasta ahora lo que hemos hecho es, descargar el repositorio, crear una rama nueva donde hacer las modificaciones, guardar los cambios y hacer un commit con los cambios realizados.

* Subimos los cambios a nuestro Github o Gitlab, nos preguntará nuestra contraseña y usuario `demo`es el nombre de nuestra rama _(recordar que Github y Gitlab son interfaces graficas, los comandos funcionarian igual para cualquier interface)_

`git push --set-upstream origin demo`

![gitpush](/images/git/git8.png)

> Para facilitar el siguiente paso, vamos a hacer el Pull Request desde la interface de Github.

* Si abrimos Github con nuestra cuenta en el repositorio que estemos podemos apreciar que hay una rama más en `branches`, y nos sale un boton que dice `Compare & pull request`:

![gitpr](/images/git/git9.png)

>En la siguiente ventana podemos aclarar los cambios que hemos hecho poniendo comentarios o alguna aclaración y hacemos clic en `Create pull request`.

* Comprobamos que nuestros cambios no tienen conflictos con el repositorio en el que estamos trabajando:

![gitpr3](/images/git/git10.png)

Pues ya sólo nos queda que acepten nuestro Pull Request, espero que esta guía básica les sirva de ayuda.