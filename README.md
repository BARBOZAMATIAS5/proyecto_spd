# Alumno

- Barboza Matias Gabriel


# Proyecto SPD: Primera parte 

El proyecto presentado muestra un contador, mostrados a traves de dos displays de 7 segmentos, del 0 al 99, usando la técnica de la multiplexación, combinando dos señales para mostrar dentro de una numeros de dos dígitos. Se usarán pulsadores para aumentar, disminuir o reestablecer el contador a 0.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/b779da4b-024a-4b7d-8548-71052facff5a)



# FUNCIONES
- En primera instancia del código, asocio a través de #define, los nombres de los componentes que están conectados al ARDUINO, ademas tambien inicializo variables que ayudaran para el funcionamiento del contador.

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




# Proyecto SPD: Segunda parte

El proyecto presentado muestra un contador, mostrados a traves de dos displays de 7 segmentos, del 0 al 99, usando la técnica de la multiplexación, combinando dos señales para mostrar dentro de una numeros de dos dígitos. En este caso, usaremos un sensor de flexión para cambiar el numero mostrado, y, ademas un interruptor que si mostrar el contador de a uno, o solo numeros primos.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/999f957c-7394-4ccb-bcf5-8300cde4ae0b)

# FUNCIONES

- Empezamos asociamos a traves de #define a los pines que representan cada componente del proyecto, y tambien inicializamos variables.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/68a02cec-c409-4b98-9c45-278a9d7d8fff)


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


- Y por ultimo, tendremos la función "bool esPrimo(int)" y su objetivo es, mediante lo pasado por parametro, determinar si dicho numero es primo o no.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/6cb40226-0a7a-4791-b932-4ca0bdd12e56)


# INVESTIGACION acerca del MOTOR CC

El motor CC es una máquina que convierte energía eléctrica en mecánica, provocando un movimiento rotatorio, gracias a la acción de un campo magnético. 
Podemos controlar la rotación del componente a través de sus terminales, dependiendo de su conexión y cual de los dos reciba corriente eléctrica. Si se encuentran conectados y recibiendo corriente por los terminales, no se vería ningún resultado por el intento del motor de rotar para ambos sentidos opuestos.

El funcionamiento del motor CC en este proyecto serviría para aumentar o disminuir el contador a través de pulsadores sin la necesidad de tener que pulsar para que suba o baje, si no que cada pulsación aumente la velocidad de crecimiento o decrecimiento, usando dos pulsadores para ello y, uno reestablecer el contador a 0 y apagar el motor CC.
