# raspberry-pi-setup


## INTRODUCCIÓN
--------------------------------------------------------------------------------

### ¿Que es la Raspberry PI?
La Raspberry Pi es una microcomputadora desarrollada inicialmente para fines 
educativos. Las versatilidad que tiene han llevado a desarrollar todo tipo de 
aplicaciones, en muchos ámbitos. Nosotros no nos vamos a centrar aquí en ninguna.

### ¿Para que puedo usarla?

    * Mediacenter
    * Centro de juegos
    * Filtro DNS
    * Servicio de Streaming DLNA
    * Servidor descargas
    * Servidor NAS
    * Escritorio básico

### Versiones

    * Raspberry pi A
    * Raspberry pi B
    * Raspberry pi B+
    * Raspberry pi 2 B
    * Raspberry pi 3 B
    * Raspberry pi 3 B+
    * Raspberry pi 3 A+
    * Raspberry pi 4 B
    * Raspberry pi Zero
    * Raspberry pi Zero W
    * Raspberry pi Zero WH

[Wikipedia](https://es.wikipedia.org/wiki/Raspberry_Pi)

Las novedades más destacables en la PI4 son: socket mejorado Cortex-A72, varias 
configuraciones de RAM, posibilidad de decodificar 4k@60fps, dos puertos USB 3.0,
y Bluetooth 5.0, Wi-Fi 802.11ac, Gigabit Ethernet.

### Especificaciones
Solo pongo de momento los de la Pi4 B:

    * SoC Broadcom BCM2711 (CPU + GPU + DSP + SDRAM + Puerto USB)
    * CPU 1.5GHz 64-bit quad-core Cortex-A72
    * GPU Broadcom VideoCore VI, OpenGL ES 3.0, 1080p30 H.264/MPEG-4 AVC, 4kp60 H.265
    * 1 GB, 2 GB o 4 GB (compartidos con la GPU)
    * USB 2.0 2 puertos
    * USB 3.0 2 puertos
    * Entradas de video Conector MIPI CSI que permite instalar un módulo de cámara desarrollado por la RPF
    * Salidas de video Conector RCA (PAL y NTSC), microHDMI rev. 2.0, Interfaz DSI para panel LCD
    * Salidas de audio Jack de 3.5 mm, 2 puertos microHDMI
    * Almacenamiento MicroSD
    * Conectividad Bluetooth 5.0, Wi-Fi 802.11ac, Gigabit Ethernet.
    * Periféricos de bajo nivel 17 x GPIO y un bus HAT ID
    * Consumo Máximo 3A (15.3 W)
    * Alimentación 5 V vía USB-C o puerto GPIO
    * Dimensiones 85.60mm × 53.98mm

### Sistemas operativos
Los sistemas operativos desarrollados para la placa son muchos también, por lo 
que debemos centrarnos en los que nos permitan llevar a cabo los propósitos que 
queremos. Todos los que vamos a utilizar están basados en sistemas Linux.

    * Raspbian
    * Libreelec
    * OSMC
    * Recalbox

### Interfaces de la placa
### Accesorios imprescindibles y opcionales

### Tarjeta microSD
Una de las partes más importantes es la tarjeta SD, de su compatibilidad y velocidad 
de lectura va a depender que nos vaya mejor o peor la raspberry. Lo que suelen 
decir y para mi gusto las mejores son las Sandisk. La Sandisk Ultra 64gb suele 
rondar los 25€, pero he visto ofertas por bastante menos. La capacidad mínima que 
recomiendo son 32gb, ya que las imágenes suelen ser de 7-8 gb, más luego necesitas 
un buffer para el streaming, que no debe ser justo, o irá bastante mal. Importante
fijarse en la velocidad de trasferencia (hay tarjetas que parecen iguales y una 
tiene más que la otra), recomendado 100mb/s.


#### Listado de compatibilidad
* Sandisk Ultra en Amazon (me parece la mejor en compatibilidad y precio)
* Sandisk Ultra Tipo A1 (algo más rápidas)

### Adaptador de corriente
La raspberry necesita un amperaje mínimo para funcionar correctamente. Se necesita 
un adaptador de corriente continua de 3A. Si puede ser con interruptor mejor. Su 
coste es 10€ más o menos. No recomiendo comprar uno malo de china, suelen 
estropearse rápido.


Cargador de corriente Amazon con interruptor

### Cable HDMI
Cualquier cable HDMI con un mínimo de calidad. De 6 a 7€
Amazon HDMI

### Cajas raspberry (muy personal) 
lo ideal es una caja o bien que permita poner un ventilador para sacar el aire 
caliente de la pi, o bien uno de aluminio que haga contacto con los integrados y 
les disipe calor.

* Disipadores,si no hace contacto con la caja.

* Teclado retroiluminado(muy útil para búsquedas, si lleva batería mejor)

GRABAR UNA IMAGEN PRECONFIGURADA

Para grabar una imagen necesitaremos un software cómo el Win32diskimager.

Los pasos son los siguientes:
1) Insertamos la MicroSD en un lector de tarjetas.
2) Ejecutamos Win32diskimager y seleccionamos la imagen dándole al icono de la carpeta.
3) Seleccionamos la letra de Unidad en Device que el sistema ha asignado a la MicroSD
4) Le damos a write y nos grabará la imagen.
5) Introduce tu microSD con la imagen grabada en tu Raspberry
6) Enchufa el cable de alimentación
7) La Raspberry se encenderá, aparecerá la imágen inicial de garlic-dog
8) La Raspberry se reiniciará automáticamente, volverás a ver la imagen inicial de garlic-dog
9) El mediacenter Kodi arrancará automáticamente
10) Pulsamos el botón situado en la esquina inferior izquierda, seleccionamos salir para cerrar Kodi
11) Verificar que la partición ocupa el 100% de tu microSD con el comando df -h (opcional)
CONECTAR POR SSH A LA RASPBERRY

Para realizar esto, la imagen debe tener la consola SSH activada por defecto, y 
nosotros usar un software SSH desde el PC remoto o el móvil, mi recomendación 
para pc es el PuTTy, y para Android el JuiceSSH: 
