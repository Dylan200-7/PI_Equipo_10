
# TRL 1 — KARTOFFELMASCHINE

## Fundamentos científicos, estado del arte y documentación de los componentes seleccionados

**Proyecto:** Sistema mecatrónico de inspección y clasificación visual de papa Chaucha.

**Nivel de madurez tecnológica:** TRL 1 — Principios básicos observados e identificados.

**Fuente para la selección técnica:** Matriz morfológica de KARTOFFELMASCHINE, ruta indicada mediante flechas azules (alternativa 1 de cada función).

---

## 1. Introducción

La papa es uno de los cultivos más relevantes para la alimentación y la economía de numerosos países. Sin embargo, durante las etapas poscosecha pueden producirse pérdidas asociadas con la manipulación, el almacenamiento, el transporte y la comercialización, lo que hace importante mejorar los procedimientos de inspección y clasificación [1].

La selección tradicional suele efectuarse mediante inspección visual humana o mediante equipos que consideran propiedades como tamaño, forma y peso. La inspección manual depende de la experiencia del operario y de las condiciones de trabajo, mientras que los métodos exclusivamente dimensionales no identifican necesariamente defectos superficiales. Por esta razón, se investigan tecnologías de visión artificial y aprendizaje automático capaces de analizar las imágenes de los productos [2], [3].

**Kartoffelmaschine** propone un sistema mecatrónico para apoyar la clasificación de papa Chaucha según su **apariencia externa**, diferenciando papas sin defectos visibles de aquellas que presentan características superficiales no deseadas. La propuesta combina alimentación y transporte mecánico, orientación del producto, captura de imágenes, análisis mediante inteligencia artificial y separación física.

Como parte de la documentación de este **TRL 1**, además de revisar artículos científicos y patentes, se registran los **21 componentes, materiales y tecnologías seleccionados en la matriz morfológica**, exclusivamente los correspondientes a las **flechas azules**.

Esta identificación describe la solución de diseño del equipo; no implica que todos los componentes se hayan comprado, montado o validado experimentalmente. Esas evidencias corresponderán a los siguientes niveles TRL.

---

## 2. Objetivos

### 2.1. Objetivo general

Identificar los principios científicos y tecnológicos que sustentan Kartoffelmaschine y documentar la solución técnica seleccionada para un sistema automatizado de clasificación visual de papa Chaucha.

### 2.2. Objetivos específicos

- Investigar métodos de inspección y clasificación poscosecha de papa, en particular visión artificial y aprendizaje automático.
- Examinar artículos científicos y patentes relacionados con la identificación de defectos externos y la separación automatizada.
- Registrar los componentes, materiales y tecnologías elegidos mediante la ruta de flechas azules de la matriz morfológica y describir su función.
- Relacionar los antecedentes científicos con el funcionamiento conceptual del prototipo e identificar sus limitaciones.

---

## 3. Estado del arte y principios tecnológicos

### 3.1. Inspección poscosecha y visión artificial

La clasificación poscosecha puede considerar atributos físicos o visuales, entre ellos tamaño, color, forma, deformaciones, manchas y alteraciones superficiales.

La visión artificial permite obtener imágenes y analizarlas digitalmente mediante etapas de captura, preprocesamiento, identificación de características y asignación de una categoría [2].

Su et al. estudiaron la clasificación de papa mediante visión artificial y análisis de forma tridimensional [2]. Este antecedente muestra que la información visual y geométrica resulta útil para evaluar características del producto.

No obstante, el uso de una cámara convencional, como la seleccionada para Kartoffelmaschine, **no equivale** a disponer de un sistema de imágenes de profundidad o de inspección del interior de la papa.

### 3.2. Aprendizaje automático para detectar características externas

El aprendizaje automático utiliza datos de ejemplo para aprender patrones y generar predicciones sobre nuevas observaciones.

En el análisis de imágenes agrícolas se emplean redes neuronales y modelos de detección de objetos.

Su et al. investigaron una red neuronal convolucional para clasificar la calidad de papas mediante imágenes de profundidad [3].

Por su parte, Li et al. desarrollaron un método mejorado basado en YOLOv5s para la detección de defectos externos en papas [9].

Como alternativa elegida para Kartoffelmaschine, la matriz morfológica señala **YOLOv8n**, una variante compacta del enfoque YOLO.

Su incorporación se plantea para reconocer atributos visibles a partir de las imágenes capturadas; los resultados publicados para otros modelos o variedades no representan el rendimiento demostrado de YOLOv8n en papa Chaucha.

### 3.3. Integración mecatrónica y sincronización

Una clasificadora automatizada integra alimentación, transporte, inspección, procesamiento de señales, control y separación.

El producto debe ser detectado y fotografiado en una posición adecuada; posteriormente, el resultado del análisis debe asociarse correctamente con la papa que llega al mecanismo de desvío.

En Kartoffelmaschine, la combinación conceptual de una **mini faja de PVC**, una **mesa de inspección por rodillos**, una **pin conveyor chain**, sensores, motores, cámara y compuerta busca resolver esas funciones.

La sincronización entre captura, desplazamiento y separación constituye un aspecto por probar en el futuro.

---

## 4. Artículos científicos relacionados

| Referencia | Hallazgo o aporte científico | Relación con Kartoffelmaschine |
|---|---|---|
| FAO, 2010 [1] | Analiza aspectos de la cadena de valor de la papa y su desarrollo. | Contextualiza la necesidad de mejorar la operación poscosecha. |
| Su et al., 2018 [2] | Estudian clasificación de calidad mediante visión artificial y análisis 3D de forma. | Sustenta el principio de inspección por imágenes, aunque nuestra selección no incluye una cámara de profundidad. |
| Su et al., 2020 [3] | Investigan clasificación de papa mediante imágenes de profundidad y una CNN. | Proporciona antecedentes del uso de aprendizaje profundo para clasificación. |
| X. Li et al., 2025 [9] | Desarrollan un método mejorado basado en YOLOv5s para detectar defectos externos. | Respalda el enfoque de detección visual con la familia YOLO, sin confundir YOLOv5s con el YOLOv8n elegido. |

Estos trabajos muestran la pertinencia de investigar la automatización de la inspección, pero no permiten afirmar todavía que Kartoffelmaschine haya alcanzado una precisión determinada.

Además, los defectos internos o problemas de inocuidad no pueden descartarse únicamente a partir de imágenes externas.

---

## 5. Patentes relacionadas

La búsqueda de antecedentes tecnológicos permite conocer distintas formas de combinar captura de imágenes, procesamiento y mecanismos de separación.

Las patentes siguientes sirven como referencias técnicas; su inclusión no supone que Kartoffelmaschine reproduzca sus reivindicaciones ni constituye un análisis de libertad de operación.

### 5.1. CN109030504B — Panoramic potato defect detection device and method based on virtual and real imaging combination

Esta patente [4] presenta una solución de inspección de papa que combina imágenes reales y virtuales para examinar distintas superficies, utiliza procesamiento basado en redes neuronales y contempla la separación del producto.

Su interés para el proyecto reside en la búsqueda de mayor cobertura visual y en el acoplamiento de inspección y separación.

### 5.2. US9114436B2 — Method for Sorting Potato Products and Sorting Apparatus for Potato Products

Esta patente [5] describe un procedimiento de clasificación de productos de papa basado en mediciones ópticas y retirada de productos con condiciones no deseadas.

Constituye un antecedente de separación automatizada, aunque sus métodos ópticos no son equivalentes a una cámara RGB convencional.

### 5.3. US9527115B2 — Computer Vision and Machine Learning Software for Grading and Sorting Plants

Esta patente [6] expone una arquitectura que combina visión por computadora, aprendizaje automático y mecanismos de separación.

Se desarrolló en el ámbito de plantas, no específicamente de papa Chaucha; por ello se cita como referencia de integración y no como validación de nuestra propuesta.

### 5.4. Comparación de las patentes

| Patente | Tecnología relevante | Relación conceptual con el proyecto |
|---|---|---|
| CN109030504B [4] | Inspección de varias superficies y separación. | Motiva considerar un mecanismo que oriente las papas antes de clasificarlas. |
| US9114436B2 [5] | Análisis óptico y retirada automatizada. | Sustenta la necesidad de vincular la decisión de inspección con la separación física. |
| US9527115B2 [6] | Visión artificial, aprendizaje automático y accionamiento. | Referencia de una arquitectura mecatrónica integrada. |

---

## 6. Solución conceptual propuesta para Kartoffelmaschine

La propuesta se organiza en una secuencia funcional:

**Alimentación → Transporte → Orientación → Captura de imágenes → Procesamiento mediante IA → Separación → Presentación de resultados.**

### 6.1. Alimentación

La papa ingresa mediante una tolva por gravedad fabricada en PETG y pasa a una mini faja de PVC.

### 6.2. Inspección y orientación

La mesa de rodillos, la pin conveyor chain y dos motorreductores DC JGA25-370 se proponen para posicionar y orientar la papa durante la inspección.

### 6.3. Detección y captura

Un sensor E18-D80NK identifica la presencia del producto.

Un encoder incremental de 600 PPR ofrece información del movimiento del elemento al que se acople.

La Raspberry Pi Camera Module 3 registra las imágenes.

### 6.4. Procesamiento

Una Raspberry Pi 5 de 8 GB ejecutaría el procesamiento y el modelo seleccionado YOLOv8n para asignar una categoría visual.

### 6.5. Separación

Una compuerta accionada mediante servomotor MG996R desviaría la papa hacia la recepción prevista, compuesta por una compuerta con bandeja.

### 6.6. Comunicación

Indicadores LED de 5 mm, el Wi-Fi integrado de la Raspberry Pi y una interfaz web desarrollada con Flask/HTML permitirían supervisar el estado y los resultados.

La estructura se plantea en aluminio, con soportes y piezas personalizadas en PETG eSUN impreso en 3D y rodillos recubiertos de TPU 95A en la zona de contacto.

La alimentación eléctrica se definirá a partir de los tres elementos seleccionados en la matriz, verificando las exigencias reales de tensión, corriente y conexión durante el diseño eléctrico.

---

## 7. Documentación de los componentes y materiales seleccionados

### 7.1. Criterio de selección

La **Matriz morfológica — KARTOFFELMASCHINE** presenta 21 funciones organizadas en cinco subsistemas y tres alternativas por función.

Se ha considerado **únicamente la ruta marcada con flechas azules**, que corresponde a la **alternativa 1 en las 21 funciones**.

En las tablas siguientes se presentan los elementos seleccionados y se explica su finalidad dentro del prototipo.

**Alcance:** Se trata del inventario seleccionado para la propuesta de diseño. La matriz no certifica existencias físicas, compras, montaje ni pruebas.

El término «materiales» se usa aquí en sentido amplio e incluye componentes, dispositivos y herramientas de software.

### 7.2. Subsistema de energía (3 elementos)

Este subsistema tiene como finalidad suministrar la energía eléctrica necesaria para el funcionamiento de los componentes electrónicos y los actuadores mecánicos.

| N.º | Elemento seleccionado (flecha azul) | Función prevista |
|---|---|---|
| 1 | Fuente Mean Well 12 V | Proporcionar la alimentación eléctrica general prevista para el sistema. |
| 2 | Fuente switching 12 V | Alimentar los actuadores de acuerdo con la distribución eléctrica propuesta. |
| 3 | Buck XL4015 a 5 V | Reducir la tensión para la Raspberry Pi y la electrónica que requiera 5 V, sujeto a la verificación de corriente y compatibilidad. |

Las dos fuentes de 12 V figuran como selecciones distintas porque responden a funciones diferentes de la matriz.

Durante el diseño se deberá comprobar si ambas son necesarias y cómo se distribuye adecuadamente la potencia.

### 7.3. Subsistema de procesamiento y control de señales (5 elementos)

Este subsistema constituye la parte encargada de obtener y analizar la información visual de las papas y proporcionar señales para el control del mecanismo.

| N.º | Elemento seleccionado (flecha azul) | Función prevista |
|---|---|---|
| 4 | Raspberry Pi 5, 8 GB RAM | Unidad de procesamiento de imágenes y coordinación del control. |
| 5 | Raspberry Pi Camera Module 3 | Captura de imágenes de la superficie de las papas. |
| 6 | YOLOv8n | Modelo de inteligencia artificial propuesto para la detección o clasificación visual; es software, no un material físico. |
| 7 | Sensor E18-D80NK | Detección de presencia de una papa en el área de inspección. |
| 8 | Encoder rotativo incremental 600 PPR | Medición del giro o desplazamiento del mecanismo al que se incorpore. |

La selección de la Raspberry Pi 5 y el módulo de cámara responde a la necesidad de obtener y procesar imágenes en un sistema compacto.

Asimismo, YOLOv8n constituye la tecnología de aprendizaje automático propuesta para identificar características externas y apoyar la clasificación.

### 7.4. Subsistema mecánico (7 elementos)

Este subsistema tiene como finalidad permitir el ingreso, transporte, orientación y separación de las papas durante el funcionamiento del prototipo.

| N.º | Elemento seleccionado (flecha azul) | Función prevista |
|---|---|---|
| 9 | Tolva por gravedad PETG | Recepción de papas y alimentación hacia el sistema de transporte. |
| 10 | Mini faja PVC | Desplazamiento de las papas desde la recepción hasta la inspección. |
| 11 | Mesa de inspección por rodillos | Sostener y transportar las papas durante la inspección. |
| 12 | Pin conveyor chain | Mecanismo de cadena con pasadores seleccionado para apoyar el giro u orientación de las papas. |
| 13 | 2 motorreductores DC JGA25-370 | Accionamiento previsto del mecanismo de giro. |
| 14 | Compuerta accionada por servo MG996R | Realizar la desviación de papas según la categoría asignada. |
| 15 | Compuerta con bandeja | Recibir las papas después de la separación. |

La implementación de un mecanismo de orientación constituye una característica importante del diseño, ya que busca permitir la observación de distintas superficies de la papa y reducir las zonas que podrían quedar fuera del campo de visión de la cámara.

### 7.5. Subsistema de comunicación (3 elementos)

Este subsistema permitirá informar al operador sobre el funcionamiento del equipo y los resultados del proceso de clasificación.

| N.º | Elemento seleccionado (flecha azul) | Función prevista |
|---|---|---|
| 16 | LEDs indicadores 5 mm | Mostrar información básica del estado del sistema y la clasificación. |
| 17 | Wi-Fi integrado de Raspberry Pi 5 | Enviar resultados e información sin incorporar un módulo externo de comunicación. |
| 18 | Interfaz web mediante Flask/HTML | Presentar información para la supervisión e interacción del operador; corresponde a software. |

La interfaz web facilitará la supervisión de los resultados, mientras que los indicadores LED ofrecerán una señalización visual básica durante el funcionamiento del prototipo.

### 7.6. Subsistema de materiales y estructura (3 elementos)

Los materiales estructurales se seleccionaron considerando su aplicación en la fabricación y el montaje de los diferentes componentes mecánicos.

| N.º | Material seleccionado (flecha azul) | Función prevista |
|---|---|---|
| 19 | Aluminio | Construcción de la estructura principal. |
| 20 | PETG eSUN impreso en 3D | Fabricación de soportes y piezas personalizadas para el prototipo. |
| 21 | Rodillo recubierto de TPU 95A | Proporcionar contacto con la papa durante las operaciones de giro u orientación. |

El aluminio constituye la opción seleccionada para la estructura principal, mientras que el PETG permite fabricar piezas personalizadas mediante impresión 3D.

Por su parte, el recubrimiento de TPU 95A se propone como superficie de contacto en el sistema de rodillos.

### 7.7. Resumen de los componentes seleccionados

| Subsistema | Cantidad de elementos |
|---|---:|
| Energía | 3 |
| Procesamiento y control de señales | 5 |
| Mecánica | 7 |
| Comunicación | 3 |
| Materiales y estructura | 3 |
| **Total** | **21** |

La documentación presentada corresponde exclusivamente a los 21 elementos seleccionados mediante las flechas azules de la matriz morfológica.

No se incorporan las alternativas 2 o 3 de la matriz.

### 7.8. Relación de las selecciones con los principios estudiados

| Principio tecnológico respaldado por antecedentes | Componentes seleccionados en Kartoffelmaschine | Justificación del diseño |
|---|---|---|
| Captura y análisis de imágenes [2], [3] | Raspberry Pi Camera Module 3 y Raspberry Pi 5 | Disponer de una plataforma para adquirir y procesar imágenes de la superficie. |
| Aprendizaje profundo para detección visual [3], [9] | YOLOv8n | Explorar una clasificación automatizada basada en características visuales. |
| Inspección de distintas superficies [4] | Mesa de rodillos, pin conveyor chain, dos motorreductores y rodillo TPU 95A | Proponer un mecanismo de orientación para reducir las superficies no observadas. |
| Separación física basada en la inspección [4]–[6] | Compuerta con servo MG996R y compuerta con bandeja | Relacionar el resultado computacional con un mecanismo de salida. |
| Integración del control mecatrónico | Sensor E18-D80NK, encoder y elementos de alimentación y comunicación | Posibilitar coordinación y monitoreo durante una implementación futura. |

---

## 8. Relación con los Objetivos de Desarrollo Sostenible

### 8.1. ODS 12 — Producción y consumo responsables

La meta 12.3 plantea reducir las pérdidas de alimentos en las cadenas de producción y suministro [7].

Kartoffelmaschine se relaciona con este objetivo al estudiar una herramienta para realizar una inspección visual más sistemática.

No puede afirmarse aún que el diseño reduzca pérdidas: será necesario evaluarlo con datos reales.

### 8.2. ODS 9 — Industria, innovación e infraestructura

Este objetivo impulsa la innovación tecnológica [8].

El proyecto se vincula con él mediante la integración propuesta de mecánica, electrónica, visión artificial y aprendizaje automático para una operación agrícola poscosecha.

---

## 9. Limitaciones y aspectos por verificar

- **Definición de categorías:** «Buen estado» y «mal estado» deben traducirse en criterios visuales reproducibles. Una fotografía no verifica por sí sola condiciones internas o inocuidad.

- **Variabilidad de la papa Chaucha:** Forma, tamaño, color y apariencia pueden modificar el rendimiento de una clasificación automatizada.

- **Adquisición de imágenes:** Iluminación, enfoque, distancia, fondo y posición influyen en los datos que recibirá el modelo.

- **Orientación mecánica:** La cadena y los rodillos deberán demostrar que exponen suficientes superficies sin causar daños al producto.

- **Sincronización:** Deberá garantizarse que la decisión del modelo corresponda a la papa correcta cuando se active la compuerta.

- **Alimentación eléctrica y conexiones:** Deberán verificarse la necesidad de dos fuentes de 12 V, la capacidad del convertidor a 5 V y la compatibilidad eléctrica de cada dispositivo.

- **Evidencia de implementación:** La matriz morfológica documenta una selección, no ensayos, fotografías de montaje, pruebas de precisión ni validación del prototipo.

---

## 10. Conclusiones

El análisis de literatura científica y patentes permitió reconocer fundamentos tecnológicos para investigar la inspección y clasificación visual de papa Chaucha mediante procesamiento de imágenes, aprendizaje automático e integración mecatrónica [2]–[6], [9].

Los antecedentes sustentan la **posibilidad de estudiar el concepto**, pero no constituyen una demostración experimental del funcionamiento de Kartoffelmaschine.

Se documentó además la solución específica seleccionada en la matriz morfológica: **21 elementos correspondientes exclusivamente a las flechas azules**, distribuidos entre energía, procesamiento y control, mecánica, comunicación, y materiales y estructura.

Esta información concreta cómo se propone implementar el sistema y evita confundir los antecedentes científicos con los componentes escogidos.

Por tanto, el resultado del **TRL 1** es una base científica y documental coherente que reúne el problema de inspección poscosecha, los principios tecnológicos aplicables y un inventario conceptual claramente identificado.

El análisis detallado del diseño, la prueba de concepto y la validación experimental deberán desarrollarse y registrarse en las etapas TRL posteriores.

---

## 11. Referencias bibliográficas (formato IEEE)

[1] N. Cromme, A. B. Prakash, N. Lutaladio y F. Ezeta, Eds., *Strengthening Potato Value Chains: Technical and Policy Options for Developing Countries*. Roma, Italia: Food and Agriculture Organization of the United Nations, 2010. [En línea]. Disponible: https://www.fao.org/4/i1710e/i1710e.pdf

[2] Q. Su, N. Kondo, M. Li, H. Sun, D. F. Al Riza y H. Habaragamuwa, “Potato quality grading based on machine vision and 3D shape analysis,” *Computers and Electronics in Agriculture*, vol. 152, pp. 261–268, 2018, doi: 10.1016/j.compag.2018.07.012.

[3] Q. Su, N. Kondo, D. F. Al Riza y H. Habaragamuwa, “Potato quality grading based on depth imaging and convolutional neural network,” *Journal of Food Quality*, vol. 2020, art. 8815896, 2020, doi: 10.1155/2020/8815896.

[4] Zhengzhou University of Light Industry, “Panoramic potato defect detection device and method based on virtual and real imaging combination,” patente china CN109030504B, 2020. [En línea]. Disponible: https://patents.google.com/patent/CN109030504B/en

[5] P. Berghmans, C. Fivez y J. Speybrouck, “Method for sorting potato products and sorting apparatus for potato products,” patente estadounidense US9114436B2, 2015. [En línea]. Disponible: https://patents.google.com/patent/US9114436B2/en

[6] D. A. LaRose, C. C. Fromme, D. J. Stager, M. K. Sergi-Curfman, J. A. Bagnell, E. A. Cuzzillo y L. D. Baker, “Computer vision and machine learning software for grading and sorting plants,” patente estadounidense US9527115B2, 2016. [En línea]. Disponible: https://patents.google.com/patent/US9527115B2/en

[7] Naciones Unidas, “Objetivo 12: Garantizar modalidades de consumo y producción sostenibles.” [En línea]. Disponible: https://www.un.org/sustainabledevelopment/es/sustainable-consumption-production/

[8] Naciones Unidas, “Objetivo 9: Construir infraestructuras resilientes, promover la industrialización sostenible y fomentar la innovación.” [En línea]. Disponible: https://www.un.org/sustainabledevelopment/es/infrastructure/

[9] X. Li, F. Wang, Y. Guo, Y. Liu, H. Lv, F. Zeng y C. Lv, “Improved YOLO v5s-based detection method for external defects in potato,” *Frontiers in Plant Science*, vol. 16, art. 1527508, feb. 2025, doi: 10.3389/fpls.2025.1527508.


La selección presentada corresponde a la alternativa 1 de las 21 funciones, indicada visualmente por flechas azules en el archivo original.
