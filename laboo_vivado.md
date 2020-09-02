### Descargar instalador
## Instalación de Vivado
Primero es necesario que descarguen el archivo .tar que usaran para realizar la instalacion.

[Descarga](https://www.xilinx.com/support/download.html)

Escogen el paquete que es para todos los sistemass operativos
![Download](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/Imagen2.png)

Para poder descargar el archivo el sistema les pedira que creen una cuenta
![sigin](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/Imagen1.png)

luego de descargar el archivo deben abrirlo, les paarecera la sigueinte ventana
![instlacion1](https://github.com/unal-edigital1-2020-1/page/tree/master/labs/figs/Imagen3.png)

Ingresan su usuario y contraseña, activan ***Download and Install Now***
![instalacion2](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/Imagen4.png)

Activan las 3 casillas como muestra en la imagen y le dan Next
![instalacion3](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/Imagen5.png)

Activan la casilla ***Vivado*** y le dan Next
![instalacion4](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/Imagen6.png)

Seleccionan la casilla ***Vivado HL WebPACK***
![instalacion5](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/Imagen7.png)

En esta ventana solo deben dejar las casillas seleccionadas como se muestra en la siguiente imagen
![instalacion6](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/Imagen8.png)

Cuando les pida crear la carpeta donde guardar los proyectos darle ***Yes*** (recuerden dicha caroeta, ya qu ela vamos a necesitar mas adelante)
![instalacion6](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/Imagen10.png)

por ultimo es darle en ***Install*** y esperar que el programa se instale
![instalacion6](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/Imagen11.png)


## Configuración básica para un nuevo proyecto en Vivado
### Creacion de un nuevo proyecto
Al abrir el software ***vivado 2019.2*** aparecera la siguiente ventana, dele click a ***Create Project*** 
![project1](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/image13.jpg)

Darle ***Next*** 
![project2](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/image14.jpg)

En este punto definimos el nombre del proyecto y su ubicacion, es importante tener presente donde se va a guardar el proyecto. Dale ***Next***
![project3](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/imagen15.jpg)

En esta ventana vamos a escoger la opcion ***RTL Project*** y luego ***Next***
![project4](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/imagen16.jpg)

En esta ventana vamos a crear el script donde vamos a agregar el codigo de nuestro proyecto.  Es darle en ***Create File***
![project5](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/imagen17.jpg)


Y darle un nombre al script donde vamos a describir el hardware de la FPGA. Este nombre no puede contener espacios: 
![project6](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/imagen18.jpg)


En esta ventana vamos a especificarle que clase de FPGA vamos a usar en el proyecto. Para las practicas de este semestre vamos a usar una ***Nexys 4***, esta tarjeta de desarrollo tiene una FPGA de referencia ***xc7a100tcsg324-1***, para poder encontrarla en el catalogo se recomienda colocar los filtros como estan en la parte superior de la siguiente imagen. 
![project7](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/imagen19.jpg)

Por ultimo el sistema te va a dar un resumen de como va a crear el proyecto.
![project8](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/imagen20.jpg)

Esta entana te va a preguntar si deseas agregar las variables de entrada y salida del proyecto desde aqui, se pueden agregar en el listado o ingresar en el codigo
![project9](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/imagen21.jpg)

Despues de creado el proyecto apareceran varias ventanas, la ventana ***Source*** es la que tiene las carpetas del proyecto. En nuestro caso dicha carpeta tiene el nombre de ***Main.v***
![project10](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/image22.jpg)

Le damos doble click en el archivo del proyecto y nos habre el script para poder trabajar en el e iniciar nuestro proyecto.
![project11](https://github.com/unal-edigital1-2020-1/page/blob/master/labs/figs/image23.jpg)

