# INTERFAZIII

1. [Hola Mundo](#ejercicio-n1-arduino-hola-mundo)<br>
2. [Led Parpadeante](#ejercicio-n2-arduino-led-parpadeante)<br>
3. [Control por Pulsador](#ejercicio-n3-arduino-control-por-pulsador)<br>
4. [Led con Potenciómetro](#ejercicio-n4-arduino-led-con-potenci%C3%B3metro)<br>
5. [Semáforo](#ejercicio-n5-arduino-sem%C3%A1foro)<br>
6. [Potenciómetro + Processing](#ejercicio-n6-processing-potenci%C3%B3metro)<br>


### Ejercicio n°1 Arduino: "Hola Mundo"

```js
void setup() {
  Serial.begin(9600); // Inicia la comunicación serie a 9600 bps
  Serial.println("Hola, ñññññññ"); // Envía "Hola, Mundo!" al monitor serie
}

void loop() {
  // No es necesario poner nada en el loop para este ejemplo
}
```
<img
src="https://raw.githubusercontent.com/maaaaay-beepbeep/INTERFAZII/refs/heads/main/img/hola%20mundo.png"/>


### Ejercicio n°2 Arduino: "Led Parpadeante"

```js
void setup() {  // Configuración inicial (ej: pines como entrada/salida)
  pinMode(13, OUTPUT);  // Pin 13 como salida
}

void loop() {   // Se repite infinitamente
  digitalWrite(13, HIGH);  // Encender LED
  delay(1000);             // Esperar 1 segundo
  digitalWrite(13, LOW);   // Apagar LED
  delay(1000);             // Esperar 1 segundo
}
```
<img
src="https://raw.githubusercontent.com/maaaaay-beepbeep/INTERFAZII/refs/heads/main/img/led%20parpadeante.png"/>


### Ejercicio n°3 Arduino: "Control por Pulsador"

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
src="https://raw.githubusercontent.com/maaaaay-beepbeep/INTERFAZII/refs/heads/main/img/control%20por%20pulsador.png"/>


### Ejercicio n°4 Arduino: "LED con Potenciómetro"

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
src="https://raw.githubusercontent.com/maaaaay-beepbeep/INTERFAZII/refs/heads/main/img/led%20con%20potenciador.png"/>


### Ejercicio n°5 Arduino: "Semáforo"

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
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(2000); // 2 segundos
}
```
<img
src="https://raw.githubusercontent.com/maaaaay-beepbeep/INTERFAZII/refs/heads/main/img/sem%C3%A1foro.png"/>







Arduino como Periférico

### Ejercicio n°? Arduino: "Semáforo con led" en físico

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
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  //delay(500); // 2 segundos
}
```


### Ejercicio n°? Arduino: "Semáforo parpadeante con led" en físico

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
  digitalWrite(LED_4, LOW);
  delay(250); // 5 segundos digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(250); // 5 segundos
  digitalWrite(LED_4, LOW);
  delay(250); // 5 segundos
   digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(250); // 5 segundos
  digitalWrite(LED_4, LOW);
  delay(250); // 5 segundos digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(250); // 5 segundos
  digitalWrite(LED_4, LOW);
  delay(250); // 5 segundos
  

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(2000); // 2 segundos
}
```


### Ejercicio n°6 Processing: Potenciómetro

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
  fill(128, c, 255);
  ellipse(width/3, height/3, d, d);
  fill(128, c, 128);
  ellipse(width/1, height/2, d, d);
  fill(0, c, 128);
  ellipse(width/4, height/4, d, d);
  
}
```

### Ejercicio n°7 Processing: Pulsador

```js

### Ejercicio n°8 Processing: Botón + Potenciómetro

```js

### Ejercicio n°9 Arduino: If / else

```js

### Ejercicio n°10 Processing: Botón

```js

### Ejercicio n° 10? Arduino: Botonera

```js

### Entrega n°1: Semáforo en Arduino + modificaciones

```js
enlace de código con sus modificaciones: https://docs.google.com/document/d/1LgkIKUsXWpTZZkGF7ONNi1rBaF-qCVB6cX15AuuwSvw/edit?usp=sharing
```

```js
// Semáforo de Autos y Peatones

// Pines de los LEDs
const int LED_ROJO_AUTOS = 6;
const int LED_AMARILLO_AUTOS = 7;
const int LED_VERDE_AUTOS = 8;

const int LED_VERDE_PEATONES = 9;
const int LED_ROJO_PEATONES = 10;

void setup() {
  // Configuramos todos los pines como salidas
  pinMode(LED_ROJO_AUTOS, OUTPUT);
  pinMode(LED_AMARILLO_AUTOS, OUTPUT);
  pinMode(LED_VERDE_AUTOS, OUTPUT);
  pinMode(LED_VERDE_PEATONES, OUTPUT);
  pinMode(LED_ROJO_PEATONES, OUTPUT);
}

void loop() {
  // 🚦 FASE 1: Autos en verde, peatones en rojo
  digitalWrite(LED_VERDE_AUTOS, HIGH);
  digitalWrite(LED_ROJO_AUTOS, LOW);
  digitalWrite(LED_AMARILLO_AUTOS, LOW);

  digitalWrite(LED_VERDE_PEATONES, LOW);
  digitalWrite(LED_ROJO_PEATONES, HIGH);
  delay(5000);

  // 🚦 FASE 2: Autos en amarillo, rojo peatones parpadeando
  digitalWrite(LED_VERDE_AUTOS, LOW);
  digitalWrite(LED_AMARILLO_AUTOS, HIGH);

  for (int i = 0; i < 4; i++) {
    digitalWrite(LED_ROJO_PEATONES, LOW);
    delay(250);
    digitalWrite(LED_ROJO_PEATONES, HIGH);
    delay(250);
     digitalWrite(LED_ROJO_PEATONES, LOW);
    delay(250);
    digitalWrite(LED_ROJO_PEATONES, HIGH);
    delay(250);
     digitalWrite(LED_ROJO_PEATONES, LOW);
    delay(250);
    digitalWrite(LED_ROJO_PEATONES, HIGH);
    delay(250);
  }

  digitalWrite(LED_AMARILLO_AUTOS, LOW);

  // 🚦 FASE 3: Autos en rojo, peatones en verde
  digitalWrite(LED_ROJO_AUTOS, HIGH);
  digitalWrite(LED_VERDE_PEATONES, HIGH);
  digitalWrite(LED_ROJO_PEATONES, LOW);
  delay(5000);

  // Parpadeo del verde de peatones
  for (int i = 0; i < 4; i++) {
    digitalWrite(LED_VERDE_PEATONES, LOW);
    delay(250);
    digitalWrite(LED_VERDE_PEATONES, HIGH);
    delay(250);
    digitalWrite(LED_VERDE_PEATONES, LOW);
    delay(250);
    digitalWrite(LED_VERDE_PEATONES, HIGH);
    delay(250);
    digitalWrite(LED_VERDE_PEATONES, LOW);
    delay(250);
    digitalWrite(LED_VERDE_PEATONES, HIGH);
    delay(250);
  }
}
```

### Ejercicio n°11 Arduino: Sensor de distancia

```js

### Ejercicio n°11? Processing: ´´

```js

### Ejercicio n°12 Processing: Vídeo Ascii

```js

### Ejercicio n°13 Arduino: Vídeo Glitch

```js

### Ejercicio n°14 Arduino: Sensor de humedad

```js

### Ejercicio n°15 Arduino: Cuerpo, Vídeo y Sensor Sharp

```js
void setup() {
  Serial.begin(9600);
}

void loop() {
  int potValue = analogRead(A0);
  Serial.println(potValue);
  delay(20);
}
```


### Ejercicio n°15? Processing: ´´

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

### Ejercicio n°16 Arduino: Promedio de imágenes

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


### Ejercicio n°16 Processing: ´´

```js
import processing.serial.*;

Serial myPort;
PImage[] imgs;
int numImages = 3;
PImage avgImg;
float mixAmount = 0;

void setup() {
  size(800, 600);
  println(Serial.list());
  
  //Cambia el índice según tu puerto (0, 1, 2, etc.)
  myPort = new Serial(this, Serial.list()[0], 9600);
  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort.bufferUntil('\n');

  // Cargar imágenes
  imgs = new PImage[numImages];
  imgs[0] = loadImage("img1.jpg");
  imgs[1] = loadImage("img2.jpg");
  imgs[2] = loadImage("img3.jpg");

  avgImg = createImage(imgs[0].width, imgs[0].height, RGB);
}

void draw() {
  // Dibujar la imagen promedio según el valor del potenciómetro
  background(0);
  calcAverage(mixAmount);
  image(avgImg, 0, 0, width, height);
  
  fill(255);
  textSize(20);
  text("Mezcla: " + nf(mixAmount, 1, 2), 20, height - 20);
}

void serialEvent(Serial p) {
  String val = p.readStringUntil('\n');
  if (val != null) {
    val = trim(val);
    float sensor = float(val);
    mixAmount = map(sensor, 0, 1023, 0, 1); // 0 a 1
  }
}

void calcAverage(float t) {
  avgImg.loadPixels();

  for (int i = 0; i < avgImg.pixels.length; i++) {
    color c1 = imgs[0].pixels[i];
    color c2 = imgs[1].pixels[i];
    color c3 = imgs[2].pixels[i];

    // Promedio ponderado según el potenciómetro
    float r = red(c1)*(1-t) + red(c2)*t*0.5 + red(c3)*t*0.5;
    float g = green(c1)*(1-t) + green(c2)*t*0.5 + green(c3)*t*0.5;
    float b = blue(c1)*(1-t) + blue(c2)*t*0.5 + blue(c3)*t*0.5;

    avgImg.pixels[i] = color(r, g, b);
  }
  avgImg.updatePixels();
}
```


### Entrega n°2: CHROMA.S

```js
Código Arduino:

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
    digitalWrite(ledButtonPins[i], buttonState == LOW ? HIGH : LOW);

    if (buttonState != lastButtonState[i]) {
      Serial.print("B");
      Serial.print(i);
      Serial.print(":");
      Serial.println(buttonState);
      lastButtonState[i] = buttonState;
    }
  }

  // Leer y enviar potenciómetros
  for (int i = 0; i < numPots; i++) {
    int potValue = analogRead(potPins[i]);
    int pwmValue = potValue / 4;

    analogWrite(ledPotPins[i], pwmValue);

    if (abs(pwmValue - lastPotValue[i]) > 2) {
      Serial.print("P");
      Serial.print(i);
      Serial.print(":");
      Serial.println(pwmValue);
      lastPotValue[i] = pwmValue;
    }
  }

  delay(10);
}



Código Processing:

import processing.serial.*;
import processing.sound.*;

Serial myPort;

// Sonidos emocionales
SoundFile alegria, tristeza, rabia;
boolean playingAlegria = false;
boolean playingTristeza = false;
boolean playingRabia = false;

// Estado de botones
boolean[] buttonState = {false, false, false};

// Colores base de las emociones
color cAlegria = color(255, 230, 0);   // Amarillo cálido
color cTristeza = color(0, 120, 255);  // Azul profundo
color cRabia = color(255, 50, 30);     // Rojo intenso

// Potenciómetros
float brillo = 1.0;
float volumen = 1.0;

void setup() {
  size(800, 600);
  myPort = new Serial(this, "COM3", 9600); // Cambia COM3 según tu puerto

  alegria = new SoundFile(this, "alegria.wav");
  tristeza = new SoundFile(this, "tristeza.wav");
  rabia = new SoundFile(this, "rabia.wav");
}

void draw() {
  leerDatos();

  // Mezclar colores activos
  color fondo = color(0);
  int count = 0;

  if (buttonState[0]) { fondo = lerpColor(fondo, cAlegria, 0.5); count++; }
  if (buttonState[1]) { fondo = lerpColor(fondo, cTristeza, 0.5); count++; }
  if (buttonState[2]) { fondo = lerpColor(fondo, cRabia, 0.5); count++; }

  if (count > 0) fondo = color(
    red(fondo) * brillo,
    green(fondo) * brillo,
    blue(fondo) * brillo
  );

  background(fondo);
  fill(255);
  textAlign(CENTER, CENTER);
  textSize(24);
  text("Botonera Emocional", width/2, height - 50);
}

void leerDatos() {
  while (myPort.available() > 0) {
    String data = trim(myPort.readStringUntil('\n'));
    if (data == null || data.length() < 2) return;

    if (data.charAt(0) == 'B') {
      String[] partes = splitTokens(data.substring(1), ":");
      if (partes.length == 2) {
        int id = int(partes[0]);
        int estado = int(partes[1]);
        buttonState[id] = (estado == 0); // LOW = presionado

        if (buttonState[id]) activarSonido(id);
      }
    }

    if (data.charAt(0) == 'P') {
      String[] partes = splitTokens(data.substring(1), ":");
      if (partes.length == 2) {
        int id = int(partes[0]);
        int valor = int(partes[1]);

        if (id == 0) brillo = map(valor, 0, 255, 0.3, 1.5);
        if (id == 1) volumen = map(valor, 0, 255, 0.0, 1.0);
        actualizarVolumen();
      }
    }
  }
}

void activarSonido(int id) {
  if (id == 0 && !playingAlegria) { alegria.loop(); playingAlegria = true; }
  if (id == 1 && !playingTristeza) { tristeza.loop(); playingTristeza = true; }
  if (id == 2 && !playingRabia) { rabia.loop(); playingRabia = true; }
}

void actualizarVolumen() {
  alegria.amp(volumen);
  tristeza.amp(volumen);
  rabia.amp(volumen);
}
```
