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

Se encarga de ejecutar el sistema.

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



- void prenderDisplay(int)

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



- mostrarContador(int)
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



- int pulsadorEstador(void)

Retorna el estado del pulsador como un #define (valor del pin pulsado). PULSADOR_MAS 4 <- pin 4

Se le atribuyen a las variables: 'sumarContador' = lectura de PULSADOR_MAS, 'restarContador' = lectura de PULSADOR_MENOS, 'resetearContador' = lectura de PULSADOR_RESETEAR 

Dentro de la funcíon:

La función usa bloques de 'if-else' para cambiar los estados de las variables, siempre y cuando se cumpla las condiciones, la funcion retornará un #define haciendo alusion a un pin, de lo contrario retornará 0.

Explicacion 'if': Si sumarContador es igual a 0 && (Y) sumarContador es diferente de sumarAnterior, entonces entra dentro de este if retornando PULSADOR_MAS (en este caso) y, cambiando el valor de sumarAnterior a que sea igual a sumarContador, imposibilitando nuevamente la entrada a este bloque en caso de mantener apretado el pulsador, ya que sumarContador y sumarAnterior van a tener los mismos valores.

~~~ C
int pulsadorEstado(int)
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

Al igual que el proyecto anterior, es un contador que muestra numeros del 00 al 99 mediante dos displays de 7 segmentos usando la tecnica de la multiplexacion. En este caso, haremos uso de un switch para cambiar el funcionamiento del contador, mostrando numeros primos o no. Se usará la velocidad del motor para aumentar el contador dependiendo de a la velocidad que vaya y se lo controlará mediante el sensor de flexion.
Se seguirá usando dos pulsadores para aumentar o disminuir los valores del contador pero sin tener que apretar siempre que se quiera realizar alguna acción.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/a364f489-fc89-4408-b3d5-a053545faa95)


----------------------------------

# Cambios realizados:

Componentes agregados:
- Switch.
- Motor CC.
- Transitor NPN.
- Sensor de flexion.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/da82dd7d-f415-4549-874e-79ac7dd84953)

Se han agregado #define, variables, una nueva función y se han modificado partes del código de algunas funciones.

----------------------------------
# FUNCIONES

Las siguientes FUNCIONES siguen manteniendo su estructura:
  - void numerosContador(int)
  - void prenderDisplay(int)
  - mostrarContador(int)


Los #define se asocian a los pines y se crean variables.

~~~ C
#define MOTOR 3
#define SENSOR_FLEXION A3

#define PULSADOR_MAS 5
#define PULSADOR_MENOS 4
#define SWITCH_CONTADOR 6

#define PIN_A 12
#define PIN_B 13
#define PIN_C 7
#define PIN_D 8
#define PIN_E 9
#define PIN_F 11
#define PIN_G 10

#define OFF 0
#define LEDUNIDAD A4
#define LEDDECENA A5

#define TIEMPODISPLAY 10
#define REVOLUCIONES 36
#define TIEMPOCONTADOR 150

unsigned long tiempo;
unsigned long tiempo_transcurrido = 0;

int contador = 0;
int pulsador = 0;
int contadorPrimo = 0;

int sumarContador = 1;
int sumarAnterior = 1;

int restarContador = 1;
int restarAnterior = 1;

int n = 0;
int velocidadMotor = 0;
int sensorFlexion = 0;
int sumarORestar = 0;

int switchContador;
~~~



- setup()
  
Configuración de los nuevos pines.

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
  pinMode(MOTOR, OUTPUT);
  pinMode(SENSOR_FLEXION, INPUT_PULLUP);
  pinMode(PULSADOR_MAS, INPUT_PULLUP);
  pinMode(PULSADOR_MENOS, INPUT_PULLUP);
  pinMode(SWITCH_CONTADOR, INPUT);

  Serial.begin(9600);
}
~~~



- loop()

Se encarga de ejecutar el sistema.

Dentro de la funcion:

'tiempo' almacena la funcion millis(), devuelve milisegundos y empieza a contar una vez ejecutado el código.

'pulsador' se encargará de almacenar el valor que devuelva la funcion 'pulsadorEstado()'

'switchContador' cambiará de numeros primos a no primos, o viceversa, siempre que se interactue con el.

'sensor' almacena el valor de la funcion map() donde limita los valores del sensor de flexion de 0 a 7.

'n' servirá para controlar la velocidad del motor CC, donde se multiplica 1 * #REVOLUCIONES (36: cada 36 pasa a otra revolucion) * 'sensor'.

La funcion consta del uso de funciones 'if-else' que nos permiten: cambiar de primos a no primos, aumentar o disminuir el contador, condicionar al contador para que se mantenga entre 00 a 99, cambio de estado del pulsador.

~~~ C 
void loop()
{
  tiempo = millis();
  pulsador = pulsadorEstado();
  switchContador = digitalRead(SWITCH_CONTADOR);
  sensorFlexion = map(analogRead(SENSOR_FLEXION), 384, 783, 0, 7);
  n = 1 * REVOLUCIONES *  sensorFlexion;
  
  analogWrite(MOTOR, n);
  
  if (switchContador == 1)//primo
  {
    if (esPrimo(contador))
    {
      mostrarContador(contador);
      contadorPrimo = contador;
    }
    else
    {
      mostrarContador(contadorPrimo);
    }
  }
  else if(switchContador == 0) //no primo
  {
    mostrarContador(contador);
  }
  
  if (tiempo - tiempo_transcurrido > TIEMPOCONTADOR)
  {
    tiempo_transcurrido = tiempo;
    contador = cambiarOperacion(sumarORestar, contador, sensorFlexion);
  }
  
  if (contador > 99)
  {
    contador = contador - 99;
  }
  else if (contador < 0)
  {
    contador = contador + 99;
  }
  
  if (pulsador == PULSADOR_MAS)
  {
    sumarORestar = 0;
  }
  else if (pulsador == PULSADOR_MENOS)
  {
    sumarORestar = 1;
  }
  
  delay(TIEMPODISPLAY);
}
~~~



- cambiarOperacion(int, int, int)

Su funcionalidad es sumar o restar al parametro 'contador', el valor de 'valor', y retornando 'contador'.

Dentro de la funcion:

Usa la funcion 'if-else' para realizar o el aumento o la disminucion del contador dependiendo de si la variable 'cambio' (pasada por parametro) cumple alguna de los dos condiciones.

~~~ C
int cambiarOperacion (int cambio, int contador, int valor)
{
  if (cambio == 0)
  {
    contador += valor;
  }
  else if (cambio == 1)
  {
    contador -= valor;
  }
  return contador;
}
~~~


- pulsadorEstado(int)

Retorna el estado del pulsador como un #define (valor del pin pulsado).

Dentro de la función:

Mantiene el mismo funcionamiento que el del proyecto anterior, exceptuando que se ha eliminado las variables, #define y funciones 'if-else' referidos a RESETEAR el contador.

~~~C
int pulsadorEstado()
{
  sumarContador = digitalRead(PULSADOR_MAS);
  restarContador = digitalRead(PULSADOR_MENOS);

  if (sumarContador)
  {
    sumarAnterior = 1;
  }
  if (restarContador)
  {
    restarAnterior = 1;
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
  return 0;
}
~~~



- bool esPrimo(int)

Retorna si el numero pasado por parametro, es primo entonces true, o, no es primo entonces false.

Dentro de la función:

Se usa las funciones 'if-else' empezando con, si 'contador' es menor o igual a 1, entonces retorna FALSE, caso contrario, entra en la funcion 'for' que tiene como variable local 'i = 2', como condicion "si i es menor o igual a contador / 2" entonces se le suma 1 a i cada vez que se cumpla. Dentro de este bloque se encuentra un 'if', el cual, si el resto de 'contador' e 'i' es igual a 0, entonces retorna FALSE, pero si no ocurre esto, devolverá TRUE.

La condicion dentro del 'for' >>> "i <= contador / 2", simplifica la búsqueda, ya que, si antes de la mitad del número, no se encontraron divisores, se da por supuesto, que se divide por 1 y por sí mismo, por lo tanto, es primo.

~~~ C
bool esPrimo(int contador)
{
  if (contador <= 1)
  {
    return false;
  }
  for (int i = 2; i <= contador / 2;i++)
  { 
    if (contador % i == 0)
    {
      return false;
    }
  }
  return true;
}
~~~



----------------------------------
# INVESTIGACION acerca del MOTOR CC - TRANSITOR NPN - SENSOR de FLEXION:

- MOTOR CC

El motor CC es una máquina que convierte energía eléctrica en mecánica, provocando un movimiento rotatorio, gracias a la acción de un campo magnético, aprovecha las fuerzas de atracción y repulsión de los polos con el fin de crear movimientos de rotación.
Sus partes fundamentales son: 

-Estator: carcasa de material ferromagnético y en su interior se encuentran distribuidos los polos inductores en número par con la intencion de que el roto gire.

-Entrehierro: espacio entre el estator y rotor, evita el desgaste de ambas piezas.

-Rotor: pieza central del motor, elaborado de acero y sicilio barnizado. Es la parte que gira y mantiene el movimiento en su propio eje, transformando la energía electromagnética en energía mecánica.

-Colector de legas: montada sobre el eje de giro y cuenta con varias legas fabricadas de cobre y separadas por mica.

-Escobillas: elementos que permiten el contacto eléctrico entra las delgas y el circuito de corriente continua. Hacen que la presión y el contacto se mantengan constantes.

El funcionamiento de un motor CC se basa en la fuerza que se produce sobre un conductor eléctrico recorrido por una intensidad de corriente eléctrica en el seno de un campo magnético, según la expresión de la ley de Lorentz.

F = B * L * I >>> F=fuerza en newton | B= induccion de campo magnetico (teslas) | L= longitud del conductor cortado por líneas de campo mágnetico (metros) | I = intensidad que recorre al conductor (amperios)



- TRANSITOR NPN 

Un transistor, también conocido como un BJT (Transistor de Unión Bipolar), es un dispositivo semiconductor impulsado por corriente, que puede ser utilizado para controlar el flujo de corriente eléctrica en la que una pequeña cantidad de corriente en el conductor base controla una mayor cantidad de corriente entre el Colector y el Emisor. Se pueden utilizar para amplificar una señal débil, como un oscilador o un interruptor.

¿Cómo funciona con el motor CC?

Un transistor es un componente electrónico que permite el paso de una corriente de salida dando una de entrada. Se activara cuando le demos corriente.

El transistor tiene tres patas: colector, base y emisor. Del colector al emisor pasara la corriente que queremos controlar asi que el colector lo conectaremos al lado positivo de nuestra alimentación; el emisor a nuetro motor. En cuanto a la base, la conectaremos a un extremo de la resistencia y por el otro extremo a algun pin PWM de nuestro arduino. Esto ayudará a controlar la velocidad del motor, debido se utiliza una pequeña corriente en la base del transistor para controlar una corriente mayor entre el colector y el emisor. Lo cual, en el proyecto, la hacemos variar con la variable 'n'.



- SENSOR de FLEXION

Un sensor de flexión o sensor de curvatura es un sensor diseñado específicamente para medir la cantidad de desviación o flexión. Este sensor funciona de manera similar a una resistencia variable porque cuando se tuerce, la resistencia cambiará. El cambio de resistencia puede depender de la linealidad de la superficie porque la resistencia será diferente cuando esté nivelada.



----------------------------------
# FUENTES:

- Fuente MOTOR CC:
  
  https://automatismoindustrial.com/curso-carnet-instalador-baja-tension/motores/1-3-5-motores-de-corriente-continua/1-3-5-2-principios-de-funcionamiento/
  
  https://es.wikipedia.org/wiki/Motor_de_corriente_continua
  
  
- Fuente TRANSITOR:

https://hetpro-store.com/TUTORIALES/transistor-npn/

https://sdindustrial.com.mx/blog/diferencia-transistor-npn-y-pnp/

- Fuente SENSOR de FLEXION:

https://cursos.mcielectronics.cl/2022/12/27/interfaz-del-sensor-flex-con-arduino/

# LINK PROYECTO SEGUNDA PARTE: 

https://www.tinkercad.com/things/3ucjSRs74In

----------------------------------

# Proyecto SPD: Tercera parte

El proyecto sigue manteniendo su objetivo, ser un contador que muestra mediante dos displays de 7 segmentos, números del 00 al 99 usando la técnica de la multiplexación con el mismo sitema que el proyecto anterior, con la diferencia de que se agrega un nuevo componente que controlará la velocidad que cambia el contador.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/4133c028-6a4b-4d46-8439-b448a1681524)


-----------------------------------
# Cambios realizados:

Componentes agregados:
- Fotorresistencia.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/29d7cb98-8bce-439b-ab76-2411f81d232b)


Se agregaron nuevos #define, variables, una función nueva y se han modificado partes del código.


------------------------------------

# FUNCIONES

Las siguientes FUNCIONES siguen manteniendo su estructura:
  - numerosContador(int)
  - prenderDisplay(int)
  - mostrarContador(int)
  - esPrimo(int)
  - cambiarOperacion(int, int, int)



Los #define se asocian a los pines y se crean variables.

~~~ C
#define MOTOR 3
#define SENSOR_FLEXION A3
#define SENSOR_LUZ A2

#define PULSADOR_MAS 5
#define PULSADOR_MENOS 4
#define SWITCH_CONTADOR 6

#define PIN_A 12
#define PIN_B 13
#define PIN_C 7
#define PIN_D 8
#define PIN_E 9
#define PIN_F 11
#define PIN_G 10

#define OFF 0

#define LEDUNIDAD A4
#define LEDDECENA A5

#define TIEMPODISPLAY 10
#define REVOLUCIONES 36

unsigned long tiempo;
unsigned long tiempoTranscurrido = 0;

int contador = 0;
int pulsador = 0;
int contadorPrimo = 0;

int sumarContador = 1;
int sumarAnterior = 1;

int restarContador = 1;
int restarAnterior = 1;

int velocidadMotor = 0;
int sensorFlexion = 0;
int sensorLuz = 0;

int n = 0;
int sumarORestar = 2;
int tiempoContador = 0;

int switchContador;
~~~



- setup()

Configuracion de los pines.

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
  pinMode(MOTOR, OUTPUT);
  pinMode(SENSOR_LUZ, INPUT_PULLUP);
  pinMode(SENSOR_FLEXION, INPUT_PULLUP);
  pinMode(PULSADOR_MAS, INPUT_PULLUP);
  pinMode(PULSADOR_MENOS, INPUT_PULLUP);
  pinMode(SWITCH_CONTADOR, INPUT);

  Serial.begin(9600);
}
~~~



- loop()

Se encarga de ejecutar el sistema.

Dentro de la fúncion:

Nos encontramos con variables usadas en el anterior proyecto.

'sensorLuz' lee los valores de entrada

Es usada la funcion 'cambiarTiempo()', encargada de cambiar el valor de la variable 'tiempoContador'.

~~~ C
void loop()
{
  tiempo = millis();
  pulsador = pulsadorEstado();
  sensorLuz= analogRead(SENSOR_LUZ);
  switchContador = digitalRead(SWITCH_CONTADOR);
  sensorFlexion = map(analogRead(SENSOR_FLEXION), 384, 783, 0, 7);
  n = 1 * REVOLUCIONES *  sensorFlexion;
  
  cambiarTiempo(sensorLuz);
  
  analogWrite(MOTOR, n);
  
  if (switchContador == 1)//primo
  {
    if (esPrimo(contador))
    {
      mostrarContador(contador);
      contadorPrimo = contador;
    }
    else
    {
      mostrarContador(contadorPrimo);
    }
  }
  else if(switchContador == 0) //no primo
  {
    mostrarContador(contador);
  }
  
  if (tiempo - tiempoTranscurrido > tiempoContador)
  {
    tiempoTranscurrido = tiempo;
    contador = cambiarOperacion(sumarORestar, contador, sensorFlexion);
  }
  
  if (contador > 99)
  {
    contador = contador - 100;
  }
  else if (contador < 0)
  {
    contador = contador + 100;
  }
  
  if (pulsador == PULSADOR_MAS)
  {
    sumarORestar = 0;
  }
  else if (pulsador == PULSADOR_MENOS)
  {
    sumarORestar = 1;
  }
  
  delay(TIEMPODISPLAY);
}
~~~



- cambiarTiempo(int, int)

Se encarga de retornar, dependiendo del valor que asuma 'sensor', de devolver cierto valor.

Dentro de la función:

Se usan bloques de 'if-else' con la finalidad de cambiar los valores de 'tiempoContador', dependiendo del valor de 'sensor'.

~~~ C
void cambiarTiempo(int sensor)
{
  if (sensor >= 10 && sensor <= 15)
  {
    tiempoContador = 200;
  }
  else if (sensor > 15 && sensor <= 25)
  {
    tiempoContador = 300;
  }
  else if (sensor > 25)
  {
    tiempoContador = 400;
  }
}
~~~


----------------------------------
# INVESTIGACION acerca de la FOTORRESISTENCIA


Una fotorresistencia es una resistencia, cuyo valor en ohmios, varía ante las variaciones de la luz. Estas resistencias están construidas con un material sensible a la luz, de tal manera que cuando la luz incide sobre su superficie, el material sufre una reacción química, alterando su resistencia eléctrica.

Para entender el funcionamiento de la fotorresistencia, es importante que sepamos de qué se compone este dispositivo electrónico. Lo que hace que el fotorresistor funcione dependiendo de la cantidad de luz que incide sobre él, es que está compuesto principalmente de sulfuro de cadmio (CdS). Este componente químico se caracteriza por ser semiconductor, y es el responsable de hacer que la resistencia de los dispositivos varíen, dependiendo de la cantidad e intensidad de la luz a la que son expuestos.

----------------------------------
# FUENTES:

- Fuente FOTORRESISTENCIA:

https://www.ehu.eus/es/web/tutorial-myrio/7.-fotoerresistentzia



# LINK PROYECTO TERCERA PARTE:

https://www.tinkercad.com/things/bmz2OQ4oxsI


----------------------------------
# Proyecto SPD: Cuarta parte

La cuarta parte del proyecto sigue teniendo el mismo objetivo que los anteriores pero, con la diferencia de que al apretar el switch, se apague el sistema.

![imagen](https://github.com/BARBOZAMATIAS5/proyecto_spd/assets/117691193/986c79df-1330-40c2-8e7a-953560e99cc4)


-----------------------------------
# Cambios realizados:

- Se elimina la función esPrimo().
- Se cambia el funcionamiento del switch, haciendo que apague o prenda el sistema.

------------------------------------

# FUNCIONES

Las siguientes FUNCIONES siguen manteniendo su estructura:
  - setup()
  - numerosContador(int)
  - prenderDisplay(int)
  - mostrarContador(int)
  - cambiarOperacion(int, int, int)
  - cambiarTiempo(int)



- loop ()

Se encarga del funcionamiento del código.

Dentro de la función:

El uso de switchSistema y la funcion 'if-else', servirá para almacenar dentro de uno, el funcionamiento completo del sistema y, en el otro, simplemente cambiar algunas variables a su estado inicial.

~~~ C
void loop()
{
  switchSistema = digitalRead(SWITCH_CONTADOR);
  
  analogWrite(MOTOR, n);
  
  if (switchSistema == 1)//apagado
  {
    n = 0;
    contador = 0;
    mostrarContador(contador);
    sumarORestar = 2;
  }
  
  else if(switchSistema == 0) //encendido
  {
    tiempo = millis();
  	sensorLuz= analogRead(SENSOR_LUZ);
    pulsador = pulsadorEstado();
    sensorFlexion = map(analogRead(SENSOR_FLEXION), 384, 783, 0, 7);
  	tiempoContador = cambiarTiempo(tiempoContador, sensorLuz);
  
    n = 1 * REVOLUCIONES *  sensorFlexion;
    
    mostrarContador(contador);
    
    if (tiempo - tiempo_transcurrido > tiempoContador)
    {
      tiempo_transcurrido = tiempo;
      contador = cambiarOperacion(sumarORestar, contador, sensorFlexion);
    }

    if (contador > 99)
    {
      contador = contador - 100;
    }
    else if (contador < 0)
    {
      contador = contador + 100;
    }

    if (pulsador == PULSADOR_MAS)
    {
      sumarORestar = 0;
    }
    else if (pulsador == PULSADOR_MENOS)
    {
      sumarORestar = 1;
    }
  }

  delay(TIEMPODISPLAY);
}
~~~



----------------------------------
# LINK PROYECTO CUARTA PARTE:

https://www.tinkercad.com/things/dcDukXcITqy
