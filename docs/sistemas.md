# Sistemas

# LVM.

## Gestión de disco

>Ampliar el espacio de disco de nuestras máquinas virtuales.

## Paso 1:

Añadimos la unidad en nuestro sistema. Si usamos KVM Libvirt abrimos nuestro Virt-Manager, arrancamos nuestra máquina virtual, pulsamos añadir hardware (*add hardware*): 
![alt text](images/addhardware.jpg?raw=true "Añadir hardware a la máquina virtual")

Elegimos la primera opción, almacenamiento (*storage*), seleccionamos almacenamiento personalizado (*custom storage*):
![alt text](images/customstorage.jpg?raw=true "Añadir hardware a la máquina virtual")

Elegimos nuestro *pool* (directorio) de almacenamiento y creamos un nuevo qcow2 con el tamaño deseado.
![alt text](images/createpool.jpg?raw=true "Añadir hardware a la máquina virtual")

## Paso 2:

Entramos en nuestra máquina virtual. Si ejecutamos el comando:
`lsblk`

>Veremos algo de este estilo:

<pre>
NAME                    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0                      11:0    1   761M  0 rom  
vda                     254:0    0   100G  0 disk 
├─vda1                  254:1    0   243M  0 part /boot
├─vda2                  254:2    0     1K  0 part 
└─vda5                  254:5    0  99,8G  0 part 
  ├─dappnode--vg-root   253:0    0 179,8G  0 lvm  /
  └─dappnode--vg-swap_1 253:1    0    20G  0 lvm  [SWAP]
vdb                     254:16   0   100G  0 disk 
└─vdb1                  254:17   0   100G  0 part 
  └─dappnode--vg-root   253:0    0 179,8G  0 lvm  /
vdc                     254:32   0   100G  0 disk
</pre>

>En este caso el nuevo dispositivo de bloques aparece nombrado como `vdc` y tiene un tamaño de 100G

> Para poder añadirlo a nuestro sistema de ficheros primero tendremos que crear una partición y darle formato. En nuestro caso el formato elegido es `ext4`

Lo anterior lo hacemos con `fdisk`.

`fdisk /dev/vdc`

- Pulsamos `"n"` para crear una nueva partición. Aceptamos las opciones por defecto.
- Pulsamos `"w"` para guardar los cambios y salir.

>Si volvemos a mostrar los dispositivos de bloque veremos algo así:

<pre>
NAME                    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0                      11:0    1   761M  0 rom
vda                     254:0    0   100G  0 disk
├─vda1                  254:1    0   243M  0 part /boot
├─vda2                  254:2    0     1K  0 part
└─vda5                  254:5    0  99,8G  0 part
  ├─dappnode--vg-root   253:0    0 179,8G  0 lvm  /
  └─dappnode--vg-swap_1 253:1    0    20G  0 lvm  [SWAP]
vdb                     254:16   0   100G  0 disk
└─vdb1                  254:17   0   100G  0 part
  └─dappnode--vg-root   253:0    0 179,8G  0 lvm  /
vdc                     254:32   0   100G  0 disk
└─vdc1                  254:33   0   100G  0 part
</pre>

## Paso 3:

- Ahora queremos añadir el nuevo dispositivo de bloque a nuestro grupo de volumenes. Vamos a mostrar el estado actual:

`pvdisplay` 

<pre>

  --- Physical volume ---
  PV Name               /dev/vda5
  VG Name               dappnode-vg
  PV Size               <99,76 GiB / not usable 0   
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              25538
  Free PE               0
  Allocated PE          25538
  PV UUID               3rIpft-Hu1d-0Tl0-niKA-vPWW-OrY9-QxJBBw
</pre>

>Tenemos un dispositivo físico con nombre /dev/vda5 que pertenece al grupo de volumenes "dappnode-vg".

- Vamos a añadir un nuevo dispositivo físico para después añadirlo al grupo de volumenes:

<pre>
pvcreate /dev/vdc1
  Physical volume "/dev/vdc1" successfully created
</pre>

- Y acto seguido lo añadimos al grupo de volumenes:

<pre>
vgextend dappnode-vg /dev/vdc1
  Volume group "dappnode-vg" successfully extended
</pre>

- Mostramos el estado:

`pvdisplay`
<pre> 
  --- Physical volume ---
  PV Name               /dev/vda5
  VG Name               dappnode-vg
  PV Size               <99,76 GiB / not usable 0   
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              25538
  Free PE               0
  Allocated PE          25538
  PV UUID               3rIpft-Hu1d-0Tl0-niKA-vPWW-OrY9-QxJBBw
   
  --- Physical volume ---
  PV Name               /dev/vdb1
  VG Name               dappnode-vg
  PV Size               <100,00 GiB / not usable 3,00 MiB
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              25599
  Free PE               0
  Allocated PE          25599
  PV UUID               WajnVa-1CWp-HJWF-0ghS-vwx4-cm0g-IPby0Q
</pre>

## Paso 4:

Extendemos el volumen lógico:

`lvextend -l 100%FREE /dev/dappnode-vg/root`

<pre>
Rounding up size to full physical extent 100.00 GiB
  Extending logical volume storage to 100.00 GiB
  Logical volume storage successfully resized
</pre>

## Paso 5:

Por último redimensionamos el sistema de archivos para que nuestro Linux sea consciente de que ahora tiene más espacio en la partición raíz.


`resize2fs /dev/dappnode-vg/root`

Si mostramos ahora nuestro espacio disponible veremos que la partición raiz ha aumentado:

<pre>
df -h
S.ficheros                    Tamaño Usados  Disp Uso% Montado en
udev                            9,8G      0  9,8G   0% /dev
tmpfs                           2,0G    18M  2,0G   1% /run
/dev/mapper/dappnode--vg-root   177G    72G   98G  43% /
</pre>

# Nagios.

## Instalar paquetes:
`sudo apt install nagios-nrpe-server nagios-plugins`

## Modificar regla de acceso:

`sudo vim /etc/nagios/nrpe.cfg`

## Buscamos la línea
`allowed_hosts=127.0.0.1`


## Y la cambiamos por:
`allowed_hosts=127.0.0.1,[IP del NAGIOS]`

## Añadimos definiciones de chequeos personalizados
`vim /etc/nagios/nrpe_local.cfg`

## Lista de chequeos personalizados:

>**Ojo**, en el primer chequeo que viene ahora hay que modificar `/dev/vda1` por el dispositivo de tu servidor.
Puedes ver la lista de dispositivos de disco con el comando `lsblk` 

`command[check_root]=/usr/lib/nagios/plugins/check_disk -w 20% -c 10% -p /dev/vda1`

`command[check_peers]=/usr/lib/nagios/plugins/check_peers`

`command[check_load]=/usr/lib/nagios/plugins/check_load -r -w .70,.70,.70 -c .90,.80,.70`

`command[check_mem]=/usr/lib/nagios/plugins/check_mem -w 80 -c 90`

## Subimos nuestros scripts de checkeos, puedes encontrarlos en la carpeta `scriptsNagios`
`scp check_root [user]@[ip]:/tmp`

`scp check_peers [user]@[ip]:/tmp`

`scp check_mem [user]@[ip]:/tmp`

## Y luego desde dentro de la máquina los copiamos a su destino
`cp /tmp/check_* /usr/lib/nagios/plugins/`

## Paramos y arrancamos el servicio nagios-nrpe-server
`/etc/init.d/nagios-nrpe-server stop`

`/etc/init.d/nagios-nrpe-server start`