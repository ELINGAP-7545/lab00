# lab00

***Field Programmable Gate Array (FPGA)*** son dispositivos reconfigurables, en los cuales se puede implementar cualquier lógica combinacional o secuencia, en generial un amplio abanico de funciones electronicas. Esto es gracias a que las FPGAS son dispositivos que integran bloques lógicos y que se pueden interconectar según la funcional deseada escrita en el Lenguaje de descripción de hardware (HDL).

Para obtener mas información, se recomienda leer [FPGAs For Dummies eBook](https://www.intel.com/content/dam/www/programmable/us/en/pdfs/literature/misc/FPGAs_For_Dummies_eBook.pdf)

# Configuración Framework para FPGA

Para general el bitstream, archivo que contiene la información de programación de la FPGA, los fabricantes de FPGAS ofrencen las herramientas de desarrollo propias, como Intel, Xilinx, Lattice, etc., que facilitan la integración del sistema hardware con el HDL.
Por ellos, y acorde con la tecnología de trabajo se recomienda instalar las herramientas IDE y de sintetización, según gustos y tecnología. en este sentido el primer paso en este laboratorio es descargar las herramientas de diseño de hardware.

### Herramientas de Sintetización

* [ISEWebpack](https://github.com/Fabeltranm/SPARTAN6-ATMEGA-MAX5864/wiki/Instalaci%C3%B3n-y-Configuraci%C3%B3n#instalaci%C3%B3n-de-isewebpack) Descontinuado 
* [Vivado](https://www.xilinx.com/products/design-tools/vivado.html)
* [yosys](http://www.clifford.at/yosys/) Open
* [migen](https://github.com/Fabeltranm/lm32_SoC/wiki/Instalación-y-configuración-de-las-herramientas-Litex-y-migen)
* [Quartus Prime lite](http://fpgasoftware.intel.com/?edition=lite) 

### Instalar el IDE de su preferencia (si no desea utilizar los del fabricante)
* [Vim](https://www.vim.org/)
* [Atom](https://atom.io/)
* [Eclipse](https://www.eclipse.org) + [PyDev](https://www.pydev.org/)
* [Sublime Text](http://www.sublimetext.com)

## Instalación de Quartus Prime lite
Esta guia esta basada en el lab0 de intel [link](./docs//Intro_to_FPGA.pdf) 

### Descargar instalador
* Descargar los archivos de instalaciòn de Quartus Prime lite del siguiente [link](http://fpgasoftware.intel.com/?edition=lite)
* Selecione  la version 19.4 (o superior) y  seleciones el sistema operativo  respectivo
* Descomprima  y ejecute el arcivo ***setup***. Siga las instrucciones de instalación de Quartus tools para su computador.

**NOTA**: si no cuenta con usuario registrado en la pagina de Intel debe crear uno.

## Configuración básica para configurar un nuevo proyecto en Quartus Prime lite

* Una vez instalado, debe abrir el programa ´Quartus´.
* En la barra de herramientas (toolbar) de Quartus, navegar en el menu 'File' y hacer clic en  ´´´New Project Wizard´´´. (ver imagen)

![proyectWizard](./figs/f1.pdf) 

![proyectWizard](./figs/f2.pdf) 

![proyectWizard](./figs/f3.pdf) 

![proyectWizard](./figs/f4.pdf) 

![proyectWizard](./figs/f5.pdf) 

### Ejercicio 1 - Diseño de sumador 1 bit 



### Especificación
Diseñar un sumador de un bit A y un bit B completo. Es decir el sumador cuenta con carrier  y se comporta acorde a la siguiente tabla de verdad.

A  | B  | Cin | Out | Cout 
-- | -- | --  | --  |  --
0| 0 | 0 |0 | 0
0| 0 | 1 | 1| 0
0| 1 | 0 | 1| 0
0| 1 | 1 | 0| 1
1| 0 | 0 | 1| 0
1| 0 | 1 | 0| 1
1| 1 | 0 | 0| 1
1| 1 | 1 | 1| 1

## Bloque Funcional

Según la especificación del sumador completo de 1 bit. se deduce que el bloque o modulo funcional esta dado por la siguiente gráfica: 

![Sumador 1bit](https://github.com/Fabeltranm/SPARTAN6-ATMEGA-MAX5864/blob/master/lab/lab01-sumador1b/doc/bloqSum1b.jpg)

## Lógica Combinacional 

Optimizando el circuito, según la Tabla de verdad , podemos observar que la lógica combinación del ejercicio propuesto esta dada por:

![Sumador 1bit](https://github.com/Fabeltranm/SPARTAN6-ATMEGA-MAX5864/blob/master/lab/lab01-sumador1b/doc/sum1bPuertas.jpg)
 
## Implementación HDL verilog

Antes que nada  verifique que tenga el programa para sintetizar la descripción de hardware.

### Descripción Funcional 

Una vez abierto el  framework  de su preferencia, digitar o copiar el siguiente código

```verilog

module sum1bcc_primitive (A, B, Ci,Cout,S);

  input  A;
  input  B;
  input  Ci;
  output Cout;
  output S;

  wire a_ab;
  wire x_ab;
  wire cout_t;

  and(a_ab,A,B);
  xor(x_ab,A,B);

  xor(S,x_ab,Ci);
  and(cout_t,x_ab,Ci);

  or (Cout,cout_t,a_ab);

endmodule
```
Observe que el HDL inicia con la descripción del módulo ``` sum1bcc_primitive.v``` : Se definen las  entradas  y salidas del bloque funcional , tal cual  como se estaba especificado en el bloque funcional

Luego se instancia las respectivas puertas lógicas (AND, OR, XOR), acorde a los resultados de la lógica de la tabla de verdad. Se resalta la definición de tres componentes ```a_ab, x_ab, cout_t ``` , de tipo ```wire ```, que no es  mas que 'cables' utilizados para conectar las salidas y entradas de unos módulos, en el actual ejemplo son conexiones de puertas. 

Sin embargo,  como su nombre lo indica se esta realizando una descripción funcional del módulo, y en este sentido, podemos tener varios  tipos de descripción. en el archivo ``` sum1bcc.v```, pueden observar la siguiente descripción:

```verilog
module sum1bcc (A, B, Ci,Cout,S);

  input  A;
  input  B;
  input  Ci;
  output Cout;
  output S;

  reg [1:0] st;

  assign S = st[0];
  assign Cout = st[1];

  always @ ( * ) begin
    st  =   A+B+Ci;
  end
  
endmodule
```

Se evidencia que esta nueva descripción cuenta con un  ```  Reg ```  de 2 bits ``` st ```. ``` Reg ``` , en este sentido, representan un elemento de almacenamiento de datos y conserva dicho valor hasta que se les asigna el siguiente valor.

### Simulación ISIM
General la simulación visual  y forzar la entradas A B y Ci a clock para  validar todas las posibles entradas.
Comprobar su funcionamiento.


