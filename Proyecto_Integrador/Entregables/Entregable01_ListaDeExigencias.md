# 1. Lista de Exigencias

## Tabla 1: Lista de Exigencias

| **LISTA DE EXIGENCIAS** |                                                                                                                       |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Edición:**            | Rev. 1                                                                                                                |
| **PROYECTO:**           | **Diseño de sistema mecatrónico inteligente de triaje poscosecha de papa Chaucha / grupo Phureja — Kartoffelmachine** |
| **Fecha:**              | 20/08/2026                                                                                                            |
| **Revisado:**           |                                                                                                                       |
| **CLIENTE:**            | **UNIVERSIDAD PERUANA CAYETANO HEREDIA**                                                                              |
| **Elaborado:**          | **Josue Mogollon(JM), Nicole Anyosa(NA), Dayra Kuang(DK), Dylan Quispe(DQ)**                                                                                           |

---

| **Fecha (cambios)** | **Deseo o Exigencia** | **Descripción**                                                                                                                                                                   | **Responsable** |
| ------------------- | :-------------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------: |
| 20/08/26 | E | **Función Principal:** Inspeccionar y clasificar automáticamente papa Chaucha/Phureja según defectos externos, brotación y tamaño, para determinar su aprovechamiento poscosecha. | JM |
| 20/08/26 | E | **Geometría:** El sistema deberá manipular papas de distintos tamaños, incluyendo tubérculos pequeños, evitando caídas o atascos durante el proceso. | DK |
| 20/08/26 | E | **Cinemática:** El transporte deberá desplazar y orientar las papas de manera controlada para facilitar su inspección sin producir daños. | DQ |
| 20/08/26 | E | **Fuerzas:** Los mecanismos no deberán producir golpes, cortes, aplastamiento ni daños significativos en los tubérculos. | DQ |
| 20/08/26 | E | **Energía:** El sistema deberá utilizar una alimentación eléctrica adecuada para los motores, sensores, cámara, controlador y actuadores. | DQ |
| 20/08/26 | E | **Materia:** Se procesarán papas Chaucha/Phureja de diferentes tamaños y estados visibles, considerando defectos, deterioro y brotación. | NA |
| 20/08/26 | E | **Señales:** Entradas: encendido, inicio, parada, sensores y cámara. Salidas: estado, clasificación, accionamiento del separador, error y emergencia. | DQ |
| 20/08/26 | E | **Control:** El sistema deberá coordinar transporte, captura de imágenes, clasificación y separación automática de cada tubérculo. | DQ |
| 20/08/26 | E | **Electrónico (hardware):** Se utilizará cámara, iluminación, sensores, controlador, motores y actuadores necesarios para la inspección y clasificación. | DQ |
| 20/08/26 | E | **Software:** El programa deberá procesar las imágenes obtenidas y clasificar automáticamente las papas según las características detectadas. | DQ |
| 20/08/26 | E | **Inspección visual:** Las imágenes deberán capturarse con iluminación controlada para identificar color, textura, forma y defectos externos. | NA |
| 20/08/26 | E | **Medición:** El sistema deberá estimar el tamaño del tubérculo mediante visión artificial y sin realizar contacto destructivo. | DQ |
| 20/08/26 | E | **Comunicaciones:** Sensores, cámara, controlador y actuadores deberán intercambiar información correctamente y mantenerse sincronizados. | DQ |
| 20/08/26 | E | **Seguridad:** El diseño deberá proteger al usuario de partes móviles y conexiones eléctricas, además de contar con un sistema de parada de emergencia. | DK |
| 20/08/26 | E | **Higiene e inocuidad:** Las superficies en contacto con la papa deberán ser resistentes, no tóxicas y fáciles de limpiar. | NA |
| 20/08/26 | E | **Ergonomía:** Los controles y zonas de alimentación y recolección deberán permitir una operación cómoda y segura. | DQ |
| 20/08/26 | E | **Fabricación:** Se priorizarán materiales y componentes comerciales disponibles localmente o de fácil adquisición y reemplazo. | DQ |
| 20/08/26 | E | **Control de calidad:** Se evaluará la clasificación correcta, tiempo de procesamiento, funcionamiento de la separación, presencia de atascos y posibles daños en las papas. | NA |
| 20/08/26 | E | **Montaje:** Los componentes mecánicos, electrónicos y de visión deberán instalarse de manera estable y permitir su desmontaje. | DQ |
| 20/08/26 | E | **Transporte:** El prototipo deberá tener dimensiones y peso adecuados para ser trasladado fácilmente dentro de la universidad. | DQ |
| 20/08/26 | D | **Uso:** El prototipo funcionará principalmente en interiores y deberá mantener condiciones adecuadas de iluminación para la inspección. | DK |
| 20/08/26 | E | **Mantenimiento:** Los componentes deberán ser accesibles para limpieza, inspección, ajuste y reemplazo. | DQ |
| 20/08/26 | D | **Costos:** Se priorizarán componentes comerciales y reutilizables para mantener un costo accesible de fabricación. | JM |
| 20/08/26 | E | **Plazos:** El proyecto se desarrollará durante el periodo académico **2026-2**, siguiendo las etapas establecidas para el desarrollo del sistema. | DK |

---


# 2. Plan de Trabajo

## Figura 1: Plan de Trabajo

> **Nota:** las semanas indicadas constituyen una planificación de trabajo del equipo. Las fechas exactas de sustentaciones y entregas deberán reemplazarse por las establecidas por el docente.

| N.° | **ACTIVIDADES**                                            | **HORA DE ENTREGA / EXPOSICIÓN** | **FECHA DE ENTREGA** | **SEMANAS** | **HORAS DE TRABAJO** |
| --: | ---------------------------------------------------------- | -------------------------------- | -------------------- | ----------- | -------------------: |
|   1 | Lista de exigencias                                        | Según cronograma                 | Semana 1             | 1           |                    5 |
|   2 | Plan de trabajo                                            | Según cronograma                 | Semana 1             | 1           |                    3 |
|   3 | Investigación de la problemática y estado de la tecnología | Según cronograma                 | Semana 2             | 1–2         |                    8 |
|   4 | Estructura de funciones del sistema                        | Según cronograma                 | Semana 3             | 2–3         |                    6 |
|   5 | Desarrollo de conceptos de solución                        | Según cronograma                 | Semana 4             | 3–4         |                    8 |
|   6 | Selección del concepto de solución integrado               | Según cronograma                 | Semana 5             | 4–5         |                    6 |
|   7 | Diseño preliminar del subsistema mecánico                  | Según cronograma                 | Semana 6             | 5–6         |                    8 |
|   8 | Diseño preliminar electrónico y de control                 | Según cronograma                 | Semana 6             | 5–6         |                    6 |
|   9 | Diseño preliminar del sistema de visión artificial         | Según cronograma                 | Semana 7             | 6–7         |                    8 |
|  10 | Sustentación parcial                                       | Según cronograma                 | Semana 7             | 7           |                    3 |
|  11 | Adquisición, organización y etiquetado del dataset         | Según cronograma                 | Semana 8             | 7–8         |                    8 |
|  12 | Entrenamiento y validación inicial del modelo de IA        | Según cronograma                 | Semana 10            | 8–10        |                   12 |
|  13 | Fabricación y ensamblaje mecánico                          | Según cronograma                 | Semana 11            | 9–11        |                   12 |
|  14 | Integración de sensores, control y actuadores              | Según cronograma                 | Semana 12            | 11–12       |                   10 |
|  15 | Integración del sistema de visión artificial               | Según cronograma                 | Semana 13            | 12–13       |                    8 |
|  16 | Ensayos del prototipo completo                             | Según cronograma                 | Semana 14            | 13–14       |                    8 |
|  17 | Corrección de fallas y optimización                        | Según cronograma                 | Semana 15            | 14–15       |                    8 |
|  18 | Planos, lista de piezas y documentación técnica            | Según cronograma                 | Semana 15            | 14–15       |                    4 |
|  19 | Instrucciones de fabricación, montaje y mantenimiento      | Según cronograma                 | Semana 16            | 15–16       |                    4 |
|  20 | Elaboración del informe técnico final                      | Según cronograma                 | Semana 16            | 15–16       |                    8 |
|  21 | Sustentación y entrega final                               | Según cronograma                 | Semana 16            | 16          |                    3 |
|     | **TOTAL DE HORAS PROGRAMADAS**                             |                                  |                      |             |            **146 h** |

---

## Bibliografía 

* **Gamez-Rojas, G., Fuertes-Guerrero, C., & Mejía-España, D. (2025).** *Fumigación con etanol como tratamiento para inhibir la brotación en papa criolla colombiana (Solanum phureja).* TecnoLógicas, 28(63).
* **Seminario-Cunya, J. F., Villanueva-Guevara, R., & Valdez-Yopla, M. H. (2018).** *Rendimiento de cultivares de papa amarillos precoces del grupo Phureja.* Agronomía Mesoamericana, 29(3), 639–653.
* **Ruiz Santa Cruz, Y. F., & Sánchez Torres, M. R. (2024).** *Método de clasificación automática para defectos externos de Solanum phureja.* Universidad Señor de Sipán.
* **Barnes, M., Duckett, T., Cielniak, G., Stroud, G., & Harper, G. (2010).** *Visual detection of blemishes in potatoes using minimalist boosted classifiers.* Journal of Food Engineering, 98(3), 339–346.
* **Su, Q., Kondo, N., Li, M., Sun, H., & Al Riza, D. F. (2017).** *Potato feature prediction based on machine vision and 3D model rebuilding.* Computers and Electronics in Agriculture, 137, 41–51.
* **Yang, Y., Liu, Z., Huang, M., Zhu, Q., & Zhao, X. (2023).** *Automatic detection of multi-type defects on potatoes using multispectral imaging combined with a deep learning model.* Journal of Food Engineering, 336.
* **Li, J., Sun, W., Meng, Y., Liu, K., & Simionescu, P. A. (2026).** *Design and experimental study of a seed potato cutting machine and its machine vision-based defective tuber removal system.* Computers and Electronics in Agriculture.
* **Ministerio de Salud del Perú.** *D.S. N.° 007-98-SA — Reglamento sobre Vigilancia y Control Sanitario de Alimentos y Bebidas.*
* **Congreso de la República del Perú.** *Ley N.° 29783 — Ley de Seguridad y Salud en el Trabajo.*
* **ISO 12100:2010.** *Safety of machinery — Risk assessment and risk reduction.*
* **ISO 7250-1:2017.** *Basic human body measurements for technological design.*
* **ISO 22000:2018.** *Food safety management systems.*
* **VDI/VDE 2206:2021.** *Development of mechatronic and cyber-physical systems.*

