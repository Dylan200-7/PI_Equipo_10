Diseño de PCB – Sensor de distancia VL53L0X
🔌 1. Esquemático electrónico

El siguiente esquemático representa la organización y conexión de los componentes electrónicos utilizados en el diseño del sensor de distancia VL53L0X.

El circuito está compuesto por el sensor VL53L0X, resistencias de 10 kΩ, capacitores de desacoplamiento, un conector de 40 pines y las conexiones de alimentación de +3.3 V y GND. El sensor permite realizar la medición de distancia mediante tecnología de tiempo de vuelo (ToF).

En el esquemático se identifica el componente U1, correspondiente al VL53L0X, cuyos pines incluyen las conexiones de alimentación, tierra, SDA, SCL, XSHUT y GPIO1. También se encuentran las resistencias R1, R2 y R3, todas de 10 kΩ, además de los capacitores C1 de 100 nF y C2 de 4.7 µF.

<p align="center"> <img src="SCH_Schematic1_2026-09-03.pdf" width="800"/> </p> <p align="center"> <em>Figura 1. Esquemático electrónico del sensor de distancia VL53L0X desarrollado en EasyEDA.</em> </p>
🧩 2. Diseño PCB

A partir del esquemático electrónico se realizó el diseño de la placa de circuito impreso (PCB), distribuyendo los componentes electrónicos y realizando el enrutamiento de las pistas necesarias para establecer las conexiones entre el sensor VL53L0X, las resistencias, los capacitores y el conector de 40 pines.

El diseño PCB contempla los componentes U1 (VL53L0X), U2 (conector 2.54-2*20), R1, R2, R3, C1 y C2. Las resistencias R1, R2 y R3 presentan un valor de 10 kΩ, mientras que C1 tiene un valor de 100 nF y C2 un valor de 4.7 µF.

El archivo Gerber generado contiene las diferentes capas necesarias para la fabricación de la placa, incluyendo las capas de cobre superior e inferior, máscara de soldadura, serigrafía, pasta de soldadura y archivos de perforación.


Vista de pistas de la PCB

La vista de pistas permite observar la distribución de las conexiones eléctricas realizadas sobre la placa, así como las diferentes rutas utilizadas para interconectar los componentes.

El paquete Gerber proporcionado contiene las capas TopLayer y BottomLayer, correspondientes a las capas de cobre superior e inferior de la PCB, además de las capas de serigrafía y máscara de soldadura.


🖥️ 3. Vista 3D de la PCB

La vista tridimensional de la PCB permite comprobar visualmente la distribución y ubicación de los componentes sobre la placa, facilitando la revisión del diseño antes de su fabricación.

En el diseño desarrollado se encuentran el sensor VL53L0X, las resistencias R1, R2 y R3, los capacitores C1 y C2 y el conector de 40 pines. El esquemático identifica específicamente estos componentes y sus respectivos valores.


