### interfaz2
1.[Hola Mundo](https://github.com/Aura0403/interfaz2?tab=readme-ov-file#ejercicio-n-1-arduino-hola-mundo)<br>
2.[Led Parpadeante](https://github.com/Aura0403/interfaz2?tab=readme-ov-file#ejercicio-n2-led-parpadeante)<br>
3.[Led Pulsador](https://github.com/Aura0403/interfaz2?tab=readme-ov-file#ejercicio-n3-led-pulsador)<br>
4.[Led con potenciometro](https://github.com/Aura0403/interfaz2?tab=readme-ov-file#ejercicio-n4-led-con-potenciometro)<br>
5.[Semaforo en Arduino](https://github.com/Aura0403/interfaz2?tab=readme-ov-file#ejercicio-n5-semaforo-en-arduino)<br>
6.[Potenciometro+Arduino](https://github.com/Aura0403/interfaz2?tab=readme-ov-file#ejercicio-6-elipse-interactivo-controlar-un-circulo-en-processing-mediante-un-potenciometro-conectado-a-un-arduino-uno)<br>
7.[Arduino+boton+processing](https://github.com/Aura0403/interfaz2?tab=readme-ov-file#ejercicio-n-7-arduino--boton-processing)<br>
8.[Arduino+boton+potenciometro+processing](https://github.com/Aura0403/interfaz2?tab=readme-ov-file#ejercicio-8-arduino--bot%C3%B3n--potenciometro--processing)<br>
9.[For if else](https://github.com/Aura0403/interfaz2?tab=readme-ov-file#ejercicio-9-for-if-else)<br>
10.[Botonera](https://github.com/Aura0403/interfaz2?tab=readme-ov-file#ejercicio-10-botonera)<br>
11.[Entrega](https://github.com/Aura0403/interfaz2?tab=readme-ov-file#ejercicio-con-nota-arduino--bot%C3%B3n--potenciometro--processing-modificado-colores-y-formas)<br>
12.[Cuerpo, vídeo, sensor sharp](https://github.com/Aura0403/interfaz2/blob/main/README.md#ejercicio-12-cuerpo-v%C3%ADdeo-sensor-sharp)<br>









### Ejercicio n° 1 Arduino: "Hola mundo"

```js
void setup() {
  Serial.begin(9600); // Inicia la comunicación serie a 9600 bps
  Serial.println("Hola, Mundo!"); // Envía "Hola, Mundo!" al monitor serie
}

void loop() { 
  // No es necesario poner nada en el loop para este ejemplo
}
```
### Ejercicio n°2: led parpadeante
```js
void setup() {  // Configuración inicial (ej: pines como entrada/salida)
  pinMode(13, OUTPUT);  // Pin 13 como salida
  pinMode(8, OUTPUT);
}

void loop() {   // Se repite infinitamente
  digitalWrite(13, HIGH);  // Encender LED
  delay(1000);             // Esperar 1 segundo
  digitalWrite(13, LOW);   // Apagar LED
  //delay(1000);            // Esperar 1 segundo
  digitalWrite(8, HIGH);
  delay(1000);
  digitalWrite(8, LOW);
  delay(1000);
}
```
<img 
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/led%20parpadeante.png" width="1024" height="550" />
<img 
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/led%20parpadeante%20fisico.jpeg" width="1024" height="550" />


### Ejercicio n°3: Led pulsador
```js
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
}
void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
  } else {
    digitalWrite(13, LOW);
  }
}
```
<img
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/led%20pulsador.png" width="1024" height="550" />

<img
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/led%20pulsador.jpeg" width="1024" height="550" />
### Ejercicio n°4: led con potenciometro
```js
void setup() {
  pinMode(9, OUTPUT);  // Pin PWM (símbolo ~)
}
void loop() {
  int valor = analogRead(A0);           // Leer potenciómetro (0-1023)
  int brillo = map(valor, 0, 1023, 0, 255);  // Convertir a rango PWM
  analogWrite(9, brillo);               // Ajustar brillo
}
```
<img
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/led%20ponteciometro.png" width="1024" height="550" />
<img
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/potenciometo%20fisico.jpeg" width="1024" height="550" />

### Ejercicio n°5: Semaforo en Arduino
```js
// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  //digitalWrite(LED_4, LOW);   // Verde peatones apagado
  //digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(2000); // 2 segundos
}
```
<img src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/semaforo.png" width="1024" height="550" />

<img src="http://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/semaforo%20fisico.jpeg" width="1024" height="550" />

### Ejercicio semaforo con alteraccion luz peatonal verde
```js
// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
  digitalWrite(LED_4, HIGH);// Verde peatones encendido
  delay(1000); // 5 segundos
  digitalWrite(LED_4, LOW);
  delay(1000);
  digitalWrite(LED_4, HIGH);// Verde peatones encendido
  delay(1000); // 5 segundos
  digitalWrite(LED_4, LOW);
  delay(1000);
  digitalWrite(LED_1, LOW);

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(2000); // 2 segundos
}
```
### Ejercicio 6: Elipse Interactivo: controlar un circulo en Processing mediante un potenciometro conectado a un Arduino UNO.

```js
import processing.serial.*;

Serial myPort;  // Crear objeto de la clase Serial
static String val;    // Datos recibidos desde el puerto serial
int sensorVal = 0;

void setup()
{
  background(0); 
  //fullScreen(P3D);
   size(1080, 720);
   noStroke();
  noFill();
  String portName = "COM3";// Cambia el número (en este caso) para que coincida con el puerto correspondiente conectado a tu Arduino. 

  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort = new Serial(this, Serial.list()[0], 9600);

}

void draw()
{
  if ( myPort.available() > 0) {  // Si hay datos disponibles,
  val = myPort.readStringUntil('\n'); 
  try {
   sensorVal = Integer.valueOf(val.trim());
  }
  catch(Exception e) {
  ;
  }
  println(sensorVal); // léelos y guárdalos en vals!
  }  
 //background(0);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 0 y 175
  float c = map(sensorVal, 0, width, 0, 400);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 40 y 300
  float d = map(sensorVal, 0, width, 40,500);
  fill(255, c, 0);
  ellipse(width/2, height/2, d, d); 
  ellipse(width/6, height/5, d, d);
   ellipse(width/6, height/1, d, d);
    ellipse(width/1, height/5, d, d);
}
```
<img 
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/Ejercicio%206.png" width="1024" height="550" />

## Ejercicio n° 7: Arduino + boton+ processing

### codigo arduino

```js
int buttonPin = 2;  // Pin del botón
int buttonState = 0;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {   // Botón presionado
    Serial.println(1);        // Enviar un "1" a Processing
    delay(200);               // Evitar rebotes
  }
}
```

### codigo processing

```js
import processing.serial.*;

Serial myPort;
ArrayList<PVector> circles; 

void setup() {
  size(1920, 1080);
  background(0);
  
  // Ajusta el nombre del puerto según tu Arduino
  println(Serial.list());
  myPort = new Serial(this, "COM3", 9600);
  //myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<PVector>();
}

void draw() {
  //background(0);
  
  // Dibujar círculos almacenados
  fill(random(7), random (224), random (7, 200), 6);
  //noStroke();
  stroke(250, 250, 250, 50);
  for (PVector c : circles) {
    ellipse(c.x, c.y, random (30, 200), random(30, 330));
  }
  
  // Revisar si llega algo de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.equals("1")) {
        // Cada vez que se aprieta el botón, agregar un círculo en posición aleatoria
        circles.add(new PVector(random(width), random(height)));
      }
    }
  }
}
```
### primer boceto
<img 
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/Ejercicio%207%20arduino%20boton%20processing.png" height="550" />
### segundo boceto definitivo
<img 
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/ejercicio%207%20arduino%20boton%20processing%202.png" height="550" />

## ejercicio 8: Arduino + botón + potenciometro + Processing

### codigo arduino

```js

int buttonPin = 2;       // Pin del botón
int potPin = A0;         // Pin del potenciómetro
int buttonState = 0;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {   // Botón presionado
    int potValue = analogRead(potPin);   // 0 - 1023
    Serial.print("BTN,");     // etiqueta para Processing
    Serial.println(potValue); // mando el valor junto con el evento
    delay(200);               // debounce simple
  }
}
```

### codigo processing

```js

import processing.serial.*;

Serial myPort;
ArrayList<CircleData> circles; 

void setup() {
  size(1200, 720);
  background(0);
  
  // Ajusta el puerto según tu Arduino
  println(Serial.list());
  myPort = new Serial(this, "COM3", 9600);
  //myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<CircleData>();
}

void draw() {
  //background(0);
  
  // Dibujar todos los círculos guardados
  //fill(0, 150, 255);
  //noStroke();
  fill(random (247), random(5),random (196,200), 30);
  stroke(247, 252, 252);
  for (CircleData c : circles) {
    ellipse(c.x, c.y, random(c.size), random (c.size));
  }
  
  // Leer datos de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.startsWith("BTN")) {
        // Extraer el valor del potenciómetro
        String[] parts = split(val, ',');
        if (parts.length == 2) {
          float potVal = float(parts[1]);
          float circleSize = map(potVal, 0, 1023, 10, 100); // tamaño 10-100 px
          circles.add(new CircleData(random(width), random(height), circleSize));
        }
      }
    }
  }
}

// Clase para guardar datos de cada círculo
class CircleData {
  float x, y, size;
  CircleData(float x, float y, float size) {
    this.x = x;
    this.y = y;
    this.size = size;
  }
}
```
### primer boceto
<img 
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/ejercico%208%20arduino%20boton%20pocentiometro%20procesing.png" height="550" />

### boceto final y definitivo
<img 
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/ejercicio%208%20arduino%20boton%20potenciometro%20processing2.png" height="550" />

### Ejercicio 9: for if else

```js
int leds[] = {2, 3, 4, 5}; // Creamos un arreglo con los pines donde van conectados los LEDs

void setup() {
  // Esta función corre solo una vez al iniciar Arduino
  for (int i = 0; i < 4; i++) {         // Recorre el arreglo desde i = 0 hasta i = 3
    pinMode(leds[i], OUTPUT);           // Configura cada pin del arreglo como salida (para controlar LEDs)
  }
}

void loop() {
  // Esta función corre en bucle infinito
  for (int i = 0; i < 4; i++) {         // Recorre los 4 LEDs, uno por uno
    if (i % 3 == 0) {                   // Si el índice es par (0, 2)...
      digitalWrite(leds[i], HIGH);      // Enciende el LED correspondiente
    } else {                            // Si el índice es impar (1, 3)...
      digitalWrite(leds[i], LOW);       // Apaga el LED correspondiente
    }
    delay(500);                         // Espera 0,5 segundos antes de pasar al siguiente
  }

```
<img 
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/for%20if%20else.png" height="550" />

  ### Ejercicio 10: Botonera.

  #### Codigo arduino

  ```js
// --- Configuración de botones ---
const int numButtons = 3;
const int buttonPins[numButtons] = {2, 4, 7};
const int ledButtonPins[numButtons] = {9, 10, 11}; // LEDs botones

// --- Configuración de potenciómetros ---
const int numPots = 2;
const int potPins[numPots] = {A0, A1};
const int ledPotPins[numPots] = {3, 5}; // LEDs PWM

// Variables de estados previos
int lastButtonState[numButtons];
int lastPotValue[numPots];

void setup() {
  Serial.begin(9600);

  // Configurar botones y LEDs
  for (int i = 0; i < numButtons; i++) {
    pinMode(buttonPins[i], INPUT_PULLUP);
    pinMode(ledButtonPins[i], OUTPUT);
    lastButtonState[i] = digitalRead(buttonPins[i]);
  }

  // Configurar LEDs de potenciómetros
  for (int i = 0; i < numPots; i++) {
    pinMode(ledPotPins[i], OUTPUT);
    lastPotValue[i] = analogRead(potPins[i]);
  }
}

void loop() {
  // Leer y enviar botones
  for (int i = 0; i < numButtons; i++) {
    int buttonState = digitalRead(buttonPins[i]);

    // LED se enciende cuando botón está presionado
    digitalWrite(ledButtonPins[i], buttonState == LOW ? HIGH : LOW);

    if (buttonState != lastButtonState[i]) {  // enviar cambios
      Serial.print("B");
      Serial.print(i); 
      Serial.print(":");
      Serial.println(buttonState);
      lastButtonState[i] = buttonState;
    }
  }

  // Leer y enviar potenciómetros
  for (int i = 0; i < numPots; i++) {
    int potValue = analogRead(potPins[i]); // 0–1023
    int pwmValue = potValue / 4;           // 0–255

    // Ajustar LED según valor
    analogWrite(ledPotPins[i], pwmValue);

    if (abs(pwmValue - lastPotValue[i]) > 2) { // evitar ruido
      Serial.print("P");
      Serial.print(i);
      Serial.print(":");
      Serial.println(pwmValue);
      lastPotValue[i] = pwmValue;
    }
  }

  delay(10);
}
```

#### Codigo Processing.

```
// Importamos librería para comunicación serial
import processing.serial.*;
// Importamos librería Minim para manejar audio
import ddf.minim.*;

// Declaramos el objeto serial para comunicarnos con Arduino
Serial myPort;
// Objeto principal de Minim
Minim minim;
// Array de reproductores de audio (3 pistas)
AudioPlayer[] players;
// Variable para guardar el índice de la pista que está sonando
int currentTrack = -1;  // -1 significa que no hay pista activa al inicio

void setup() {
  size(400, 200); // Ventana de 400x200 píxeles
  
  // --- Configuración del puerto serial ---
  printArray(Serial.list()); // Muestra en consola la lista de puertos disponibles
  myPort = new Serial(this, Serial.list()[0], 9600); // Abrimos el primer puerto de la lista a 9600 baudios
  
  // --- Configuración de audio ---
  minim = new Minim(this); // Inicializamos Minim
  players = new AudioPlayer[3]; // Creamos un array de 3 reproductores
  
  // Cargamos los 3 archivos de audio desde la carpeta "data"
  players[0] = minim.loadFile("audio1.mp3", 2048); 
  players[1] = minim.loadFile("audio2.mp3", 2048); 
  players[2] = minim.loadFile("audio3.mp3", 2048); 
}

void draw() {
  background(0); // Fondo negro
  fill(255);     // Color blanco para el texto
  textSize(16);  // Tamaño del texto
  
  // Mostramos en pantalla qué botón está activo
  text("Botón actual: " + (currentTrack == -1 ? "ninguno" : currentTrack), 20, 40);
}

void serialEvent(Serial myPort) {
  // Leemos la cadena que llega desde Arduino hasta el salto de línea
  String inString = trim(myPort.readStringUntil('\n'));
  
  // Si no llega nada, salimos
  if (inString == null) return;

  // --- Si el mensaje recibido empieza con "B" significa que es un botón ---
  if (inString.startsWith("B")) {
    // Quitamos la letra "B" y separamos el mensaje en partes (ejemplo "0:0")
    String[] parts = split(inString.substring(1), ':');
    
    // Si realmente recibimos dos partes (índice y estado)
    if (parts.length == 2) {
      int buttonIndex = int(parts[0]); // Número del botón (0,1,2)
      int state = int(parts[1]);       // Estado del botón (0 = presionado, 1 = suelto)
      
      // Si el botón fue presionado (LOW = 0 en Arduino)
      if (state == 0) { 
        playTrack(buttonIndex); // Llamamos a la función para reproducir la pista correspondiente
      }
    }
  }
}

// --- Función que reproduce una pista según el botón ---
void playTrack(int index) {
  // Si ya había una pista sonando, la pausamos y la rebobinamos al inicio
  if (currentTrack != -1 && players[currentTrack].isPlaying()) {
    players[currentTrack].pause();
    players[currentTrack].rewind();
  }
  
  // Reproducimos en bucle la pista seleccionada
  players[index].loop();
  
  // Actualizamos la variable para saber cuál es la pista activa
  currentTrack = index;
}
```

<img 
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/botonera.png" height="550" /> 


<img 
src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/botonera%20en%20fisico.jpeg" height="550" /> 

## Ejercicio con nota: Arduino + botón + potenciometro + Processing modificado (colores y formas)
Este ejercicio muestra como resultado una visual de formas a traves de codigos que trabajan en conjunto entre Arduino y Processing, es una visual interactiva que funciona a traves de un potenciometro y boton, al momento de apretar el boton, este manda la señal que permite que aparezcan figuras circulares de tamaño aleatorio ya que ocupo un random en el ancho que arroja tamaño de 0 a 300 y el alto fue respecto al tamaño base (c.size), y el potenciometro al ocuparlo genera cambios en el alto de las figuras, las hace mas largas o mas cortas, tambien hice cambios con respecto a los colores y fondo de la visual.
Me ayude con Inteligencia articifial al momento de necesitar orientacion para entender el cambio de la estetica visual y entender de mejor manera el funcionamiento general del circuito.


### Codigo arduino

```js

int buttonPin = 2;       // Pin del botón
int potPin = A0;         // Pin del potenciómetro
int buttonState = 0;


void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}


void loop() {
  buttonState = digitalRead(buttonPin);


  if (buttonState == HIGH) {   // Botón presionado
    int potValue = analogRead(potPin);   // 0 - 1023
    Serial.print("BTN,");     // etiqueta para Processing
    Serial.println(potValue); // mando el valor junto con el evento 
    delay(200);               // debounce simple
  }
}
```
### Codigo processing sin modificar

```js

import processing.serial.*;

Serial myPort;
ArrayList<CircleData> circles; 

void setup() {
  size(1200, 720);
  background(0);
  
  // Ajusta el puerto según tu Arduino
  println(Serial.list());
  myPort = new Serial(this, "COM3", 9600);
  //myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<CircleData>();
}

void draw() {
  //background(0);
  
  // Dibujar todos los círculos guardados
  //fill(0, 150, 255);
  //noStroke();
  fill(random (247), random(5),random (196,200), 30);
  stroke(247, 252, 252);
  for (CircleData c : circles) {
    ellipse(c.x, c.y, random(c.size), random (c.size));
  }
  
  // Leer datos de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.startsWith("BTN")) {
        // Extraer el valor del potenciómetro
        String[] parts = split(val, ',');
        if (parts.length == 2) {
          float potVal = float(parts[1]);
          float circleSize = map(potVal, 0, 1023, 10, 100); // tamaño 10-100 px
          circles.add(new CircleData(random(width), random(height), circleSize));
        }
      }
    }
  }
}
// Clase para guardar datos de cada círculo
class CircleData {
  float x, y, size;
  CircleData(float x, float y, float size) {
    this.x = x;
    this.y = y;
    this.size = size;
  }
}
```

### Codigo processing modificado

```js

import processing.serial.*;  

Serial myPort;
ArrayList<CircleData> circles;  

void setup() {
  size(1200, 800);               //  CAMBIADO: altura aumentada de 720 a 800, para que la ventana sea mas alta y puedan aparecer mas circulos en ella.
  background(74, 0, 121);        // CAMBIADO: color de fondo cambiado a morado, ya que esta rojo y azul presente y el verde esta en 0.
  
  println(Serial.list());       
  myPort = new Serial(this, "COM3", 9600);  
  
  circles = new ArrayList<CircleData>();   
}

void draw() {
  //background(0);              
  
  // Colores aleatorios para los círculos
  fill(random (240), random(136), random (89), 24);   //  CAMBIADO: color más cálido y más transparente ocupando tonalidades aleatorias de colores rojos, verdes y azules, tambienle agregue mas transparencia bajandolo de 30 a 24.
  
  stroke(52, 240, 24);                                //  CAMBIADO: contorno verde claro
  
  for (CircleData c : circles) {
    ellipse(c.x, c.y, random(300), random(c.size));   //  CAMBIADO: ancho aleatorio hasta 300 provocando figuras mas desformes o anchas, antes la altura y el ancho dependian del mismo valor.
  }

  // Leer datos desde Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.startsWith("BTN")) {
        String[] parts = split(val, ',');
        if (parts.length == 2) {
          float potVal = float(parts[1]);
          float circleSize = map(potVal, 0, 1023, 10, 100);
          circles.add(new CircleData(random(width), random(height), circleSize));
        }
      }
    }
  }
}

// Clase que guarda los datos del círculo (posición y tamaño)
class CircleData {
  float x, y, size;
  CircleData(float x, float y, float size) {
    this.x = x;
    this.y = y;
    this.size = size;
  }
}
```

## Regisro resultado de processing

<img src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/registro%20processing%20entrega%201.png" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/registro%20processing%20entrega%202.png" width="1024" height="550" />
<img src="http://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/registro%20processing%20entrega%203.png" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/registro%20processing%204.png" width="1024" height="550" />

## Registro fisico
<img src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/regiistro%20fisico%20entrega%201.jpeg" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/registro%20fisico%20entrega%202.jpeg" width="1024" height="550" />
<img src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/registro%20fisico%20entrega%203.jpeg" width="1024" height="550" />

### Ejercicio 12: Cuerpo, vídeo, sensor sharp.

#### Codigo Arduino:

```js
// --- Sensor Sharp conectado al pin A0 ---
int sensorPin = A0;
int valor;

void setup() {
  Serial.begin(9600);
}

void loop() {
  valor = analogRead(sensorPin);
  Serial.println(valor);
  delay(50); // envío cada 50 ms
}
```

#### Codigo Processing:

```js
// --- Librerías necesarias ---
import processing.serial.*;
import processing.video.*;

// --- Variables de cámara y serial ---
Capture cam;
Serial myPort;

// --- Variables del sensor ---
float sensorValue = 0;
float suavizado = 0;

// --- Parámetros para detección de silueta ---
float umbral = 100; // controla el contraste para definir la silueta

void setup() {
  size(1280, 720);
  background(0);
  
  // --- Inicializar cámara ---
  String[] cameras = Capture.list();
  if (cameras.length == 0) {
    println("No se encontró cámara.");
    exit();
  } else {
    println("Cámara encontrada: " + cameras[0]);
    cam = new Capture(this, cameras[0]);
    cam.start();
  }
  
  // --- Inicializar puerto serie (Arduino) ---
  // Puedes ver la lista de puertos con println(Serial.list());
  String portName = Serial.list()[0]; 
  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort = new Serial(this, portName, 9600);
}

void draw() {
  background(0);
  
  // --- Leer datos del sensor ---
  while (myPort.available() > 0) {
    String inString = trim(myPort.readStringUntil('\n'));
    if (inString != null) {
      sensorValue = float(inString);
      suavizado = lerp(suavizado, sensorValue, 0.1);
    }
  }
  
  // --- Mapear los valores del sensor ---
  float escala = map(suavizado, 0, 1023, 1.5, 0.5); // tamaño de la silueta
  float alpha = map(suavizado, 0, 1023, 255, 80);   // opacidad según distancia
  
  // --- Captura de video ---
  if (cam.available()) {
    cam.read();
  }

  // --- Dibujar silueta desde la cámara ---
  cam.loadPixels();
  loadPixels();
  
  for (int y = 0; y < cam.height; y++) {
    for (int x = 0; x < cam.width; x++) {
      int loc = x + y * cam.width;
      color c = cam.pixels[loc];
      float brillo = brightness(c);
      
      // Si el brillo es menor que el umbral, dibujamos píxel blanco (silueta)
      if (brillo < umbral) {
        int px = int(x * escala);
        int py = int(y * escala);
        if (px < width && py < height) {
          stroke(255, alpha);
          point(px, py);
        }
      }
    }
  }
}
```
### Registro fisico

<img src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/Cuerpo%2C%20v%C3%ADdeo%2C%20sensor%20sharp%20registro%20fisico.jpg" width="1024" height="550" />

### Registro processing

<img src="https://raw.githubusercontent.com/Aura0403/interfaz2/refs/heads/main/Img/cuerpo%2C%20video%2C%20sensor%2C%20sharp%2C%20registro%20processing.png" width="1024" height="550" />

































  

