# Diseño de PCB – Sensor Infrarrojo TCRT5000

## 🔌 1. Esquemático electrónico

El siguiente esquemático representa la organización y conexión de los componentes electrónicos utilizados en el diseño del sensor infrarrojo TCRT5000.

El circuito está compuesto por el **emisor infrarrojo**, el **receptor**, sus respectivas resistencias, un conector de alimentación/señal y el **microcontrolador Raspberry Pi Pico**, encargado de recibir y procesar la señal generada por el sensor.

<p align="center">
  <img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_02/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/SCH_Sensor_IR_TCRT5000_1-P1_Quispe_Charres_Mathias_Dylan_Henry.png" width="800"/>
</p>

<p align="center">
  <em>Figura 1. Esquemático electrónico del sensor infrarrojo TCRT5000 desarrollado en EasyEDA.</em>
</p>

---

## 🧩 2. Diseño PCB

A partir del esquemático electrónico se realizó el diseño de la **placa de circuito impreso (PCB)**, ubicando los componentes y realizando el enrutamiento de las pistas necesarias para conectar el sensor infrarrojo, las resistencias, el conector y el microcontrolador.

<p align="center">
  <img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_02/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/PCB_PCB1_Quispe_Charres_Mathias_Dylan_Henry.png" width="800"/>
</p>

<p align="center">
  <em>Figura 2. Diseño principal de la placa PCB desarrollado en EasyEDA.</em>
</p>

### Vista de pistas de la PCB

La siguiente vista permite observar con mayor detalle las pistas, conexiones y distribución de los diferentes elementos presentes en la placa.

<p align="center">
  <img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_02/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/PCB_PCB2_Quispe_Charres_Mathias_Dylan_Henry.png" width="800"/>
</p>

<p align="center">
  <em>Figura 3. Vista de las pistas y conexiones de la PCB.</em>
</p>

---

## 🖥️ 3. Vista 3D de la PCB

EasyEDA permite visualizar el diseño final de la placa en tres dimensiones, facilitando la revisión de la ubicación de los componentes y permitiendo observar cómo quedaría físicamente la PCB una vez ensamblada.

En esta vista se puede observar el **Raspberry Pi Pico**, el **sensor infrarrojo TCRT5000**, las resistencias, el conector y los diferentes elementos gráficos incorporados en la placa.

<p align="center">
  <img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_02/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/PCB_3D_PCB1_Quispe_Charres_Mathias_Dylan_Henry.png" width="800"/>
</p>

<p align="center">
  <em>Figura 4. Vista tridimensional de la PCB desarrollada en EasyEDA.</em>
</p>

---

## 📦 4. Archivos Gerber

Una vez finalizado el diseño de la PCB, se generaron los **archivos Gerber**, los cuales contienen la información necesaria para la fabricación física de la placa de circuito impreso.

Estos archivos incluyen información relacionada con las capas de cobre, perforaciones, máscara de soldadura, serigrafía y contorno de la PCB.

<p align="center">
  <a href="https://github.com/Dylan200-7/PI_Equipo_10/raw/main/Proyecto_Integrador/Talleres/Taller_02/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/Gerber_PCB1_Quispe_Charres_Mathias_Dylan_Henry.zip">
    <strong>⬇️ Descargar archivos Gerber</strong>
  </a>
</p>

---

## 📁 Archivos de la entrega

| Archivo | Descripción |
|---|---|
| `SCH_Sensor_IR_TCRT5000_1-P1_Quispe_Charres_Mathias_Dylan_Henry.png` | Imagen del esquemático electrónico del sensor infrarrojo TCRT5000 elaborado en EasyEDA. |
| `PCB_PCB1_Quispe_Charres_Mathias_Dylan_Henry.png` | Imagen principal del diseño de la placa PCB. |
| `PCB_PCB2_Quispe_Charres_Mathias_Dylan_Henry.png` | Vista de las pistas y conexiones de la PCB. |
| `PCB_3D_PCB1_Quispe_Charres_Mathias_Dylan_Henry.png` | Vista tridimensional de la PCB con los componentes electrónicos. |
| [`Gerber_PCB1_Quispe_Charres_Mathias_Dylan_Henry.zip`](https://github.com/Dylan200-7/PI_Equipo_10/raw/main/Proyecto_Integrador/Talleres/Taller_02/Quispe_Charres_Mathias_Dylan_Henry/Imagenes/Gerber_PCB1_Quispe_Charres_Mathias_Dylan_Henry.zip) | Archivo comprimido que contiene los archivos Gerber necesarios para la fabricación de la PCB. |
