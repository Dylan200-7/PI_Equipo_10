# Diseño de PCB – Sensor de distancia VL53L0X

## 🔌 1. Esquemático electrónico

El siguiente esquemático representa la organización y conexión de los componentes electrónicos utilizados en el diseño del sensor de distancia **VL53L0X**.

El circuito está compuesto por el **sensor VL53L0X**, resistencias de **10 kΩ**, capacitores de desacoplamiento, un conector de **40 pines** y las conexiones de alimentación de **+3.3 V y GND**. El sensor permite realizar la medición de distancia mediante tecnología de tiempo de vuelo (ToF).

En el esquemático se identifica el componente **U1**, correspondiente al VL53L0X, cuyos pines incluyen las conexiones de alimentación, tierra, **SDA, SCL, XSHUT y GPIO1**. También se encuentran las resistencias **R1, R2 y R3**, todas de 10 kΩ, además de los capacitores **C1 de 100 nF** y **C2 de 4.7 µF**.

<p align="center">
  <img src="SCH_Schematic1_2026-09-03.pdf" width="800"/>
</p>

<p align="center">
  <em>Figura 1. Esquemático electrónico del sensor de distancia VL53L0X desarrollado en EasyEDA.</em>
</p>

---

## 🧩 2. Diseño PCB

A partir del esquemático electrónico se realizó el diseño de la **placa de circuito impreso (PCB)**, distribuyendo los componentes electrónicos y realizando el enrutamiento de las pistas necesarias para establecer las conexiones entre el sensor VL53L0X, las resistencias, los capacitores y el conector de 40 pines.

El diseño PCB contempla los componentes **U1 (VL53L0X), U2 (conector 2.54-2*20), R1, R2, R3, C1 y C2**. Las resistencias R1, R2 y R3 presentan un valor de 10 kΩ, mientras que C1 tiene un valor de 100 nF y C2 un valor de 4.7 µF.

### Vista de pistas de la PCB

La siguiente vista permite observar con mayor detalle las pistas, conexiones y distribución de los diferentes elementos presentes en la placa.

---

## 🖥️ 3. Vista 3D de la PCB

EasyEDA permite visualizar el diseño final de la placa en tres dimensiones, facilitando la revisión de la ubicación de los componentes y permitiendo observar cómo quedaría físicamente la PCB una vez ensamblada.

En esta vista se puede observar la distribución de los componentes electrónicos que conforman la placa, incluyendo el **sensor VL53L0X**, las resistencias, los capacitores y el conector utilizado en el diseño.

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/3D_PCB1_2026-09-03%20%281%29.png" width="800"/>
</p>

<p align="center">
  <em>Figura 4. Vista tridimensional de la PCB desarrollada en EasyEDA.</em>
</p>

---

## 📦 4. Archivos Gerber

Una vez finalizado el diseño de la PCB, se generaron los **archivos Gerber**, los cuales contienen la información necesaria para la fabricación física de la placa de circuito impreso.

Estos archivos incluyen información relacionada con las diferentes capas de cobre, perforaciones, máscara de soldadura, serigrafía y contorno de la PCB.

El conjunto de archivos Gerber se encuentra comprimido en formato **ZIP**, facilitando su organización y posterior utilización para la fabricación de la placa.

<p align="center">
  <a href="Gerber_PCB1_2026-09-03.zip">
    <strong>⬇️ Descargar archivos Gerber</strong>
  </a>
</p>

---

## 📁 Archivos de la entrega

| Archivo | Descripción |
|---|---|
| [SCH_Schematic1_2026-09-03.pdf](SCH_Schematic1_2026-09-03.pdf) | Archivo PDF del esquemático electrónico del sensor de distancia VL53L0X elaborado en EasyEDA. |
| [Gerber_PCB1_2026-09-03.zip](Gerber_PCB1_2026-09-03.zip) | Archivo comprimido que contiene los archivos Gerber necesarios para la fabricación de la PCB. |
| [3D_PCB1_2026-09-03 (1).png](https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/3D_PCB1_2026-09-03%20%281%29.png) | Imagen de la vista tridimensional de la PCB desarrollada en EasyEDA. |
