
# TRL 1 — KARTOFFELMASCHINE

## Fundamentos científicos, estado del arte y documentación tecnológica

**Proyecto:** Kartoffelmaschine — Sistema mecatrónico de clasificación automatizada de papa Chaucha.

**Nivel de madurez tecnológica:** TRL 1 — Identificación y observación de los principios científicos y tecnológicos.

---

## 1. Introducción

La papa es uno de los cultivos más importantes para la alimentación y la economía de numerosos países. Sin embargo, durante la etapa poscosecha pueden producirse pérdidas asociadas con la manipulación, almacenamiento, transporte y comercialización. Por ello, la evaluación de la calidad y la selección del producto representan actividades importantes dentro de su cadena de valor [1].

Tradicionalmente, la clasificación de papas se realiza mediante inspección visual humana o procedimientos mecánicos basados en propiedades como tamaño, forma y peso. La inspección manual depende de la experiencia del operador y de las condiciones de trabajo, mientras que los sistemas exclusivamente mecánicos pueden presentar limitaciones para identificar determinadas alteraciones superficiales.

Ante esta problemática, se han desarrollado investigaciones sobre el uso de visión artificial, procesamiento digital de imágenes e inteligencia artificial para automatizar el análisis de productos agrícolas. Estas tecnologías permiten reconocer características visibles, como cambios de color, manchas, deformaciones e irregularidades superficiales, con el propósito de apoyar los procesos de clasificación [2], [3].

**Kartoffelmaschine** propone el desarrollo de un sistema mecatrónico capaz de optimizar el proceso de clasificación de papa Chaucha mediante la integración de visión artificial, aprendizaje automático (*machine learning*) y mecanismos de separación física.

El prototipo contempla una estructura mecánica de transporte y orientación de papas, una cámara para obtener imágenes, una unidad de procesamiento basada en Raspberry Pi y un modelo de inteligencia artificial YOLOv8n para reconocer características visuales asociadas con defectos externos.

Asimismo, el sistema incorpora sensores, motores, mecanismos de separación y una interfaz de comunicación para integrar las etapas del proceso.

En este documento se presentan los fundamentos científicos y tecnológicos del proyecto, artículos científicos y patentes relacionadas, así como la documentación de los materiales, componentes electrónicos y herramientas computacionales que conforman la propuesta.

El presente trabajo corresponde al **Technology Readiness Level 1 (TRL 1)**, en el que se identifican los principios tecnológicos necesarios para sustentar el desarrollo posterior del prototipo.

---

## 2. Objetivos

### 2.1. Objetivo general

Investigar y documentar los principios científicos y tecnológicos necesarios para el desarrollo de Kartoffelmaschine, un sistema mecatrónico que utiliza visión artificial y aprendizaje automático para optimizar la clasificación de papa Chaucha según sus características externas.

### 2.2. Objetivos específicos

- Investigar los métodos tradicionales y automatizados de clasificación poscosecha de papa.
- Analizar artículos científicos relacionados con visión artificial, procesamiento de imágenes y aprendizaje automático aplicado a la clasificación de papas.
- Identificar patentes relacionadas con sistemas de inspección y separación automatizada de productos agrícolas.
- Documentar los materiales, componentes mecánicos, electrónicos y herramientas computacionales utilizados en el diseño del proyecto.
- Describir el funcionamiento conceptual del sistema y la interacción entre sus componentes.
- Identificar las principales limitaciones tecnológicas que deberán evaluarse durante el desarrollo del prototipo.

---

## 3. Estado del arte

### 3.1. Clasificación poscosecha y visión artificial

La clasificación poscosecha consiste en separar productos agrícolas de acuerdo con determinadas características físicas o visuales, como tamaño, forma, color, deformaciones y presencia de defectos superficiales.

En el caso de la papa, los sistemas tradicionales pueden utilizar inspección manual o mecanismos de clasificación basados en dimensiones y peso. Sin embargo, estos métodos no siempre permiten identificar de manera uniforme alteraciones externas del producto.

La visión artificial constituye una alternativa tecnológica que permite obtener información visual mediante cámaras y analizarla utilizando algoritmos computacionales.

Generalmente, un sistema de inspección por visión artificial comprende las siguientes etapas:

1. Captura de imágenes del producto.
2. Preprocesamiento para mejorar la calidad de las imágenes.
3. Identificación de características visuales relevantes.
4. Clasificación de acuerdo con los criterios establecidos.
5. Transmisión del resultado hacia el sistema de separación.

Su et al. [2] investigaron la clasificación de calidad de papas mediante visión artificial y análisis tridimensional de su forma, demostrando la utilidad de la información geométrica y visual en estos procedimientos.

En Kartoffelmaschine, este principio se aplicará mediante una cámara Raspberry Pi Camera Module 3, destinada a capturar imágenes de la superficie de las papas.

### 3.2. Inteligencia artificial y aprendizaje automático

El aprendizaje automático o *machine learning* es una rama de la inteligencia artificial que permite desarrollar modelos capaces de identificar patrones a partir de datos.

En la inspección agrícola, esta tecnología puede utilizarse para reconocer características visuales y asignar categorías a los productos analizados.

Entre los modelos empleados se encuentran las redes neuronales convolucionales (CNN), que permiten extraer automáticamente características relevantes de las imágenes.

Su et al. [3] investigaron la clasificación de calidad de papas utilizando imágenes de profundidad y una red neuronal convolucional, proporcionando un antecedente del uso de aprendizaje profundo para esta aplicación.

Por otra parte, Li et al. [9] desarrollaron un método basado en YOLOv5s para detectar defectos externos en papas.

Estos antecedentes respaldan la investigación de modelos de inteligencia artificial para automatizar la identificación de características visuales.

Para Kartoffelmaschine se propone utilizar **YOLOv8n**, una versión compacta de la familia de modelos YOLO (*You Only Look Once*).

Su función será analizar las imágenes obtenidas por la cámara e identificar patrones visuales que permitan diferenciar las categorías de clasificación establecidas.

El rendimiento del modelo dependerá de la calidad de las imágenes, la cantidad de datos disponibles, la variedad de papas utilizada y las condiciones de evaluación.

### 3.3. Sistemas mecatrónicos de clasificación

Un sistema mecatrónico integra componentes mecánicos, electrónicos y computacionales para ejecutar procesos de manera automatizada.

En una clasificadora de productos agrícolas, los elementos mecánicos permiten transportar y posicionar el producto, mientras que los sensores y sistemas electrónicos proporcionan información para coordinar su funcionamiento.

El sistema computacional procesa los datos obtenidos y genera instrucciones para los actuadores encargados de ejecutar la separación.

En Kartoffelmaschine, el proceso integra:

- Alimentación mediante una tolva por gravedad.
- Transporte mediante una mini faja de PVC.
- Orientación mediante una mesa de rodillos y un mecanismo de cadena.
- Captura de imágenes mediante una cámara.
- Procesamiento y clasificación con Raspberry Pi y YOLOv8n.
- Separación física mediante una compuerta accionada por servomotor.
- Visualización de información mediante indicadores LED y una interfaz web.

La integración de estos elementos constituye la base conceptual del funcionamiento del prototipo.

---

## 4. Artículos científicos relacionados

La investigación bibliográfica permitió identificar trabajos relacionados con la automatización de la inspección y clasificación de papas.

| Referencia | Investigación | Aporte científico | Relación con Kartoffelmaschine |
|---|---|---|---|
| FAO, 2010 [1] | *Strengthening Potato Value Chains* | Analiza la cadena de valor de la papa y aspectos de su producción y comercialización. | Permite contextualizar los problemas relacionados con la etapa poscosecha. |
| Su et al., 2018 [2] | *Potato quality grading based on machine vision and 3D shape analysis* | Investiga el uso de visión artificial y análisis geométrico para clasificar papas. | Sustenta la aplicación de imágenes para evaluar características del producto. |
| Su et al., 2020 [3] | *Potato quality grading based on depth imaging and convolutional neural network* | Aplica redes neuronales convolucionales a imágenes de profundidad. | Proporciona fundamentos para estudiar modelos de aprendizaje profundo. |
| Li et al., 2025 [9] | *Improved YOLO v5s-based detection method for external defects in potato* | Propone un método basado en YOLO para identificar defectos externos. | Se relaciona con la identificación visual mediante modelos de la familia YOLO. |

### 4.1. Aplicación de las investigaciones al proyecto

Los artículos muestran que la visión artificial y el aprendizaje profundo pueden utilizarse para estudiar características geométricas y visuales de papas.

En particular, la detección automática de defectos externos constituye un antecedente importante para Kartoffelmaschine, debido a que el proyecto busca identificar papas que presenten alteraciones visibles.

No obstante, los resultados publicados corresponden a las condiciones, variedades y modelos empleados en cada investigación.

Por esta razón, será necesario evaluar experimentalmente el comportamiento de YOLOv8n utilizando imágenes de papa Chaucha.

---

## 5. Patentes relacionadas

Además de los artículos científicos, se identificaron patentes que describen tecnologías de inspección visual, procesamiento de imágenes y clasificación automatizada.

### 5.1. CN109030504B — Panoramic potato defect detection device and method based on virtual and real imaging combination

Esta patente [4], desarrollada por Zhengzhou University of Light Industry, presenta un sistema de inspección que combina imágenes reales y virtuales para analizar diferentes superficies de las papas.

El dispositivo utiliza una cámara y elementos ópticos que permiten obtener información visual desde distintas perspectivas. Posteriormente, las imágenes se analizan mediante una red neuronal para detectar características no deseadas.

**Relación con Kartoffelmaschine:**

Esta tecnología constituye un antecedente para el diseño de un sistema que busque observar diferentes superficies de las papas antes de realizar la clasificación.

En Kartoffelmaschine se plantea utilizar mecanismos de rodillos y giro para modificar la orientación del producto durante la inspección.

### 5.2. US9114436B2 — Method for Sorting Potato Products and Sorting Apparatus for Potato Products

Esta patente [5] describe un procedimiento de clasificación de productos de papa mediante tecnologías de detección óptica y mecanismos de separación.

El sistema analiza características del producto y utiliza la información obtenida para identificar condiciones no deseadas.

**Relación con Kartoffelmaschine:**

Proporciona un antecedente de integración entre inspección óptica y separación automatizada.

En el proyecto se busca aplicar este principio mediante una cámara, procesamiento computacional y una compuerta accionada por servomotor.

### 5.3. US9527115B2 — Computer Vision and Machine Learning Software for Grading and Sorting Plants

Esta patente [6], desarrollada por Carnegie Mellon University, describe un sistema que integra visión artificial, aprendizaje automático y mecanismos de separación para clasificar plantas.

Aunque su aplicación original no corresponde específicamente a papas, constituye un antecedente de integración entre procesamiento de imágenes y clasificación física automatizada.

**Relación con Kartoffelmaschine:**

Sirve como referencia para la arquitectura del sistema, especialmente en la comunicación entre el procesamiento computacional y los mecanismos que realizan la separación.

### 5.4. Comparación de patentes

| Patente | Tecnología principal | Aplicación en Kartoffelmaschine |
|---|---|---|
| CN109030504B [4] | Inspección desde distintas perspectivas mediante visión artificial. | Diseño de un mecanismo que permita orientar las papas durante la captura de imágenes. |
| US9114436B2 [5] | Detección óptica y separación automatizada. | Integración de inspección y compuerta de separación. |
| US9527115B2 [6] | Visión por computadora y aprendizaje automático. | Arquitectura de procesamiento y control del sistema. |

Las patentes permiten identificar soluciones tecnológicas existentes que sirven como antecedentes para el desarrollo del proyecto.

---

## 6. Descripción general de Kartoffelmaschine

Kartoffelmaschine es una propuesta de sistema mecatrónico para optimizar la clasificación visual de papa Chaucha mediante tecnologías de visión artificial y aprendizaje automático.

El funcionamiento contempla una secuencia de alimentación, transporte, orientación, adquisición de imágenes, clasificación y separación física.

### 6.1. Alimentación

Las papas ingresarán mediante una tolva por gravedad fabricada en PETG.

Posteriormente, serán transportadas mediante una mini faja de PVC hacia la zona de inspección.

### 6.2. Orientación e inspección

Las papas llegarán a una mesa de inspección por rodillos.

El mecanismo de cadena con pasadores (*pin conveyor chain*), junto con los motorreductores, se utilizará para facilitar el movimiento y la orientación del producto.

Esta operación busca permitir la captura de imágenes desde diferentes posiciones, incrementando la superficie externa observable.

### 6.3. Captura de imágenes

Un sensor de presencia E18-D80NK permitirá identificar la llegada de una papa a la zona de inspección.

La Raspberry Pi Camera Module 3 capturará imágenes del producto para su posterior análisis.

### 6.4. Procesamiento mediante inteligencia artificial

Las imágenes serán procesadas por una Raspberry Pi 5 de 8 GB de memoria RAM.

Se utilizará el modelo YOLOv8n para estudiar la identificación automática de características visuales asociadas con las categorías de clasificación establecidas.

### 6.5. Separación física

El resultado del procesamiento se utilizará para controlar una compuerta accionada mediante un servomotor MG996R.

Este mecanismo permitirá dirigir las papas hacia las zonas de recepción previstas según su categoría.

### 6.6. Visualización y comunicación

El sistema contempla indicadores LED y una interfaz web desarrollada mediante Flask/HTML.

La conectividad Wi-Fi integrada de la Raspberry Pi permitirá transmitir información para supervisar el funcionamiento del prototipo.

---

## 7. Materiales, componentes y tecnologías del proyecto

Para el desarrollo de Kartoffelmaschine se contemplan componentes mecánicos, dispositivos electrónicos, materiales estructurales y herramientas computacionales.

Estos elementos cumplen funciones específicas dentro del sistema de alimentación, transporte, inspección visual, procesamiento de datos, control y separación física.

### 7.1. Sistema de energía

El sistema de energía tiene como finalidad suministrar las tensiones eléctricas requeridas por los distintos componentes del prototipo.

| N.º | Componente | Función |
|---|---|---|
| 1 | Fuente Mean Well de 12 V | Suministrar energía eléctrica al sistema. |
| 2 | Fuente switching de 12 V | Proporcionar alimentación a los actuadores según los requerimientos del diseño. |
| 3 | Convertidor Buck XL4015 a 5 V | Reducir la tensión de alimentación para los dispositivos electrónicos compatibles. |

**Descripción:**

Las fuentes de alimentación permitirán suministrar energía al sistema mecatrónico.

El convertidor Buck XL4015 se contempla para obtener una tensión reducida que pueda utilizarse en determinados dispositivos electrónicos.

La capacidad de corriente, distribución de potencia y compatibilidad eléctrica deberán verificarse durante la implementación.

### 7.2. Sistema de procesamiento y control de señales

Este sistema se encargará de obtener y procesar información visual, así como de coordinar el funcionamiento de los mecanismos del prototipo.

| N.º | Componente | Función |
|---|---|---|
| 4 | Raspberry Pi 5 — 8 GB RAM | Procesamiento de imágenes y control computacional. |
| 5 | Raspberry Pi Camera Module 3 | Adquisición de imágenes de las papas. |
| 6 | YOLOv8n | Modelo de inteligencia artificial para la detección o clasificación visual. |
| 7 | Sensor E18-D80NK | Detección de presencia de papas. |
| 8 | Encoder rotativo incremental de 600 PPR | Medición del movimiento o posición angular del mecanismo correspondiente. |

**Descripción:**

La Raspberry Pi 5 funcionará como unidad central de procesamiento.

La cámara permitirá obtener imágenes digitales de las papas, las cuales serán analizadas mediante YOLOv8n.

El sensor E18-D80NK ayudará a detectar el ingreso de las papas a la zona de inspección.

Por su parte, el encoder permitirá obtener información del movimiento mecánico para contribuir a la coordinación del sistema.

### 7.3. Sistema mecánico

El sistema mecánico permitirá transportar, orientar y separar físicamente las papas durante el proceso de clasificación.

| N.º | Componente | Función |
|---|---|---|
| 9 | Tolva por gravedad fabricada en PETG | Recepción y alimentación de papas. |
| 10 | Mini faja transportadora de PVC | Transporte hacia la zona de inspección. |
| 11 | Mesa de inspección por rodillos | Soporte y desplazamiento de las papas durante la inspección. |
| 12 | Pin conveyor chain | Mecanismo de cadena con pasadores para apoyar la orientación de las papas. |
| 13 | Dos motorreductores DC JGA25-370 | Accionamiento del mecanismo de giro. |
| 14 | Compuerta accionada por servomotor MG996R | Separación física según la clasificación obtenida. |
| 15 | Compuerta con bandeja | Recepción de las papas clasificadas. |

**Descripción:**

La tolva por gravedad permitirá introducir las papas al sistema de transporte.

La mini faja de PVC desplazará el producto hacia la mesa de inspección.

En esta zona, los rodillos, el mecanismo de cadena y los motorreductores se utilizarán para orientar las papas, facilitando la captura de imágenes desde distintas posiciones.

Finalmente, la compuerta accionada mediante el servomotor MG996R permitirá ejecutar la separación física de acuerdo con el resultado del sistema de clasificación.

### 7.4. Sistema de comunicación

Este sistema facilitará la visualización del estado operativo y de los resultados del proceso.

| N.º | Componente o tecnología | Función |
|---|---|---|
| 16 | LEDs indicadores de 5 mm | Señalización visual del estado del sistema. |
| 17 | Wi-Fi integrado de Raspberry Pi 5 | Comunicación inalámbrica y transmisión de información. |
| 18 | Interfaz web mediante Flask/HTML | Visualización de resultados y supervisión del prototipo. |

**Descripción:**

Los indicadores LED proporcionarán información visual básica sobre las operaciones del equipo.

La conectividad Wi-Fi de la Raspberry Pi permitirá comunicar el sistema con la interfaz web.

Mediante Flask y HTML se desarrollará una interfaz para mostrar información del proceso de clasificación.

### 7.5. Materiales y estructura

Los materiales estructurales permitirán fabricar los soportes, mecanismos y elementos de contacto con las papas.

| N.º | Material | Aplicación |
|---|---|---|
| 19 | Aluminio | Fabricación de la estructura principal del prototipo. |
| 20 | PETG eSUN impreso en 3D | Fabricación de soportes y piezas personalizadas. |
| 21 | Rodillo recubierto de TPU 95A | Superficie de contacto para facilitar la orientación de las papas. |

**Descripción:**

El aluminio se utilizará como material principal de la estructura del equipo.

El PETG eSUN permitirá fabricar piezas personalizadas mediante impresión 3D, adaptándolas a los requerimientos geométricos del prototipo.

Por otro lado, el recubrimiento de TPU 95A se contempla para los rodillos que estarán en contacto con las papas durante su orientación.

### 7.6. Resumen de los materiales y componentes

| Subsistema | Cantidad de elementos |
|---|---:|
| Energía | 3 |
| Procesamiento y control de señales | 5 |
| Mecánica | 7 |
| Comunicación | 3 |
| Materiales y estructura | 3 |
| **Total** | **21** |

En conjunto, estos 21 elementos constituyen la base tecnológica y material del diseño propuesto para Kartoffelmaschine.

Su integración permitirá estudiar un proceso automatizado de inspección y separación de papa Chaucha.

---

## 8. Relación del proyecto con los Objetivos de Desarrollo Sostenible

### 8.1. ODS 12 — Producción y consumo responsables

El ODS 12 promueve modalidades de producción y consumo sostenibles.

Específicamente, la meta 12.3 plantea reducir las pérdidas de alimentos a lo largo de las cadenas de producción y suministro [7].

Kartoffelmaschine se relaciona con este objetivo al proponer una herramienta tecnológica que permita apoyar la inspección y clasificación de papas durante la etapa poscosecha.

La automatización podría contribuir a una selección más uniforme y a mejorar la eficiencia del proceso; sin embargo, estos beneficios deberán evaluarse experimentalmente.

### 8.2. ODS 9 — Industria, innovación e infraestructura

El ODS 9 promueve el desarrollo tecnológico, la innovación y la industrialización sostenible [8].

Kartoffelmaschine se vincula con este objetivo mediante la aplicación de tecnologías emergentes, como visión artificial, aprendizaje automático y sistemas mecatrónicos, para mejorar un proceso de clasificación agrícola.

El proyecto busca integrar estas tecnologías dentro de un prototipo funcional que pueda ser evaluado y perfeccionado en las siguientes etapas de desarrollo.

---

## 9. Limitaciones identificadas

Durante la revisión bibliográfica y el análisis tecnológico se identificaron diferentes factores que podrían influir en el funcionamiento del prototipo.

### 9.1. Variabilidad de las papas

Las papas presentan diferencias naturales de tamaño, forma, color y textura.

Estas variaciones pueden dificultar la identificación de características visuales y deberán considerarse durante el desarrollo del modelo de inteligencia artificial.

### 9.2. Condiciones de iluminación

La calidad de las imágenes depende de factores como la iluminación, el enfoque, la distancia de captura y la orientación del producto.

Será necesario controlar estas condiciones para reducir las variaciones durante la inspección.

### 9.3. Disponibilidad de datos

El entrenamiento de modelos de aprendizaje automático requiere imágenes representativas y correctamente etiquetadas.

La cantidad y diversidad de imágenes de papa Chaucha influirá en la capacidad del modelo para reconocer defectos externos.

### 9.4. Identificación de defectos

La inspección mediante cámaras convencionales se limita principalmente a las características visibles de la superficie.

Por ello, no todos los defectos internos ni las condiciones de inocuidad pueden identificarse mediante esta tecnología.

### 9.5. Sincronización del sistema

El transporte, la orientación de las papas, la captura de imágenes y el accionamiento de la compuerta deberán trabajar de manera coordinada.

Una sincronización inadecuada podría ocasionar errores de clasificación o separación.

### 9.6. Integración eléctrica y mecánica

La conexión de los componentes requerirá verificar tensiones, corrientes, potencia disponible y compatibilidad de señales.

Asimismo, los mecanismos deberán permitir la manipulación de las papas sin ocasionar daños significativos.

---

## 10. Conclusiones

La investigación realizada permitió identificar los principales fundamentos científicos y tecnológicos asociados con la clasificación automatizada de papas mediante visión artificial, procesamiento digital de imágenes y aprendizaje automático.

Los artículos científicos analizados evidencian la aplicación de estas tecnologías en la evaluación de características geométricas y defectos externos de papas [2], [3], [9].

Asimismo, las patentes revisadas proporcionan antecedentes de sistemas que integran inspección visual, procesamiento computacional y separación física [4]–[6].

A partir de estos fundamentos, Kartoffelmaschine plantea una solución mecatrónica que combina alimentación, transporte, orientación del producto, adquisición de imágenes, clasificación mediante YOLOv8n y separación mediante una compuerta automatizada.

Se documentaron **21 elementos**, organizados en cinco subsistemas: energía, procesamiento y control de señales, mecánica, comunicación, y materiales y estructura.

Entre los principales componentes se encuentran la Raspberry Pi 5, la Raspberry Pi Camera Module 3, el modelo YOLOv8n, sensores, motorreductores, mecanismos de transporte y materiales para fabricación mecánica.

La integración de estos elementos constituye la base conceptual para el desarrollo del prototipo.

Finalmente, el TRL 1 permite establecer los fundamentos científicos y tecnológicos necesarios para continuar con las siguientes etapas de diseño, prueba de concepto y validación experimental.

---

## 11. Referencias bibliográficas (formato IEEE)

[1] N. Cromme, A. B. Prakash, N. Lutaladio y F. Ezeta, Eds., *Strengthening Potato Value Chains: Technical and Policy Options for Developing Countries*. Roma, Italia: Food and Agriculture Organization of the United Nations, 2010. [En línea]. Disponible: https://www.fao.org/4/i1710e/i1710e.pdf

[2] Q. Su, N. Kondo, M. Li, H. Sun, D. F. Al Riza y H. Habaragamuwa, “Potato quality grading based on machine vision and 3D shape analysis,” *Computers and Electronics in Agriculture*, vol. 152, pp. 261–268, 2018, doi: 10.1016/j.compag.2018.07.012.

[3] Q. Su, N. Kondo, D. F. Al Riza y H. Habaragamuwa, “Potato quality grading based on depth imaging and convolutional neural network,” *Journal of Food Quality*, vol. 2020, art. 8815896, 2020, doi: 10.1155/2020/8815896.

[4] Zhengzhou University of Light Industry, “Panoramic potato defect detection device and method based on virtual and real imaging combination,” China Patent CN109030504B, 2020. [En línea]. Disponible: https://patents.google.com/patent/CN109030504B/en

[5] P. Berghmans, C. Fivez y J. Speybrouck, “Method for sorting potato products and sorting apparatus for potato products,” U.S. Patent US9114436B2, 2015. [En línea]. Disponible: https://patents.google.com/patent/US9114436B2/en

[6] D. A. LaRose, C. C. Fromme, D. J. Stager, M. K. Sergi-Curfman, J. A. Bagnell, E. A. Cuzzillo y L. D. Baker, “Computer vision and machine learning software for grading and sorting plants,” U.S. Patent US9527115B2, 2016. [En línea]. Disponible: https://patents.google.com/patent/US9527115B2/en

[7] Naciones Unidas, “Objetivo 12: Garantizar modalidades de consumo y producción sostenibles.” [En línea]. Disponible: https://www.un.org/sustainabledevelopment/es/sustainable-consumption-production/

[8] Naciones Unidas, “Objetivo 9: Construir infraestructuras resilientes, promover la industrialización sostenible y fomentar la innovación.” [En línea]. Disponible: https://www.un.org/sustainabledevelopment/es/infrastructure/

[9] X. Li, F. Wang, Y. Guo, Y. Liu, H. Lv, F. Zeng y C. Lv, “Improved YOLO v5s-based detection method for external defects in potato,” *Frontiers in Plant Science*, vol. 16, art. 1527508, 2025, doi: 10.3389/fpls.2025.1527508.
