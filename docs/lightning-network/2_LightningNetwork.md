# __[Lightning Network](https://lightning.network/): la capa de _Cash_ sobre Bitcoin__

__LN__ es la primera implementación de __Segwit__, que ha llevado más de 3 años _(un poco como el huevo y la gallina)_ en el que han participado no solo la Start-Up que la pensó llamada ___Lightning Labs___. Sino muchas otras empresas. _Como dato curioso, se creó un consorcio temporal a principios de año entre los departamentos de calculo computacional de las 70 universidades más potentes del mundo con la intención de valorar la viabilidad del proyecto._

El funcionamiento es el siguiente: utilizando el espacio, del campo de notas, que nos da __SegWit__, abrímos una transacción y metemos un trozo de Smart contract. En un bloque futuro cerraremos la transacción con el resto del Smart contract. Eso significa que gastaremos el doble en tasas para realizar una transacción. Lógicamente esto solo es perder dinero y encima de manera más complicada.

La primera utilidad viene porque: entre uno y otro paso, podremos hacer múltiples transacciones, en una u otra dirección, en lugar de realizar una transacción única. _Por ejemplo imaginemos un contrato dónde se paga por comisión y se cobra algún tipo de material gastado durante el proceso. Se abriría un canal por ejemplo de 1000 € y cada vez que se cumplirá el objetivo se traspasaría el beneficio directamente y cada vez que se rompiera una herramienta por ejemplo se cobraría en la dirección contraria la cantidad de la reparación. Al terminar un periodo se cerraría el contrato quedando ajustado al final la cantidad exacta que se ha traspasado de una dirección a la otra y eliminando todas las transacciones intermedias que no son necesarias para terceros._

La utilidad real, viene dada, por el enrutamiento de todos los canales entre sí. De esta forma, al crear un canal entre dos personas, no solo pueden transmitir dinero entre ellas, sino entre las comunidades que ambas personas tienen detrás. Además el dinero no tiene que ir por un solo camino, de manera que si el canal no permite transmitirlo todo, se dividirá y parte recorrerá caminos más largos para transmitirlo completamente.

Todo el dinero que pase por un canal que tú has creado te da unas tasas por hacerlo. De esta forma, se están creando núcleos que están muy bien conectados y qué esperan cobrar un buen dinero en tasas, de una manera similar a como ocurre con las empresas de minería. Sin embargo, en este caso, no estamos hablando de la necesidad de comprar equipo o gastar electricidad, pues solo es necesario tener cantidades congeladas haciendo ___stake___ en forma de canales.

Como creador de un canal: aseguras que como máximo moverás esa cantidad de dinero que tienes en ___stake___, a la cual se le deben restar la apertura y cierre del __State Channel__. En caso de que hagas algo malicioso, es ese dinero el que responderá en tu lugar.

Son los mineros de la Capa 1, es decir de __Bitcoin__, los que aseguran mediante __Proof of Work__ la apertura y cierre de canal.

Esto significa que tenemos una capa 1 con una seguridad desproporcionada y una capa 2 con una seguridad completamente disgregada y asegurada. No hay necesidad de montar capas de proof of work encima o detener nuevos dispositivos haciendo caros procesos.

Lightning es permissionless:
- No se necesita pedir por una cuenta
- No pueden cerrarte la encuentra
- No hay cierra ningún días
- Ni tiene limitaciones geográficas

Aún así, correr un nodo público de Lightning Network tiene requisitos:
- __High Uptime:__ se requiere estar online para poder enrutar los pagos
- __Hot Wallet:__ necesitaremos tener la clave secreta en dicho dispositivo para firmar
- __Continuous Backups:__ si perdemos la BD de tx, perdemos los fondos

