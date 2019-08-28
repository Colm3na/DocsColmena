<h1 align="center">Brave</h1>

<p align="center"> 
<img src="/images/brave/braveSvQ.png">
</p>

> En este repositorio puedes encontrar documentación y pasos para darse de alta en la plataforma de [Brave](https://brave.com) para [publishers](https://publishers.basicattentiontoken.org).

> Es necesario que nuestra web tenga un certificado HTTPS, si necesitas incorporarlo puedes seguir [estos pasos](https://github.com/Colm3na/Brave/blob/wimelTest/Certificado_HTTPS.md)

<h1 align="center">Empezando con Brave publishers:</h1>

### Necesitamos crear una cuenta en [Uphold](https://uphold.com/) para gestionar los pagos y nuestros fondos de una manera más sencilla, estos son los pasos a seguir:

1. Nos dirigimos a [Uphold](https://uphold.com) y hacemos clic en _“Sign up”_.

![uphold1](/images/brave/inst1.png)

2. Rellenamos nuestros datos, email, contraseña, país de residencia etc, y hacemos clic en _“CONTINUAR”_ **_(como nos indican, tiene que ser una contraseña segura)_**

![uphold2](/images/brave/inst2.png)

3. Completamos la información personal y hacemos clic en _“CONTINUAR”_

![uphold3](/images/brave/inst3.png)

4. Nos mandan un correo de confirmación al email introducido anteriormente.

<p align="center"> 
<img src="/images/brave/inst4.png">
</p>

5. Hacemos clic en el link que nos han enviado a nuestro mail.

![uphold5](/images/brave/inst5.png)

6. Iniciamos sesión en Uphold, escribimos nuestro número de teléfono para darle más seguridad a nuestra cuenta usando [Authy](https://authy.com), y hacemos clic en _“ENVIAR CÓDIGO”_. 

![uphold6](/images/brave/inst6.png)

7. Nos mandarán un mensaje al móvil indicado anteriormente con un enlace al [Appstore](https://itunes.apple.com/us/app/authy/id494168017) (IOS) o [Google Play](https://play.google.com/store/apps/details?id=com.authy.authy) (Android).

<p align="center"> 
<img src="/images/brave/inst7.jpg">
</p>

8. Instalamos la app de [Authy](https://authy.com/download/), y vamos siguiendo los pasos que nos indican.

<p align="center"> 
<img src="/images/brave/gif1.gif">
</p>

9. El siguiente paso es darnos de alta en Brave como creadores de contenido. Para ello nos dirigimos a [Brave-creators](https://brave.com/creators/) y hacemos clic en _“Become a Creator”_

![brave-creator](/images/brave/inst7.png)

10. En la siguiente ventana que nos aparece hacemos clic en _“GET STARTED”_

![brave-creator](/images/brave/inst8.png)

11. Introducimos nuestro email y hacemos clic en _“Get Started”_

<p align="center"> 
<img src="/images/brave/inst9.png">
</p>

12. Recibiremos un email con un enlace, hacemos clic en él.

<p align="center"> 
<img src="/images/brave/inst10.png">
</p>

13. Rellenamos los datos y hacemos clic en _“Sign Up”_

<p align="center"> 
<img src="/images/brave/inst11.png">
</p>

14. En caso de tener alguna aplicación para el segundo factor, en este paso podemos configurarlo. Para esta guía vamos a omitirlo (si necesitáis una guía de configuración de segundo factor dejadlo en los comentarios), hacemos clic en _“Skip for now”_

<p align="center"> 
<img src="/images/brave/inst12.png">
</p>

15. Una vez realizados estos pasos podemos ver nuestra página principal de [Brave Creators](https://brave.com/creators/)

<p align="center"> 
<img src="/images/brave/inst13.png">
</p>

16. Ahora vamos a añadir nuestro sitio web y a generar el token necesario para verificarlo. Para ello, hacemos clic en _“Add Channel”_

![brave-creator](/images/brave/inst14.png)

17. Elegimos qué queremos dar de alta, en mi caso _“WEBSITE”_

<p align="center"> 
<img src="/images/brave/inst15.png">
</p>

18. Introducimos nuestra web en el recuadro (para el ejemplo, vamos a proceder a dar de alta la web de la [Colmena](https://www.coworkingcolmena.com/)) y hacemos clic en _“Continue”_

![brave-creator](/images/brave/inst16.png)

19. En el siguiente paso nos muestra dos opciones para verificar nuestra página web, en mi caso voy a elegir  _“I’ll use a trusted file”_

<p align="center"> 
<img src="/images/brave/inst17.png">
</p>

20. Una vez que hemos hecho clic, nos muestra un archivo que debemos guardar con el token necesario para enlazar nuestra web con Brave (no debemos modificar ni el nombre ni el contenido de ese archivo). Para ello hacemos clic en _“Download”_.

> Dejamos esta ventana abierta para la verificación posterior.

![brave-creator](/images/brave/inst18.png)

## Tenemos dos opciones para introducir este archivo en nuestra web: [desde la terminal](https://github.com/Colm3na/Brave/tree/wimelTest#desde-la-terminal) o instalando el [complemento de wordpress](https://github.com/Colm3na/Brave/tree/wimelTest#desde-el-complemento-de-wordpress).

## Desde la terminal:

1. Nos dirigimos donde tengamos nuestra web situada (en mi caso `/var/www/html/`)

`cd /var/www/html`

<p align="center"> 
<img src="/images/brave/inst19.png">
</p>

2. Creamos una carpeta llamada “.well-known”

`mkdir .well-known`

<p align="center"> 
<img src="/images/brave/inst20.png">
</p>

3. Entramos en la carpeta, creamos el archivo y copiamos en el interior el contenido del archivo descargado anteriormente, guardamos y salimos.

`nano brave-rewards-verification.txt`

![brave-creator](/images/brave/inst21.png)

## Desde el complemento de wordpress

### El plugin de wordpress creará por nosotros el fichero sin necesidad de hacerlo manualmente.

1. Descargar el [plugin](https://wordpress.org/plugins/brave-payments-verification/)

2. Instalarlo en `/wp-content/plugins/` 

3. Ir a _Settings_ > _Brave Payments Verification_ y añadir el token obtenido del fichero de verificación y hacer click en _Save Changes_

> **Nota:** Una vez hayamos recibido confirmación por email de que el sitio está verificado, podemos desactivar este plugin.

## Una vez que hemos realizado los pasos anteriores vamos a proceder a verificar nuestra web

1. Nos dirigimos a la página anterior y hacemos clic en _“Verify”_

<p align="center"> 
<img src="/images/brave/inst22.png">
</p>

_**Con estos pasos ya tenemos nuestra web de alta en Brave Creators; si nos dirigimos a nuestra página principal en Brave Rewards podemos ver que nos aparece nuestra web.**_

![brave-creator](/images/brave/inst23.png)
