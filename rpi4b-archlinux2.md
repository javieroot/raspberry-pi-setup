Installation

Ubicar la unidad a formatear, se puede utilizar fdisk -l o lsblk

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
├─sda1   8:1    0   512M  0 part /boot/efi
├─sda2   8:2    0   100G  0 part /
├─sda3   8:3    0     4G  0 part [SWAP]
└─sda4   8:4    0   827G  0 part /home
sdb      8:16   1    29G  0 disk 
└─sdb1   8:17   1    29G  0 part /run/media/javier/4A1A-B4FD

En este caso la tarjeta de memoria es la unidad sdb


Replace sdX in the following instructions with the device name for the SD card as it appears on your computer.

    Start fdisk to partition the SD card:
    fdisk /dev/sdX
    En este caso sdb
    sudo fdisk /dev/sdb

    At the fdisk prompt, delete old partitions and create a new one:
        Type o. This will clear out any partitions on the drive.
        Type p to list partitions. There should be no partitions left.
        Type n, then p for primary, 1 for the first partition on the drive, press ENTER to accept the default first sector, then type +100M for the last sector.
        Type t, then c to set the first partition to type W95 FAT32 (LBA).
        Type n, then p for primary, 2 for the second partition on the drive, and then press ENTER twice to accept the default first and last sector.
        Write the partition table and exit by typing w.



[javier@modelos ~]$ sudo fdisk /dev/sdb
[sudo] password for javier: 

Bienvenido a fdisk (util-linux 2.34).
Los cambios solo permanecerán en la memoria, hasta que decida escribirlos.
Tenga cuidado antes de utilizar la orden de escritura.


Orden (m para obtener ayuda): o
Se ha creado una nueva etiqueta de disco DOS con el identificador de disco 0xb0028a69.

Orden (m para obtener ayuda): p
Disco /dev/sdb: 28.99 GiB, 31104958464 bytes, 60751872 sectores
Modelo de disco: Card  Reader    
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes
Tipo de etiqueta de disco: dos
Identificador del disco: 0xb0028a69

Orden (m para obtener ayuda): n
Tipo de partición
   p   primaria (0 primaria(s), 0 extendida(s), 4 libre(s))
   e   extendida (contenedor para particiones lógicas)
Seleccionar (valor predeterminado p): p
Número de partición (1-4, valor predeterminado 1): 1
Primer sector (2048-60751871, valor predeterminado 2048): 
Último sector, +/-sectores o +/-tamaño{K,M,G,T,P} (2048-60751871, valor predeterminado 60751871): +100M

Crea una nueva partición 1 de tipo 'Linux' y de tamaño 100 MiB.

Orden (m para obtener ayuda): t
Se ha seleccionado la partición 1
Código hexadecimal (escriba L para ver todos los códigos): c
Se ha cambiado el tipo de la partición 'Linux' a 'W95 FAT32 (LBA)'.

Orden (m para obtener ayuda): n
Tipo de partición
   p   primaria (1 primaria(s), 0 extendida(s), 3 libre(s))
   e   extendida (contenedor para particiones lógicas)
Seleccionar (valor predeterminado p): p
Número de partición (2-4, valor predeterminado 2): 2
Primer sector (206848-60751871, valor predeterminado 206848): 
Último sector, +/-sectores o +/-tamaño{K,M,G,T,P} (206848-60751871, valor predeterminado 60751871): 

Crea una nueva partición 2 de tipo 'Linux' y de tamaño 28.9 GiB.

Orden (m para obtener ayuda): w
Se ha modificado la tabla de particiones.
Se están sincronizando los discos.

[javier@modelos ~]$ 
[javier@modelos ~]$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
├─sda1   8:1    0   512M  0 part /boot/efi
├─sda2   8:2    0   100G  0 part /
├─sda3   8:3    0     4G  0 part [SWAP]
└─sda4   8:4    0   827G  0 part /home
sdb      8:16   1    29G  0 disk 
└─sdb1   8:17   1    29G  0 part /run/media/javier/4A1A-B4FD
[javier@modelos ~]$ sudo fdisk -l
Disco /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectores
Modelo de disco: TOSHIBA MQ04ABF1
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 4096 bytes
Tamaño de E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Tipo de etiqueta de disco: gpt
Identificador del disco: C9445EE2-66E4-47F1-A290-2F722817E6B6

Disposit.   Comienzo      Final   Sectores Tamaño Tipo
/dev/sda1       2048    1050623    1048576   512M Sistema EFI
/dev/sda2    1050624  210765823  209715200   100G Sistema de ficheros de Linux
/dev/sda3  210765824  219154431    8388608     4G Linux swap
/dev/sda4  219154432 1953525134 1734370703   827G Sistema de ficheros de Linux


Disco /dev/sdb: 28.99 GiB, 31104958464 bytes, 60751872 sectores
Modelo de disco: Card  Reader    
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 512 bytes
Tamaño de E/S (mínimo/óptimo): 512 bytes / 512 bytes
Tipo de etiqueta de disco: dos
Identificador del disco: 0xb0028a69

Disposit.  Inicio Comienzo    Final Sectores Tamaño Id Tipo
/dev/sdb1             2048   206847   204800   100M  c W95 FAT32 (LBA)
/dev/sdb2           206848 60751871 60545024  28.9G 83 Linux



Para que se vean las partiviones creadas con lsblk es necesario extraer la memoria e insertarla nuevamente
[javier@modelos ~]$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
├─sda1   8:1    0   512M  0 part /boot/efi
├─sda2   8:2    0   100G  0 part /
├─sda3   8:3    0     4G  0 part [SWAP]
└─sda4   8:4    0   827G  0 part /home
sdb      8:16   1    29G  0 disk 
├─sdb1   8:17   1   100M  0 part 
└─sdb2   8:18   1  28.9G  0 part 







    Create and mount the FAT filesystem:

    mkfs.vfat /dev/sdX1 (sudo mkfs.vfat /dev/sdb1)
    mkdir boot
    mount /dev/sdX1 boot (sudo mount /dev/sdb1 boot)

    Create and mount the ext4 filesystem:

    mkfs.ext4 /dev/sdX2  (sudo mkfs.ext4 /dev/sdb2)
    mkdir root
    mount /dev/sdX2 root (sudo mount /dev/sdb2 root)

    Download and extract the root filesystem (as root, not via sudo):

    wget http://os.archlinuxarm.org/os/ArchLinuxARM-rpi-4-latest.tar.gz
    bsdtar -xpf ArchLinuxARM-rpi-4-latest.tar.gz -C root
    sync

    Move boot files to the first partition:

    mv root/boot/* boot (sudo mv root/boot/* boot)

    Unmount the two partitions:

    umount boot root (sudo umount boot root)

    Insert the SD card into the Raspberry Pi, connect ethernet, and apply 5V power.
    Use the serial console or SSH to the IP address given to the board by your router.
        Login as the default user alarm with the password alarm.
        The default root password is root.
    Initialize the pacman keyring and populate the Arch Linux ARM package signing keys:

    pacman-key --init
    pacman-key --populate archlinuxarm


