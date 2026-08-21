# 1. Lista de Exigencias

## Tabla 1: Lista de Exigencias

| **LISTA DE EXIGENCIAS** |                                                                                                                       |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Páginas:**            | 5                                                                                                                     |
| **Edición:**            | Rev. 1                                                                                                                |
| **PROYECTO:**           | **Diseño de sistema mecatrónico inteligente de triaje poscosecha de papa Chaucha / grupo Phureja — Kartoffelmachine** |
| **Fecha:**              | 20/08/2026                                                                                                            |
| **Revisado:**           |                                                                                                                       |
| **CLIENTE:**            | **UNIVERSIDAD PERUANA CAYETANO HEREDIA**                                                                              |
| **Elaborado:**          | **Equipo Kartoffelmachine**                                                                                           |

---

| **Fecha (cambios)** | **Deseo o Exigencia** | **Descripción**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | **Responsable**         |
| ------------------- | :-------------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- |
| 20/08/26            |           E           | **Función Principal:** Inspeccionar automáticamente tubérculos de papa Chaucha pertenecientes al grupo Phureja, obteniendo información visual y dimensional para identificar defectos externos, signos visibles de brotación y tamaño. Con esta información, el sistema deberá apoyar la clasificación del tubérculo según su prioridad de aprovechamiento poscosecha: **almacenar, procesar pronto o revisar/rechazar**. La necesidad se justifica por la corta vida poscosecha de *Solanum phureja*, la rápida brotación y el trabajo requerido por la inspección manual. (Gamez-Rojas et al., 2025; Sinche Serra et al., 2021; Ruiz Santa Cruz & Sánchez Torres, 2024).                                                        | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Geometría:** La geometría del sistema deberá permitir la manipulación de tubérculos de diferentes tamaños, incluyendo papas pequeñas del grupo Phureja. Seminario-Cunya et al. (2018) reportan que dentro de este grupo pueden encontrarse tubérculos de **2 cm o menos**, por lo que el mecanismo de alimentación, transporte e inspección deberá evitar que los tubérculos pequeños caigan entre elementos móviles o queden atrapados. Las dimensiones generales del prototipo deberán permitir su utilización y transporte dentro de un laboratorio universitario.                                                                                                                                                           | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Cinemática:** La velocidad y tipo de movimiento deberán permitir el desplazamiento controlado de los tubérculos a través de las etapas de alimentación, individualización, inspección y separación. El movimiento deberá favorecer la observación de diferentes regiones de la superficie del tubérculo sin producir golpes significativos. El mecanismo exacto para orientar o rotar la papa será determinado durante la etapa de conceptos de solución, manteniendo la especificación independiente de una solución mecánica particular. Sistemas recientes de procesamiento de papa han demostrado la viabilidad de integrar transporte, orientación mecánica y visión artificial. (Li et al., 2026).                        | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Fuerzas:** Las fuerzas y aceleraciones producidas durante el transporte, individualización y separación no deberán ocasionar cortes, aplastamiento, abrasión ni daños visibles significativos en los tubérculos. Como criterio de validación del prototipo, después de pasar por el sistema deberá verificarse visualmente la ausencia de nuevos daños en al menos el **95 % de una muestra de ensayo**, valor establecido como objetivo interno de diseño. Los impactos mecánicos son relevantes debido a su relación con la aparición de daños y magulladuras en papa.                                                                                                                                                        | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Energía:** El prototipo deberá ser compatible con la alimentación eléctrica disponible en Perú. El Código Nacional de Electricidad establece sistemas de suministro de baja tensión de **220 V** y frecuencia nominal de **60 Hz**. Los subsistemas electrónicos deberán emplear fuentes o convertidores apropiados para las tensiones requeridas por sensores, controlador, cámara y actuadores. Las partes de baja tensión deberán quedar eléctricamente aisladas de la red de alimentación.                                                                                                                                                                                                                                  | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Materia:** La materia de ingreso estará constituida principalmente por tubérculos de **papa Chaucha / grupo Phureja**. Se deberán considerar ejemplares de diferentes tamaños, incluyendo diámetros próximos o inferiores a 2 cm cuando correspondan al cultivar seleccionado. Como variables visibles de calidad se considerarán principalmente deformaciones, daños externos, deterioro y brotación. La materia de salida estará dividida de acuerdo con la decisión de aprovechamiento establecida por el sistema. (Seminario-Cunya et al., 2018; Gamez-Rojas et al., 2025).                                                                                                                                                 | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Señales (Información):** Deberá contar con señales de entrada y salida. **Señales de entrada:** señal de encendido, inicio, parada, detección de presencia del tubérculo, adquisición de imagen y, cuando se disponga de ellas, variables asociadas al lote. **Señales de salida:** estado del sistema, resultado de inspección, categoría asignada al tubérculo, activación del sistema de separación, señal de error, señal de emergencia y señal de fin del proceso.                                                                                                                                                                                                                                                         | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Control:** El sistema de control deberá coordinar los subsistemas mecánicos, electrónicos y computacionales. Deberá controlar el ingreso de tubérculos, su desplazamiento, captura de información, procesamiento de imágenes y accionamiento del mecanismo de separación. Cuando existan varios tubérculos simultáneamente en el sistema, la decisión generada deberá mantenerse asociada al tubérculo correspondiente hasta llegar a la zona de separación.                                                                                                                                                                                                                                                                    | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Electrónico (hardware):** Se utilizará el hardware necesario para adquirir información visual y controlar los actuadores del prototipo. El sistema incluirá como mínimo una unidad de procesamiento, cámara, iluminación controlada, sensores de presencia o posición, controladores de motores y actuadores. La plataforma concreta deberá seleccionarse considerando capacidad de procesamiento, compatibilidad, costo, disponibilidad y posibilidad de reemplazo.                                                                                                                                                                                                                                                            | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Software:** Se deberá implementar un programa que permita adquirir y procesar las imágenes de los tubérculos, ejecutar el algoritmo de visión artificial y producir la clasificación correspondiente. El sistema deberá permitir registrar resultados experimentales para calcular métricas como exactitud, precisión, tiempo de procesamiento y matriz de confusión. Como meta inicial, el módulo de clasificación visual deberá alcanzar una **exactitud mínima del 90 %** sobre un conjunto de prueba independiente. Ruiz Santa Cruz y Sánchez Torres (2024) reportaron 92 % de exactitud y 93 % de precisión promedio en clasificación de defectos externos de *Solanum phureja*, demostrando la factibilidad del objetivo. | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Inspección visual:** La adquisición de imágenes deberá realizarse bajo condiciones de iluminación suficientemente uniformes para reducir sombras, reflejos y variaciones externas. La inspección deberá identificar características visuales relacionadas con la superficie de la papa. La literatura ha demostrado que la visión artificial puede utilizar color, textura, forma e información espectral para identificar defectos en tubérculos. (Barnes et al., 2010; Yang et al., 2023).                                                                                                                                                                                                                                    | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Medición:** El sistema deberá estimar al menos una dimensión representativa del tubérculo para distinguir papas pequeñas de otros tamaños. La medición deberá realizarse de manera repetible y sin contacto destructivo. Los métodos de visión artificial han demostrado capacidad para estimar longitud, ancho, espesor, volumen y tamaño de tubérculos. (Su et al., 2017; Su et al., 2018).                                                                                                                                                                                                                                                                                                                                   | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Comunicaciones:** El controlador deberá comunicarse correctamente con sensores, cámara, actuadores y los demás subsistemas mediante protocolos de comunicación adecuados. La comunicación no deberá interferir con el funcionamiento general de la máquina y deberá mantener la sincronización necesaria entre detección, clasificación y separación.                                                                                                                                                                                                                                                                                                                                                                           | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Seguridad:** El diseño deberá minimizar los riesgos relacionados con partes móviles, motores y conexiones eléctricas. Se deberá incorporar un sistema de parada accesible para el operador y protecciones en aquellas partes móviles que puedan representar riesgo. Se tomarán como referencia los principios de evaluación y reducción de riesgos de **ISO 12100:2010** y la **Ley N.° 29783, Ley de Seguridad y Salud en el Trabajo**.                                                                                                                                                                                                                                                                                        | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Higiene e inocuidad:** Los componentes en contacto con los tubérculos deberán estar fabricados con materiales que no produzcan sustancias tóxicas, no transfieran olores o sabores, sean resistentes a la corrosión y soporten operaciones repetidas de limpieza. Asimismo, las superficies deberán ser lisas y facilitar la limpieza. Estos requisitos se sustentan en los artículos 37 y 38 del **D.S. N.° 007-98-SA**. Como referencia complementaria se considerará ISO 22000:2018 para gestión de inocuidad alimentaria.                                                                                                                                                                                                   | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Ergonomía:** La posición de los elementos de mando, zona de alimentación y zonas de recolección deberá permitir la operación sin adoptar posturas incómodas o peligrosas. Se utilizarán principios antropométricos de **ISO 7250-1:2017** durante la definición dimensional del prototipo.                                                                                                                                                                                                                                                                                                                                                                                                                                      | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Fabricación:** La máquina deberá poder fabricarse utilizando materiales y componentes disponibles en el mercado nacional o mediante importación dentro del periodo académico. El diseño deberá priorizar componentes comerciales y modulares para facilitar su reemplazo. Las partes en contacto con los tubérculos deberán cumplir los criterios higiénicos establecidos en el D.S. N.° 007-98-SA.                                                                                                                                                                                                                                                                                                                             | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Control de calidad:** Se deberán realizar ensayos experimentales para comprobar el cumplimiento de las exigencias. Entre los indicadores se considerarán: **exactitud del algoritmo de clasificación, precisión, tiempo de procesamiento por tubérculo, porcentaje de clasificación correcta, porcentaje de separación correcta, frecuencia de atascos y presencia de daño físico generado por la máquina**. El sistema de visión artificial deberá alcanzar inicialmente una exactitud mínima del 90 %.                                                                                                                                                                                                                        | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Montaje:** Los componentes mecánicos, electrónicos y de visión deberán organizarse modularmente. La estructura deberá permanecer estable durante el funcionamiento de los motores y actuadores. Los módulos de cámara, iluminación, transporte y separación deberán poder desmontarse para realizar ajustes, pruebas y mantenimiento.                                                                                                                                                                                                                                                                                                                                                                                           | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Transporte:** Las dimensiones y masa del prototipo deberán permitir su traslado dentro de las instalaciones de la universidad por los integrantes del equipo, evitando equipos de carga industrial. Los componentes sensibles como cámaras, sensores y electrónica deberán contar con medios de protección o desmontaje durante el traslado.                                                                                                                                                                                                                                                                                                                                                                                    | Equipo Kartoffelmachine |
| 20/08/26            |           D           | **Uso:** El prototipo será diseñado principalmente para funcionar en un ambiente interior controlado. La zona de adquisición de imágenes deberá reducir la influencia de cambios de iluminación ambiental. Barnes et al. (2010) señalan que las condiciones de iluminación y la variabilidad natural del producto pueden influir en la inspección visual automatizada.                                                                                                                                                                                                                                                                                                                                                            | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Mantenimiento:** Los componentes mecánicos deberán disponer de acceso para inspección, limpieza, ajuste o reemplazo. Los componentes electrónicos deberán poder cambiarse individualmente. Las zonas en contacto con la papa deberán desmontarse o permitir una limpieza completa, conforme con el principio de diseño higiénico establecido en el artículo 38 del D.S. N.° 007-98-SA.                                                                                                                                                                                                                                                                                                                                          | Equipo Kartoffelmachine |
| 20/08/26            |           D           | **Costos:** El diseño deberá priorizar soluciones de costo accesible mediante componentes comerciales y reutilizables. El presupuesto deberá incluir estructura, sistema de transporte, motores, cámara, iluminación, sensores, unidad de procesamiento, actuadores, componentes eléctricos y materiales de fabricación. El costo máximo deberá establecerse posteriormente de acuerdo con el presupuesto aprobado por el equipo y el curso, evitando establecer en esta etapa un valor sin sustento.                                                                                                                                                                                                                             | Equipo Kartoffelmachine |
| 20/08/26            |           E           | **Plazos:** El proyecto será desarrollado durante el periodo académico **2026-2**. La planificación seguirá las etapas de definición de necesidades y requisitos, arquitectura, diseño de subsistemas, integración, verificación y validación, de acuerdo con el enfoque interdisciplinario establecido por **VDI/VDE 2206:2021** para el desarrollo de sistemas mecatrónicos y ciberfísicos.                                                                                                                                                                                                                                                                                                                                     | Equipo Kartoffelmachine |

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

# Bibliografía

## Lista de Requerimientos

**Gamez-Rojas, G., Fuertes-Guerrero, C., & Mejía-España, D. (2025).**
*Fumigación con etanol como tratamiento para inhibir la brotación en papa criolla colombiana (Solanum Phureja).* TecnoLógicas, 28(63), e3278.
DOI: **10.22430/22565337.3278**.

Esta investigación demuestra la corta vida útil poscosecha de *Solanum phureja* asociada a la rápida brotación. En el tratamiento testigo se registró un índice de brotación de 82,8 % durante el periodo experimental, sustentando la necesidad de evaluar rápidamente la condición poscosecha del tubérculo.

---

**Sinche Serra, M. V., Anguisaca Totasig, E. P., & Cuesta Plúa, M. C. (2021).**
*Tratamiento postcosecha con radiación gamma para extender la vida útil de papa chaucha amarilla (Solanum phureja).* ACI Avances en Ciencias e Ingenierías, 12(3), 18.
DOI: **10.18272/aci.v12i3.2020**.

La investigación analiza el deterioro y brotación durante el almacenamiento de papa Chaucha amarilla, respaldando la necesidad de identificar signos visibles asociados con el estado poscosecha.

---

**Seminario-Cunya, J. F., Villanueva-Guevara, R., & Valdez-Yopla, M. H. (2018).**
*Rendimiento de cultivares de papa (Solanum tuberosum L.) amarillos precoces del grupo Phureja.* Agronomía Mesoamericana, 29(3), 639–653.
DOI: **10.15517/ma.v29i3.32623**.

La investigación caracteriza cultivares del grupo Phureja de Cajamarca y reporta tubérculos pequeños, incluso de alrededor de 2 cm o menos, además de diferentes destinos de procesamiento asociados al tamaño.

---

**Ruiz Santa Cruz, Y. F., & Sánchez Torres, M. R. (2024).**
*Método de clasificación automática para defectos externos con actualización manual de Solanum phureja para las exigencias de percepción de calidad.* Tesis de grado, Universidad Señor de Sipán. ALICIA-CONCYTEC.

La investigación identifica que la clasificación realizada por productores es manual y que descartar tubérculos con daños externos demanda trabajo y tiempo. Su método de clasificación mediante redes neuronales reportó **92 % de exactitud y 93 % de precisión promedio**.

---

**Ministerio de Salud del Perú. (1998).**
*Decreto Supremo N.° 007-98-SA. Reglamento sobre Vigilancia y Control Sanitario de Alimentos y Bebidas.*

El **Artículo 37** establece que los equipos y utensilios empleados en manipulación de alimentos deben fabricarse con materiales que no emitan sustancias tóxicas, no transfieran olores o sabores, no sean absorbentes, resistan la corrosión y soporten operaciones repetidas de limpieza y desinfección.

El **Artículo 38** establece que los equipos deberán diseñarse para permitir una fácil y completa limpieza y desinfección.

---

**Congreso de la República del Perú. (2011).**
*Ley N.° 29783 — Ley de Seguridad y Salud en el Trabajo.*

Se utiliza como referencia para considerar la prevención de riesgos y protección del operador durante el funcionamiento del prototipo.

---

**ISO. (2010).**
*ISO 12100:2010 — Safety of machinery — General principles for design — Risk assessment and risk reduction.*

Proporciona principios para identificar peligros, evaluar riesgos y aplicar medidas de reducción del riesgo durante el diseño de maquinaria.

---

**ISO. (2017).**
*ISO 7250-1:2017 — Basic human body measurements for technological design — Part 1: Body measurement definitions and landmarks.*

Se utilizará como referencia para considerar parámetros antropométricos durante el diseño ergonómico de las zonas de operación del equipo.

---

**ISO. (2018).**
*ISO 22000:2018 — Food safety management systems — Requirements for any organization in the food chain.*

Se utiliza como referencia general para los aspectos relacionados con inocuidad en sistemas que intervienen dentro de una cadena alimentaria.

---

**Ministerio de Energía y Minas del Perú.**
*Código Nacional de Electricidad — Utilización.*

Las disposiciones sobre alimentación desde redes de servicio público contemplan sistemas monofásicos de **220 V** y una frecuencia nominal de **60 Hz**, valores considerados para la alimentación principal del prototipo.

---

**VDI / VDE. (2021).**
*VDI/VDE 2206 — Development of mechatronic and cyber-physical systems.*

La norma proporciona un marco para el desarrollo interdisciplinario de sistemas mecatrónicos y ciberfísicos y será utilizada como metodología principal de desarrollo del proyecto Kartoffelmachine.

---

# Estado del Arte

**Barnes, M., Duckett, T., Cielniak, G., Stroud, G., & Harper, G. (2010).**
*Visual detection of blemishes in potatoes using minimalist boosted classifiers.* Journal of Food Engineering, 98(3), 339–346.
DOI: **10.1016/j.jfoodeng.2010.01.010**.

El trabajo desarrolló un sistema de visión para detectar defectos superficiales en papa mediante características de color y textura. Reportó aproximadamente **89,6 % y 89,5 % de exactitud** para variedades de papa blanca y roja.

---

**ElMasry, G., Cubero, S., Moltó, E., & Blasco, J. (2012).**
*A real-time mathematical computer method for potato inspection using machine vision.* Computers & Mathematics with Applications, 63(1), 268–279.
DOI: **10.1016/j.camwa.2011.11.019**.

Propone inspección automática de papas mediante visión artificial, combinando clasificación por tamaño y detección de defectos externos.

---

**Su, Q., Kondo, N., Li, M., Sun, H., & Al Riza, D. F. (2017).**
*Potato feature prediction based on machine vision and 3D model rebuilding.* Computers and Electronics in Agriculture, 137, 41–51.
DOI: **10.1016/j.compag.2017.03.020**.

Demuestra la posibilidad de obtener características dimensionales como longitud, ancho, espesor, volumen y masa mediante visión artificial y reconstrucción tridimensional.

---

**Su, Q., Kondo, N., Li, M., Sun, H., Al Riza, D. F., & Habaragamuwa, H. (2018).**
*Potato quality grading based on machine vision and 3D shape analysis.* Computers and Electronics in Agriculture, 152, 261–268.

El sistema empleó información bidimensional y tridimensional para clasificación de calidad, detección de deformaciones y estimación del tamaño de los tubérculos.

---

**Yang, Y., Liu, Z., Huang, M., Zhu, Q., & Zhao, X. (2023).**
*Automatic detection of multi-type defects on potatoes using multispectral imaging combined with a deep learning model.* Journal of Food Engineering, 336, 111213.
DOI: **10.1016/j.jfoodeng.2022.111213**.

El trabajo evaluó papas sanas y papas con diferentes defectos, incluyendo brotación, sarna común, pudrición seca y magulladuras. El modelo propuesto alcanzó un **mAP de 90,26 %**.

---

**Ruiz Santa Cruz, Y. F., & Sánchez Torres, M. R. (2024).**
*Método de clasificación automática para defectos externos con actualización manual de Solanum phureja para las exigencias de percepción de calidad.* Universidad Señor de Sipán.

Es uno de los antecedentes más cercanos a Kartoffelmachine debido a que trabaja específicamente con *Solanum phureja* y clasificación automática de defectos externos.

---

**HCRP-YOLO. (2025).**
*HCRP-YOLO: A lightweight algorithm for potato defect detection.* Smart Agricultural Technology, 10, 100849.
DOI: **10.1016/j.atech.2025.100849**.

Propone una arquitectura ligera basada en YOLO orientada a detectar defectos externos de papa, demostrando el interés actual por sistemas de visión artificial capaces de operar con menor costo computacional.

---

**Li, J., Sun, W., Meng, Y., Liu, K., & Simionescu, P. A. (2026).**
*Design and experimental study of a seed potato cutting machine and its machine vision-based defective tuber removal system.* Computers and Electronics in Agriculture, 249, 111818.
DOI: **10.1016/j.compag.2026.111818**.

Presenta un sistema integrado de procesamiento de papa que combina alimentación, orientación mecánica, transporte, visión artificial y separación automática. Constituye un antecedente importante para demostrar que la innovación de Kartoffelmachine no debe formularse simplemente como “usar una cámara y una IA para clasificar papas”, sino en la solución específica desarrollada para tubérculos Phureja pequeños y para la decisión de aprovechamiento poscosecha.

---

# Proyecto preliminar

**Seminario-Cunya, J. F., Villanueva-Guevara, R., & Valdez-Yopla, M. H. (2018).**
*Rendimiento de cultivares de papa (Solanum tuberosum L.) amarillos precoces del grupo Phureja.*
DOI: **10.15517/ma.v29i3.32623**.

Fuente utilizada para establecer las características dimensionales de la materia prima y la necesidad de que el mecanismo pueda manipular tubérculos pequeños.

---

**Gamez-Rojas, G., Fuertes-Guerrero, C., & Mejía-España, D. (2025).**
*Fumigación con etanol como tratamiento para inhibir la brotación en papa criolla colombiana (Solanum Phureja).*
DOI: **10.22430/22565337.3278**.

Fuente utilizada para caracterizar la problemática de vida poscosecha reducida y rápida brotación.

---

**Sinche Serra, M. V., Anguisaca Totasig, E. P., & Cuesta Plúa, M. C. (2021).**
*Tratamiento postcosecha con radiación gamma para extender la vida útil de papa chaucha amarilla (Solanum phureja).*
DOI: **10.18272/aci.v12i3.2020**.

Fuente utilizada para analizar cambios de calidad, brotación, pérdida de peso y deterioro durante el almacenamiento.

---

**D.S. N.° 007-98-SA.**
*Reglamento sobre Vigilancia y Control Sanitario de Alimentos y Bebidas.*

Fuente utilizada para la selección preliminar de materiales y definición de superficies destinadas al contacto con el tubérculo.

---

**ISO 12100:2010.**
*Safety of machinery — General principles for design — Risk assessment and risk reduction.*

Fuente utilizada para el diseño preliminar de elementos de seguridad y análisis de riesgos.

---

**ISO 7250-1:2017.**
*Basic human body measurements for technological design.*

Fuente utilizada como referencia para definir dimensiones asociadas a la interacción del operador con el prototipo.

---

# Proyecto definitivo

Las siguientes fuentes deberán emplearse durante la selección final de los algoritmos, componentes mecánicos y hardware del prototipo.

**Barnes, M., Duckett, T., Cielniak, G., Stroud, G., & Harper, G. (2010).**
*Visual detection of blemishes in potatoes using minimalist boosted classifiers.*
DOI: **10.1016/j.jfoodeng.2010.01.010**.

Referencia para procesamiento de características visuales de la superficie del tubérculo.

---

**Su, Q., Kondo, N., Li, M., Sun, H., & Al Riza, D. F. (2017).**
*Potato feature prediction based on machine vision and 3D model rebuilding.*
DOI: **10.1016/j.compag.2017.03.020**.

Referencia para estimación de dimensiones mediante visión artificial.

---

**Yang, Y., Liu, Z., Huang, M., Zhu, Q., & Zhao, X. (2023).**
*Automatic detection of multi-type defects on potatoes using multispectral imaging combined with a deep learning model.*
DOI: **10.1016/j.jfoodeng.2022.111213**.

Referencia para modelos de detección automática de múltiples defectos.

---

**Ruiz Santa Cruz, Y. F., & Sánchez Torres, M. R. (2024).**
*Método de clasificación automática para defectos externos con actualización manual de Solanum phureja para las exigencias de percepción de calidad.*

Referencia directa para el entrenamiento y evaluación de modelos de clasificación aplicados a papa Phureja.

---

**Li, J., Sun, W., Meng, Y., Liu, K., & Simionescu, P. A. (2026).**
*Design and experimental study of a seed potato cutting machine and its machine vision-based defective tuber removal system.* Computers and Electronics in Agriculture, 249, 111818.
DOI: **10.1016/j.compag.2026.111818**.

Referencia para integración mecatrónica entre transporte, manipulación, visión artificial y separación automática.

---

**VDI/VDE 2206. (2021).**
*Development of mechatronic and cyber-physical systems.*

Referencia metodológica para la especificación, diseño interdisciplinario, integración, verificación y validación de Kartoffelmachine.

---

# Fuentes principales utilizadas para sustentar las exigencias

| **Fuente**                              | **Información que aporta al proyecto**                                                     |
| --------------------------------------- | ------------------------------------------------------------------------------------------ |
| Gamez-Rojas et al. (2025)               | Corta vida poscosecha y rápida brotación de *Solanum phureja*.                             |
| Sinche Serra et al. (2021)              | Deterioro, brotación y cambios durante almacenamiento de papa Chaucha.                     |
| Seminario-Cunya et al. (2018)           | Características y tamaños de tubérculos del grupo Phureja, incluyendo tubérculos pequeños. |
| Ruiz Santa Cruz & Sánchez Torres (2024) | Selección manual, defectos externos y clasificación automática de *Solanum phureja*.       |
| Barnes et al. (2010)                    | Detección de defectos superficiales mediante color y textura.                              |
| Su et al. (2017; 2018)                  | Medición dimensional y evaluación de calidad mediante visión artificial.                   |
| Yang et al. (2023)                      | Detección automática de múltiples defectos mediante deep learning.                         |
| Li et al. (2026)                        | Integración de orientación, transporte, visión artificial y separación de papa.            |
| D.S. N.° 007-98-SA                      | Materiales, higiene, limpieza y diseño de equipos relacionados con alimentos.              |
| Ley N.° 29783                           | Seguridad y salud durante la operación.                                                    |
| ISO 12100:2010                          | Evaluación y reducción de riesgos de maquinaria.                                           |
| ISO 7250-1:2017                         | Ergonomía y antropometría.                                                                 |
| ISO 22000:2018                          | Gestión de inocuidad alimentaria.                                                          |
| Código Nacional de Electricidad         | Alimentación de 220 V y frecuencia de 60 Hz.                                               |
| VDI/VDE 2206:2021                       | Metodología de desarrollo mecatrónico e integración del sistema.                           |
