# lab00

Field Programmable Gate Array (FPGA) son dispositivos reconfigurables, en los cuales se puede implementar cualquier lógica combinacional o secuencia, en generial un amplio abanico de funciones electronicas. Esto es gracias a que las FPGAS son dispositivos que  integran bloques lógicos y que se pueden interconectar según la funcional deseada escrita en el Lenguaje de descripción de hardware (HDL).

Para obtener mas información, se recomienda leer [FPGAs For Dummies eBook](https://www.intel.com/content/dam/www/programmable/us/en/pdfs/literature/misc/FPGAs_For_Dummies_eBook.pdf)


# Configuración Framework para FPGA

Para general el bitstream, archivo que contiene la información de programación de la FPGA, los fabricantes de FPGAS ofrencen las herramientas de desarrollo propias, como Intel, Xilinx, Lattice, etc.,  que facilitan la integración del sistema hardware con el HDL.
Por ellos, y acorde con la tecnología de trabajo se recomienda instalar las herramientas IDE y de sintetización, según gustos  y tecnología. en este sentido el primer paso en este laboratorio es descargar las herramientas de diseño de hardware.

## Herramientas de Sintetización


* [instalación ISE](https://github.com/Fabeltranm/SPARTAN6-ATMEGA-MAX5864/wiki/Instalaci%C3%B3n-y-Configuraci%C3%B3n#instalaci%C3%B3n-de-isewebpack) Descontinuado 
* [Vivado](https://www.xilinx.com/products/design-tools/vivado.html)
* [yosys](http://www.clifford.at/yosys/) Open
* [migen](https://github.com/Fabeltranm/lm32_SoC/wiki/Instalación-y-configuración-de-las-herramientas-Litex-y-migen)
* Quartus Prime 


## Instalar el IDE de su preferencia (si no desea utilizar los del fabricante)
* [Vim](https://www.vim.org/)
* [Atom](https://atom.io/)
* [Eclipse](https://www.eclipse.org) + [PyDev](https://www.pydev.org/)
* [Sublime Text](http://www.sublimetext.com)



## Instalación de ISEWebpack
### Descargar instalador
descargar los archivos de instalaciòn de ISE DS según el sistema operativo del siguiente [link](https://www.xilinx.com/content/xilinx/en/downloadNav/design-tools/v2012_4---14_7.html) o [link Windows 10](https://www.xilinx.com/member/forms/download/xef.html?filename=Xilinx_ISE_S6_Win10_14.7_ISE_VMs_0206_1.zip)

**NOTA**: si no cuenta con usuaria registrado en la pagina de Xilinx debe crear uno.

A continuación se indican los pasos acorde al sistema operativo

### Instalación en Windows
* Descomprimir el archivo descargado  y ejecute, como administrador, el archivo **xsetup.exe**.
* Cuando se solicite, debe seleccionar el instalador de ISEWebpack.
* Instale en la carpeta por defecto que indica el instalador
* Si esta en Windows 8 ó 10.  y tiene problemas al iniciar ISE,  debe seguir la siguiente guía para modificar libPortability [link](https://www.xilinx.com/support/answers/62380.html) , o si lo prefiere descargue el patch de este [link](https://github.com/cbureriu/xilinx-14.7-patch-for-Win10-32-64)

### Instalación en Linux
* Descomprima el archivo descargado,  y en `Terminal` ingrese a la carpeta descomprimida 
* Dar permisos de ejecución al archivo *xsetup* para ello digital el siguiente comando:

```
sudo chmod +x xsetup
```

**Nota:** observe si se encuentra al interior de la carpeta Xilinx que , acaba de descomprimir . y que el bash  no informe de error al dar los permisos  del archivo

* Para lanzar el wizard de instalación en la `Terminal`, ejecutar el comando:

```
sudo ./xsetup
```

* Se recomienda instalar Xilinx  en la dirección `opt/Xilinx`. para ello, observe  si el wizard de instalación  tiene configurada la misma.

**Nota:** Tenga presente en la ventana donde solicite instalar componentes adicionales del software, no marcar la opción *install cable drivers*
* Cuando se solicite, debe seleccionar el instalador de ISEWebpack.  

#### Configuración del Path

* Una vez instalado el software, desde la `Terminal' ejecute en orden las siguientes instrucciones    

```
echo "PATH=\$PATH:/opt/Xilinx/14.7/ISE_DS/ISE/bin/lin64/" >> ~/.bashrc echo "export PATH" >> ~/.bashrc
```

* Si no desea tener el PATH  fijo  ejecute el siguiente comando, antes de  iniciar ISE:
 
```
source /opt/Xilinx/14.7/ISE_DS/settings64.sh
```


* Ejecute `ise` en la terminal, ya estara correctamente instalado.


### Configuración de licencia 
* Abrir ***ISE Design Suite*** y hacer clic en `Help > Manager License` 
* Seleccionar en `Acquiere a License` la opción `Get Free Vivado/ISE WebPack Licence`
* Seguir las indicaciones de la web de Xilinx para generar  y descargar la licencia.
* Una vez descargada la licencia `Xilinx.lic`, volver a hacer clic en `Help > Manager License` y hacer clic en `Load License ...`, para cargar el archivo `Xilinx.lic`.

## Instalar driver programación para FPGA

Nota: si se instala ISE Webpack o Vivado IDE, con los driver de programación, y se desea usar iMPACT  no es necesario realizar los pasos  que a continuación se describen.

Dependiendo de la tecnología FPGA y/o la tarjeta de desarrollo a usar, se debe instalar y configurar las  herramienta de inicialización, porgramación y borrado de FPGA (Ej. Digilent Adept , xc3sprog). Seguir las instrucciones de instalación de cada proveedor:


* [Digilent Adept](https://reference.digilentinc.com/reference/software/adept/start?redirect=1#software_downloads). En linux instalar Runtime y Utilities
* [xc3sprog](http://xc3sprog.sourceforge.net/)
* [openOCD](http://openocd.org/getting-openocd/)

´openOCD´, ademas de programar el firmware y ser una herramienta para el Debug en el chip, es útil para descargar el bitstream a la FPGA o a la Flash.
Se recomienda tener la última versión actualizada  de openOCD, para ello descargar el código fuente del link: [https://sourceforge.net/p/openocd/code/ci/master/tree/](https://sourceforge.net/p/openocd/code/ci/master/tree/).  para cargar el bitstream, a la FPGA debe ejecutar el siguiente comando  

```
 openocd -f quacho_basic_at.cfg -c "init;xc6s_print_dna xc6s.tap;shutdown"

```

