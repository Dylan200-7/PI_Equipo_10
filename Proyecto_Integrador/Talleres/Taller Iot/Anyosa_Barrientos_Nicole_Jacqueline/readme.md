## TALLER DE INTERNET DE LAS COSAS 

El Internet de las Cosas (IoT) es la idea de conectar objetos físicos a internet para que puedan captar datos, enviarlos y, a veces, recibir órdenes, sin que una persona tenga que intervenir cada vez.

Los materiales que usamos:
- 01 ESP32 Dev Kit 1
- 01 Arduino EXPLORE IoT Kit
- 01 Kit de sensores Keystudio 48 en 1
- 01 Multímetro
- 01 Protoboard

## Actividad 1: Lectura de un Potenciómetro con ESP32
Mejorar el código anterior haciendo uso de un promediado de los datos y convirtiendo los
valores del ADC a valores de voltaje.

Código Básico:

int potPin = 34; // Pin donde está conectado el potenciómetro

void setup() {

Serial.begin(115200); // Inicializar el monitor serie

}

void loop() {

int valor = analogRead(potPin); // Leer valor del potenciómetro

Serial.println(valor); // Mostrar valor en el monitor serie

delay(500); // Esperar medio segundo

}

![ACTIVIDAD 1](Imagenes/001.jpeg)



