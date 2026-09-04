# Diseño de PCB – Sensor de Distancia Láser de Tiempo de Vuelo (ToF) VL53L0X

## 🔌 1. Esquemático electrónico

El siguiente esquemático representa la organización y conexión de los componentes electrónicos utilizados en el diseño del módulo del sensor de distancia por tiempo de vuelo (ToF) VL53L0X.

El circuito está compuesto por el sensor óptico de precisión **VL53L0X (U1)**, resistencias de pull-up para la comunicación I2C y líneas de control, capacitores de desacoplo para la estabilidad de la alimentación, y un conector de expansión de **2.54mm de 2x20 pines (U2)** que permite la interfaz con sistemas externos o tarjetas de desarrollo como la Raspberry Pi Pico.

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/SCH_Sensor_IR_TCRT5000_1-P1_Quispe_Charres_Mathias_Dylan_Henry.png" width="800"/>
</p>

<p align="center">
  <em>Figura 1. Esquemático electrónico del sensor VL53L0X desarrollado en EasyEDA.</em>
</p>

---

## 🧩 2. Diseño PCB

A partir del esquemático electrónico se realizó el diseño de la **placa de circuito impreso (PCB)**, ubicando estratégicamente los componentes pasivos en tecnología de montaje superficial (SMD) cerca del sensor para minimizar el ruido, y realizando el enrutamiento de las pistas de alimentación (+3.3V y GND), señales de control (XSHUT, GPIO1) y el bus de datos I2C (SDA, SCL).

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/PCB_PCB1_Quispe_Charres_Mathias_Dylan_Henry.png" width="800"/>
</p>

<p align="center">
  <em>Figura 2. Diseño principal de la placa PCB desarrollado en EasyEDA.</em>
</p>

### Vista de pistas de la PCB

La siguiente vista permite observar con mayor detalle el ruteo de las pistas en las capas de cobre, la distribución de los pads para los componentes SMD y la disposición del conector hembra de 40 pines.

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/PCB_PCB2_Quispe_Charres_Mathias_Dylan_Henry.png" width="800"/>
</p>

<p align="center">
  <em>Figura 3. Vista de las pistas y conexiones de la PCB.</em>
</p>

---

## 🖥️ 3. Vista 3D de la PCB

EasyEDA permite visualizar el diseño final de la placa en tres dimensiones, facilitando la revisión de la orientación física de los componentes, la holgura del conector principal de 2x20 pines y la correcta disposición superficial de las resistencias (R1, R2, R3) y capacitores (C1, C2).

En esta vista se aprecia el acabado final que tendrá la tarjeta de circuito impreso una vez fabricada y ensamblada con sus respectivos componentes.

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/PCB_3D_PCB1_Quispe_Charres_Mathias_Dylan_Henry.png" width="800"/>
</p>

<p align="center">
  <em>Figura 4. Vista tridimensional de la PCB desarrollada en EasyEDA.</em>
</p>

---

## 📦 4. Archivos Gerber

Una vez finalizado el diseño de la PCB, se generaron los **archivos Gerber**, los cuales contienen la información técnica normalizada necesaria para la manufactura física de la placa.

Estos archivos incluyen las máscaras de soldadura (Top/Bottom Solder Mask), las capas de cobre (Top/Bottom Layer), las leyendas de componentes (Top/Bottom Silkscreen), el mapa de perforaciones (Drill) y el contorno de la placa (Board Outline).

<p align="center">
  <a href="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/Gerber_PCB1_Quispe_Charres_Mathias_Dylan_Henry.zip">
    <strong>⬇️ Descargar archivos Gerber</strong>
  </a>
</p>

---

## 📁 Archivos de la entrega

| Archivo | Descripción |
|---|---|
| [SCH_Sensor_IR_TCRT5000_1-P1_Quispe_Charres_Mathias_Dylan_Henry.pdf](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/SCH_Sensor_IR_TCRT5000_1-P1_Quispe_Charres_Mathias_Dylan_Henry.pdf) | Archivo PDF del esquemático electrónico del sensor VL53L0X elaborado en EasyEDA. |
| [PCB_PCB1_Quispe_Charres_Mathias_Dylan_Henry.pdf](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/PCB_PCB1_Quispe_Charres_Mathias_Dylan_Henry.pdf) | Archivo PDF del diseño principal de la placa PCB. |
| [PCB_PCB2_Quispe_Charres_Mathias_Dylan_Henry.pdf](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/PCB_PCB2_Quispe_Charres_Mathias_Dylan_Henry.pdf) | Archivo PDF con la vista de las pistas y conexiones de la PCB. |
| [PCB_3D_PCB1_Quispe_Charres_Mathias_Dylan_Henry.pdf](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/PCB_3D_PCB1_Quispe_Charres_Mathias_Dylan_Henry.pdf) | Archivo PDF con la vista tridimensional de la PCB y sus componentes electrónicos. |
| [Gerber_PCB1_Quispe_Charres_Mathias_Dylan_Henry.zip](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/Gerber_PCB1_Quispe_Charres_Mathias_Dylan_Henry.zip) | Archivo comprimido que contiene los archivos Gerber necesarios para la fabricación de la PCB. |


