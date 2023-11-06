----------------------------------
# Alumno

- Barboza Matias Gabriel

----------------------------------
# Proyecto SPD: Primera parte 

El proyecto presentado muestra un contador a traves de dos displays de 7 segmentos del 0 al 99, usando la técnica de la multiplexación, combinando dos señales para mostrar dentro de una, numeros de dos dígitos. Se usarán pulsadores para aumentar, disminuir o reestablecer a 0, al contador.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/b779da4b-024a-4b7d-8548-71052facff5a)


----------------------------------
# FUNCIONES
- Inicializacion de variables y los #define para agregar los componentes, asociandolos a pines del arduino como tambien, para usarlos como variables constantes.

~~~ C
#define PULSADOR_MAS 4
#define PULSADOR_MENOS 3
#define PULSADOR_RESET 5

#define PIN_A 12
#define PIN_B 13
#define PIN_C 7
#define PIN_D 8
#define PIN_E 9
#define PIN_F 11
#define PIN_G 10

#define LEDUNIDAD A4
#define LEDDECENA A5
#define OFF 0

#define TIEMPODISPLAY 10

int contador = 0;
int pulsador = 0;

int sumarContador = 1;
int sumarAnterior = 1;

int restarContador = 1;
int restarAnterior = 1;

int resetearContador = 1;
int resetearAnterior = 1;
~~~



- setup()

Se configuran los pines del sistema si son INPUT (entradas) o OUTPUT (salidas). Aquellas que son configuradas como INPUT_PULL, conectan resistencias internamente de 20kOmhs y +5V, sin la necesidad de componentes externos.

~~~ C
void setup()
{
  pinMode(LEDUNIDAD, OUTPUT);
  pinMode(LEDDECENA, OUTPUT);
  pinMode(PIN_A, OUTPUT);
  pinMode(PIN_B, OUTPUT);
  pinMode(PIN_C, OUTPUT);
  pinMode(PIN_D, OUTPUT);
  pinMode(PIN_E, OUTPUT);
  pinMode(PIN_F, OUTPUT);
  pinMode(PIN_G, OUTPUT);
  pinMode(PULSADOR_MAS, INPUT_PULLUP);
  pinMode(PULSADOR_MENOS, INPUT_PULLUP);
  pinMode(PULSADOR_RESET, INPUT_PULLUP);

  Serial.begin(9600);
}
~~~



- loop()

Se encarga de ejecutar el código continuamente como un bucle.

Dentro de la funcion: 
'pulsador' mantiene un estado dependiendo del pulsador apretado (PULSADOR_MAS o PULSADO_MENOS).

'mostrarContador(contador)' es una funcion que muestra en los displays el numero que almacena la variable 'contador'.

Se usa la funcion 'if-else' para aumentar o disminuir el numero almacenado en la variable 'contador' y, tambien, como condicionamento de que si esta variable: supera el numero 99, entonces el contador vuelve a 0; o es menor a 0, entonces el contador pasa a 99.
~~~ C
void loop()
{
  pulsador = pulsadorEstado();
  
  mostrarContador(contador);
  
  if (pulsador == PULSADOR_MAS)
  {
    contador++;
  }
  else if (pulsador == PULSADOR_MENOS)
  {
  	contador--;  
  }
  else if (pulsador == PULSADOR_RESET)
  {
    contador = 0;
  }
  
  if (contador > 99)
  {
    contador = 0;
  }
  else if (contador < 0)
  {
    contador = 99;
  }
  
  delay(TIEMPODISPLAY);
}
~~~



- void numerosContador(int)

Muestra en los displays el numero pasado por parametro, prendiendo y apagando los segmentos mediante la funcion 'digitalWrite(NUMERODEPIN, HIGH/LOW)'.

PIN_A - PIN_B - PIN_C - PIN_D - PIN_E - PIN_F - PIN_G -> #define asociado a pines.

Dentro de la función:

Se apagan todos los segmentos que estan asociados a pines.

Se usa la funcion 'switch ()' donde, dependiendo del numero (0 a 9) pasado por parametro, apagará o prenderá los segmentos que conformen la figura de ese número.

~~~ C
void numerosContador(int contador)
{
  digitalWrite(PIN_A, LOW);
  digitalWrite(PIN_B, LOW);
  digitalWrite(PIN_C, LOW);
  digitalWrite(PIN_D, LOW);
  digitalWrite(PIN_E, LOW);
  digitalWrite(PIN_F, LOW);
  digitalWrite(PIN_G, LOW);
  switch (contador)
  {
    case 1:
      digitalWrite(PIN_A, LOW);
  	  digitalWrite(PIN_B, HIGH);
      digitalWrite(PIN_C, HIGH);
  	  digitalWrite(PIN_D, LOW);
      digitalWrite(PIN_E, LOW);
  	  digitalWrite(PIN_F, LOW);
      digitalWrite(PIN_G, LOW);
    break;
    case 2:
      digitalWrite(PIN_A, HIGH);
  	  digitalWrite(PIN_B, HIGH);
      digitalWrite(PIN_C, LOW);
  	  digitalWrite(PIN_D, HIGH);
      digitalWrite(PIN_E, HIGH);
  	  digitalWrite(PIN_F, LOW);
      digitalWrite(PIN_G, HIGH);
    break;
    case 3:
      digitalWrite(PIN_A, HIGH);
  	  digitalWrite(PIN_B, HIGH);
      digitalWrite(PIN_C, HIGH);
  	  digitalWrite(PIN_D, HIGH);
      digitalWrite(PIN_E, LOW);
  	  digitalWrite(PIN_F, LOW);
      digitalWrite(PIN_G, HIGH);
    break;
    case 4:
      digitalWrite(PIN_A, LOW);
  	  digitalWrite(PIN_B, HIGH);
      digitalWrite(PIN_C, HIGH);
  	  digitalWrite(PIN_D, LOW);
      digitalWrite(PIN_E, LOW);
  	  digitalWrite(PIN_F, HIGH);
      digitalWrite(PIN_G, HIGH);
    break;
    case 5:
      digitalWrite(PIN_A, HIGH);
  	  digitalWrite(PIN_B, LOW);
      digitalWrite(PIN_C, HIGH);
  	  digitalWrite(PIN_D, HIGH);
      digitalWrite(PIN_E, LOW);
  	  digitalWrite(PIN_F, HIGH);
      digitalWrite(PIN_G, HIGH);
    break;
    case 6:
      digitalWrite(PIN_A, HIGH);
  	  digitalWrite(PIN_B, LOW);
      digitalWrite(PIN_C, HIGH);
  	  digitalWrite(PIN_D, HIGH);
      digitalWrite(PIN_E, HIGH);
  	  digitalWrite(PIN_F, HIGH);
      digitalWrite(PIN_G, HIGH);
    break;
    case 7:
      digitalWrite(PIN_A, HIGH);
    	digitalWrite(PIN_B, HIGH);
      digitalWrite(PIN_C, HIGH);
  	  digitalWrite(PIN_D, LOW);
      digitalWrite(PIN_E, LOW);
  	  digitalWrite(PIN_F, LOW);
      digitalWrite(PIN_G, LOW);
    break;
    case 8:
      digitalWrite(PIN_A, HIGH);
  	  digitalWrite(PIN_B, HIGH);
      digitalWrite(PIN_C, HIGH);
  	  digitalWrite(PIN_D, HIGH);
      digitalWrite(PIN_E, HIGH);
  	  digitalWrite(PIN_F, HIGH);
      digitalWrite(PIN_G, HIGH);
    break;
    case 9:
      digitalWrite(PIN_A, HIGH);
  	  digitalWrite(PIN_B, HIGH);
      digitalWrite(PIN_C, HIGH);
  	  digitalWrite(PIN_D, LOW);
      digitalWrite(PIN_E, LOW);
  	  digitalWrite(PIN_F, HIGH);
      digitalWrite(PIN_G, HIGH);
    break;
    case 0:
      digitalWrite(PIN_A, HIGH);
  	  digitalWrite(PIN_B, HIGH);
      digitalWrite(PIN_C, HIGH);
  	  digitalWrite(PIN_D, HIGH);
      digitalWrite(PIN_E, HIGH);
  	  digitalWrite(PIN_F, HIGH);
      digitalWrite(PIN_G, LOW);
    break;
  }
}
~~~



- 'void prenderDisplay(int)'

Su funcion es prender uno de los dos displays, pasado por parametro, y apagar el contrario, y se le agrega un delay() para que haya una pausa. 

LEDUNIDAD - LEDDECENA -> #define asociados a pines | TIEMPODISPLAY -> #define usado como constante.

Dentro de la función:

Se usa la funcion 'if-else' para prender el display pasado por parametro y apagar el otro durante un lapso de tiempo, dependiendo del valor de TIEMPODISPLAY. Si no se cumplen ninguna de las dos condiciones especificadas, entonces se prenden ambos a la vez.

~~~ C
void prenderDisplay(int numDisplay)
{
  if (numDisplay == LEDUNIDAD)
  {
    digitalWrite(LEDUNIDAD, LOW);
    digitalWrite(LEDDECENA, HIGH);
    delay(TIEMPODISPLAY);
  }
  else if (numDisplay == LEDDECENA)
  {
    digitalWrite(LEDDECENA, LOW);
    digitalWrite(LEDUNIDAD, HIGH);
    delay(TIEMPODISPLAY);
  }
  else
  {
    digitalWrite(LEDDECENA, HIGH);
    digitalWrite(LEDUNIDAD, HIGH);
  }
}
~~~



- 'mostrarContador(int)'
Se encarga de la visualizacion del numero pasado por parametro.

OFF -> #define usado como constante

Dentro de la función:

Se usan funciones que fueron explicadas anteriormente: prenderDisplay() - numerosContador().

Primero se apagan ambos displays con la funcion prenderDisplay() para despues, dentro de la funcion numerosContador(), se hace una operacion en el argumento: 'contador / 10', lo cual mostrará en la decena el resultado -> si 9 / 10 = 0.9, entonces mostrará el 0. Para mostrar en la decena dicho número, se llamará nuevamente a la funcion prenderDisplay() especificando en el argumento LEDDECENA, y se procede a apagar ambos de nuevo. Para mostrar la unidad se llamará otra vez a la funcion numerosContador() con la operacion 'contador-10*((int)contador/10)' -> si 9 - 10*((int)9/10) => 9 - 10*0 => 9-0 = 9. Y por ultimo, se llamará a prenderDisplay() con el argumento LEDUNIDAD.

~~~ C
void mostrarContador(int contador)
{
  prenderDisplay(OFF);
  numerosContador(contador/10);
  prenderDisplay(LEDDECENA);
  prenderDisplay(OFF);
  numerosContador(contador - 10*((int)contador/10));
  prenderDisplay(LEDUNIDAD);
}
~~~



- 'int pulsadorEstador(void)'
Retorna el pulsador que fue pulsado sin la necesidad de tener que mantener.

~~~ C
int pulsadorEstado()
{
  sumarContador = digitalRead(PULSADOR_MAS);
  restarContador = digitalRead(PULSADOR_MENOS);
  resetearContador = digitalRead(PULSADOR_RESET);

  if (sumarContador)
  {
    sumarAnterior = 1;
  }
  if (restarContador)
  {
    restarAnterior = 1;
  }
  if (resetearContador)
  {
    resetearAnterior = 1;
  }

  if (sumarContador == 0 && sumarContador != sumarAnterior)
  {
    sumarAnterior = sumarContador;
    return PULSADOR_MAS;
  }
  else if (restarContador == 0 && restarContador != restarAnterior)
  {
    restarAnterior = restarContador;
    return PULSADOR_MENOS;
  }
  else if (resetearContador == 0 && resetearContador != resetearAnterior)
  {
    resetearAnterior = resetearContador;
    return PULSADOR_RESET;
  }
  return 0;
}
~~~



# LINK PROYECTO PRIMERA PARTE:

https://www.tinkercad.com/things/fDUVDTE0yT6




----------------------------------
# Proyecto SPD: Segunda parte

(describir proyecto)

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/a364f489-fc89-4408-b3d5-a053545faa95)


----------------------------------

# Cambios realizados:

(describir los cambios realizados con respecto del anterior)

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/da82dd7d-f415-4549-874e-79ac7dd84953)

*Agregados
- Switch.
- Motor CC.
- Transitor NPN.
- Sensor de flexion.

----------------------------------
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

----------------------------------
# INVESTIGACION acerca del MOTOR CC - TRANSITOR NPN - SENSOR de FLEXION:

El motor CC es una máquina que convierte energía eléctrica en mecánica, provocando un movimiento rotatorio, gracias a la acción de un campo magnético. 
Podemos controlar la rotación del componente a través de sus terminales, dependiendo de su conexión y cual de los dos reciba corriente eléctrica. Si se encuentran conectados y recibiendo corriente por los terminales, no se vería ningún resultado por el intento del motor de rotar para ambos sentidos opuestos.

El funcionamiento del motor CC en este proyecto serviría para aumentar o disminuir el contador a través de pulsadores, con solo pulsar una vez, el contador suba o baje automaticamente en base a la velocidad del motor, usando dos pulsadores para ello y, uno reestablecer el contador a 0 y apagar el motor CC.


- Fuente MOTOR CC:
  
  https://bricolabs.cc/wiki/guias/control_de_motores
  
  https://www.zuendo.com/smartblog/26_Motores-cc-ventajas-inconvenientes.html
  
  https://www.youtube.com/watch?v=kr5qde6IIRk


# LINK PROYECTO SEGUNDA PARTE: 

https://www.tinkercad.com/things/3ucjSRs74In

----------------------------------

# Proyecto SPD: Tercera parte

(describir proyecto)

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/4133c028-6a4b-4d46-8439-b448a1681524)


-----------------------------------
# Cambios realizados:

(describir los cambios realizados)

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/29d7cb98-8bce-439b-ab76-2411f81d232b)

*Agregados:
- Fotorresistencia.

------------------------------------

# FUNCIONES

(explicar las nuevas funciones)

----------------------------------
# INVESTIGACION acerca de la FOTORRESISTENCIA

(investigacion)


# LINK PROYECTO TERCERA PARTE:

https://www.tinkercad.com/things/bmz2OQ4oxsI


----------------------------------
# Proyecto SPD: Cuarta parte

(describir proyecto)

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/986c79df-1330-40c2-8e7a-953560e99cc4)


-----------------------------------
# Cambios realizados:

(describir los cambios realizados)

------------------------------------

# FUNCIONES

(explicar las nuevas funciones)


----------------------------------
# LINK PROYECTO CUARTA PARTE:

https://www.tinkercad.com/things/dcDukXcITqy
