# Diseño de PCB – Sensor de Peso HX711

## 🔌 1. Esquemático electrónico

El siguiente esquemático representa la organización y conexión de los componentes electrónicos utilizados en el diseño del módulo de sensor de peso basado en la celda de carga y el amplificador **HX711**.

El circuito está compuesto por el **conector de la celda de carga** (E+, E-, A+, A-), el **módulo HX711** (amplificador y conversor ADC de 24 bits), sus capacitores de desacople, y el **microcontrolador Raspberry Pi Pico**, encargado de recibir y procesar la señal digital (DOUT / PD_SCK) generada por el sensor.

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Mogollon_Flores_Josue_Cristhian_Mateo.md/Imagenes/SCH_Sensor_Peso_HX711_1-P1_Mogollon_Flores_Josue.png.png" width="800"/>
</p>

<p align="center">
  <em>Figura 1. Esquemático electrónico del sensor de peso HX711 desarrollado en EasyEDA.</em>
</p>

---

## 🧩 2. Diseño PCB

A partir del esquemático electrónico se realizó el diseño de la **placa de circuito impreso (PCB)**, ubicando los componentes y realizando el enrutamiento de las pistas necesarias para conectar la celda de carga, el módulo HX711, los capacitores de desacople y el microcontrolador Raspberry Pi Pico.

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Mogollon_Flores_Josue_Cristhian_Mateo.md/Imagenes/PCB_PCB1_Mogollon_Flores_Josue.png" width="800"/>
</p>

<p align="center">
  <em>Figura 2. Diseño principal de la placa PCB desarrollado en EasyEDA.</em>
</p>

### Vista de pistas de la PCB

La siguiente vista permite observar con mayor detalle las pistas, conexiones y distribución de los diferentes elementos presentes en la placa.

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Mogollon_Flores_Josue_Cristhian_Mateo.md/Imagenes/PCB_PCB2_Mogollon_Flores_Josue.png" width="800"/>
</p>

<p align="center">
  <em>Figura 3. Vista de las pistas y conexiones de la PCB.</em>
</p>

---

## 🖥️ 3. Vista 3D de la PCB

EasyEDA permite visualizar el diseño final de la placa en tres dimensiones, facilitando la revisión de la ubicación de los componentes y permitiendo observar cómo quedaría físicamente la PCB una vez ensamblada.

En esta vista se puede observar el **Raspberry Pi Pico**, el **módulo HX711**, los capacitores de desacople, el conector de la celda de carga y los diferentes elementos gráficos incorporados en la placa.

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Mogollon_Flores_Josue_Cristhian_Mateo.md/Imagenes/PCB_3D_PCB1_Mogollon_Flores_Josue.png" width="800"/>
</p>

<p align="center">
  <em>Figura 4. Vista tridimensional de la PCB desarrollada en EasyEDA.</em>
</p>

---

## 📦 4. Archivos Gerber

Una vez finalizado el diseño de la PCB, se generaron los **archivos Gerber**, los cuales contienen la información necesaria para la fabricación física de la placa de circuito impreso.

Estos archivos incluyen información relacionada con las capas de cobre (top/bottom), perforaciones (drill), máscara de soldadura (solder mask), pasta de soldadura, serigrafía (silkscreen) y contorno de la PCB.

<p align="center">
  <a href="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_EasyEda/Mogollon_Flores_Josue_Cristhian_Mateo.md/Imagenes/Gerber_PCB1_Mogollon_Flores_Josue.zip">
    <strong>⬇️ Descargar archivos Gerber</strong>
  </a>
</p>


