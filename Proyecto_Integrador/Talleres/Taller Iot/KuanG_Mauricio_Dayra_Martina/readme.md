## Taller de Internet de las Cosas (IoT)
En el presente taller se trabajó la tecnología de IoT, es una tecnología que conecta objetos físicos como sensores, 
a Internet para recoger, procesar y transmitir datos.

En la clase se trabajó con:
01 ESP32 Dev Kit 1
● 01 Arduino EXPLORE IOT KIT
● 01 Kit de sensores Keystudio 48 en 1
● 01 Multímetro
● 01 Protoboard

## Actividad: Lectura de un Potenciómetro con ESP32
Mejorar el código proporcionado haciendo uso de un promediado de los datos y convirtiendo los
valores del ADC a valores de voltaje

*Código Básico:*

"int potPin = 34; // Pin donde está conectado el potenciómetro

void setup() {

Serial.begin(115200); // Inicializar el monitor serie

}

void loop() {

int valor = analogRead(potPin); // Leer valor del potenciómetro

Serial.println(valor); // Mostrar valor en el monitor serie

delay(500); // Esperar medio segundo}"

<p align="center">
  <img src="imagenes/Actividad_1.jpeg" width="850">
</p>

<p align="center">
  <img src="imagenes/Actividad_11.jpeg" width="850">
</p>


## Actividad 02:
Crear una red WIFI usando su Smartphone como Hotspot, y conectarse a ella con el ESP32. En el
monitor serial se deberá visualizar la dirección IP asignada.


