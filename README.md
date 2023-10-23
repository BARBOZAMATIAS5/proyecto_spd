# Proyecto SPD

El proyecto presentado muestra un contador, mostrados a traves de dos displays de 7 segmentos, del 0 al 99, usando la técnica de la multiplexación, combinando dos señales y transmitiendo por un solo medio.

# FUNCIONES:
- En primera instancia del código, asocio a través de #define, los nombres de los componentes que están conectados al ARDUINO, al igual que la inicialización de variables que ayudaran para el funcionamiento del contador.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/e2c013b3-98dc-4743-af33-4af29031a8aa)


- Próximo a ello, se encuentra la primera función “setup()” que se encarga de configurar los pines si pertenecen a INPUT (entradas) o OUTPUT (salidas).

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/238e4d18-ef78-403e-a45f-c2e60375458e)


- La función “loop()” será donde se ejecute el código continuamente, donde incluirá variables y funciones.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/9d8b0cd0-176c-41f5-a4f9-f25e83395c4b)


- La función “void numerosContador(int)” mostrará, en los displays de 7 segmentos, los números pasados por parámetro, prendiendo y apagando respectivamente los leds correspondientes que formen ese número (ejemplo recortado hasta case 4).

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/60acdd14-106b-486e-a952-24edb21025d4)


- La función ” void prenderDisplay(int)” tiene como funcionalidad, prender y apagar los displays dependiendo de lo pasado por parámetro (siendo LEDUNIDAD o LEDDECENA, identificadores creados al principio del código del proyecto) e introduciendo un delay para generar un retraso en el prendido y apagado.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/b61b106e-9828-481e-9b0a-06255db738f0)


- “mostrarContador(int)” como dice su nombre, se encargará de mostrar en los displays, el numero pasado por parámetro (menor o igual a 99, mayor o igual 0), usando la función “prenderDisplay(int)” y la función “numerosContador(int)”.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/16223618-d6e2-4de0-a04c-42703de2cb0a)


- Y por ultimo se encuentra la función “int pulsadorEstador(void)”, su objetivo es hacer que dependiendo de los tres pulsadores, cual ha sido pulsado y lo devuelve para ser usado en la función “loop()”, dentro de la variable pulsador.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/17f084b8-a64e-4d04-a974-3896d9a376af)

