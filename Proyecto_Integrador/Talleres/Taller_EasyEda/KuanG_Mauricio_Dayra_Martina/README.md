# Diseño de PCB – Sensor de Giro

## 1. Esquemático electrónico

El siguiente esquemático representa la organización y conexión de los componentes electrónicos utilizados para el desarrollo del sensor Hall A3144, encargado de detectar el giro mediante la detección de un campo magnético.

El circuito utiliza el A3144 como elemento principal. El sensor es alimentado mediante una fuente de 5 V, mientras que su salida digital es acondicionada para trabajar con un nivel de 3.3 V, permitiendo su posterior conexión con una Raspberry Pi.

Para mejorar la estabilidad del circuito se incorporaron capacitores de desacoplamiento y filtrado. Asimismo, se emplea una resistencia **pull-up de 10 kΩ (R1)** conectada a 3.3 V y una resistencia de **1 kΩ (R2)** asociada a la línea de salida SIGNAL.

El circuito incorpora además un **conector de cuatro pines (J1)** que permite acceder a las líneas de:

* +5 V
* +3.3 V
* GND
* SIGNAL

Los principales componentes empleados son:

* **U1:** Sensor de efecto Hall A3144.
* **R1:** Resistencia de 10 kΩ.
* **R2:** Resistencia de 1 kΩ.
* **C1:** Capacitor de 100 nF.
* **C2:** Capacitor de 10 µF.
* **C3:** Capacitor de 10 nF.
* **J1:** Conector de cuatro pines para alimentación y señal.

## 2. Diseño PCB

A partir del esquemático electrónico se realizó el diseño de la placa de circuito impreso (PCB), distribuyendo los componentes de forma compacta y realizando el enrutamiento de las pistas necesarias para interconectar el sensor, las resistencias, los capacitores y el conector de alimentación y señal. Durante el diseño de la PCB se mantuvo a los componentes próximos al sensor A3144, reduciendo las distancias de conexión y favoreciendo la estabilidad eléctrica.

El conector principal permite conectar la placa con un sistema externo mediante las líneas de alimentación de **5 V y 3.3 V**, tierra (GND) y la salida digital **SIGNAL**.

<p align="center">
  <img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Recursos/Im%C3%A1genes/Sensor_Giro.png" width="800"/>
</p>

<p align="center">
  <em>Figura 2. Diseño principal de la placa PCB del sensor de efecto Hall A3144 desarrollado en EasyEDA.</em>
</p>

## 🖥️ 3. Vista 3D de la PCB

EasyEDA permite visualizar el diseño final de la placa en tres dimensiones, facilitando la revisión de la distribución física de los componentes antes de proceder con su fabricación.

En la representación 3D se pueden observar los principales elementos que conforman el módulo: el **sensor A3144**, las resistencias **R1 y R2**, los capacitores de filtrado **C1, C2 y C3**, así como el **conector J1** utilizado para establecer la conexión con un sistema externo.

Esta vista permite verificar aspectos como la orientación de los componentes, su separación, el espacio disponible para soldadura y la disposición general de la placa.

<p align="center">
  <img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Recursos/Im%C3%A1genes/3D_SensorGiro.png" width="800"/>
</p>

<p align="center">
  <em>Figura 3. Vista tridimensional de la PCB del módulo sensor de efecto Hall A3144 desarrollada en EasyEDA.</em>
</p>

