# Proyecto SPD

El proyecto ofrece un contador del 0 al 99, usando la técnica de la multiplexación, combinando dos señales y transmitiendo por un solo medio.

En primera instancia del código, asocio a través de #define, los nombres de los componentes que están conectados al ARDUINO, al igual que la inicialización de variables que ayudaran para el funcionamiento del contador.
Próximo a ello, se encuentra la primera función “setup()” que se encarga de configurar los pines si pertenecen a INPUT (entradas) o OUTPUT (salidas).
(inserte foto)
La función “loop()” será donde se ejecute el código continuamente, donde incluirá variables y funciones.
(inserte foto)
La función “void numerosContador(int)” mostrará, en los displays de 7 segmentos, los números pasados por parámetro, prendiendo y apagando respectivamente los leds correspondientes que formen ese número.
(inserte foto)
La función ” void prenderDisplay(int)” tiene como funcionalidad, prender y apagar los displays dependiendo de lo pasado por parámetro (siendo LEDUNIDAD o LEDDECENA, identificadores creados al principio del código del proyecto) e introduciendo un delay para generar un retraso en el prendido y apagado.
“mostrarContador(int)” como dice su nombre, se encargará de mostrar en los displays, el numero pasado por parámetro (menor o igual a 99, mayor o igual 0), usando la función “prenderDisplay(int)” y la función “numerosContador(int)”.
Y por ultimo se encuentra la función “int pulsadorEstador(void)”, su objetivo es hacer que dependiendo de los tres pulsadores, cual ha sido pulsado y lo devuelve para ser usado en la función “loop()”, dentro de la variable pulsador.
