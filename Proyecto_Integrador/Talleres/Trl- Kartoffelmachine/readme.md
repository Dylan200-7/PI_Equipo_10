# TRL 1
 
## 1. Introducción
 
La papa es uno de los cultivos más importantes para la alimentación y la economía de numerosos países, pero durante la etapa poscosecha pueden producirse pérdidas por manipulación, almacenamiento, transporte y comercialización. Por ello, la evaluación de la calidad y la selección del producto son actividades clave de su cadena de valor [1].
 
Tradicionalmente, la clasificación se realiza mediante inspección visual humana o procedimientos mecánicos basados en tamaño, forma y peso. La inspección visual varía según la experiencia del operador y las condiciones de trabajo, por lo que se han investigado tecnologías que automatizan el análisis de características externas, como la visión por computadora, el procesamiento de imágenes y la inteligencia artificial [2], [3].
 
Kartoffelmaschine propone el diseño de un sistema mecatrónico que integre estas tecnologías para analizar características visibles de la papa Chaucha y apoyar su clasificación, junto con mecanismos de separación física. Este documento revisa artículos científicos y patentes relacionados, y corresponde al nivel TRL 1, en el que se identifican los principios científicos y tecnológicos que fundamentan el proyecto.
 
## 2. Objetivos
 
**General:** analizar el estado del arte de las tecnologías de inspección y clasificación poscosecha de papa para establecer los fundamentos científicos y tecnológicos de Kartoffelmaschine.
 
**Específicos:**
 
- Identificar métodos tradicionales y automatizados de clasificación de papa.
- Revisar artículos y patentes sobre visión artificial, aprendizaje automático y detección de defectos en papa.
- Comparar aportes y limitaciones de las tecnologías existentes y relacionarlos con la propuesta.

## 3. Estado del arte
 
### 3.1. Clasificación poscosecha y visión por computadora
 
La clasificación poscosecha separa los productos según características físicas o visuales, como tamaño, forma, color, deformaciones y apariencia superficial. Una clasificación basada solo en dimensiones no permite identificar todas las alteraciones visibles, y la inspección humana es difícil de mantener uniforme con grandes volúmenes [1].
 
La visión por computadora obtiene información de un objeto mediante imágenes procesadas digitalmente. En inspección agrícola, el proceso comprende captura de imágenes, procesamiento, análisis de características (color, contorno, dimensiones, manchas) y asignación de una categoría. Su et al. mostraron que la visión artificial y el análisis de imágenes de profundidad permiten evaluar propiedades geométricas y detectar defectos sin depender solo de la inspección manual [2]. Su desempeño depende de la iluminación, la distancia de la cámara, la orientación de la papa y la calidad de la imagen.
 
### 3.2. Inteligencia artificial e imágenes de profundidad
 
El aprendizaje automático entrena modelos con ejemplos etiquetados para reconocer patrones y clasificar nuevos casos. Las redes neuronales convolucionales (CNN) son modelos de aprendizaje profundo especializados en imágenes, capaces de aprender características visuales sin definirlas manualmente. Su et al. aplicaron una CNN a imágenes de profundidad para clasificar la calidad de papas, lo que respalda la viabilidad de este enfoque [3]. Sin embargo, el rendimiento depende de la cantidad y variedad de imágenes, de las etiquetas y de las condiciones de evaluación.
 
Las imágenes de profundidad aportan información de volumen, grosor e irregularidades que una imagen en color no ofrece, aunque requieren equipos especializados y mayor procesamiento [2], [3]. Su uso en Kartoffelmaschine dependerá de los criterios de clasificación, el costo y los recursos disponibles.
 
### 3.3. Sistemas mecatrónicos de clasificación
 
Un sistema mecatrónico integra componentes mecánicos, electrónicos y computacionales. Una clasificadora automática suele organizarse en: alimentación, transporte, inspección visual, procesamiento, control y separación. Para que la categoría asignada corresponda a la papa que llega al mecanismo de separación, es esencial sincronizar el transporte, la ubicación de la cámara, el tiempo de procesamiento y la respuesta de los actuadores. Esta integración deberá desarrollarse y evaluarse en las siguientes etapas del proyecto.
 
## 4. Artículos científicos relacionados
 
| Referencia | Aporte | Relación con Kartoffelmaschine |
|---|---|---|
| FAO, 2010 [1] | Marco técnico y de políticas sobre cadenas de valor de la papa en países en desarrollo. | Contextualiza la problemática poscosecha y justifica estudiar herramientas de selección y clasificación. |
| Su et al., 2018 [2] | Clasificación de calidad de papa con visión artificial y análisis 3D de forma. | Antecedente para comparar lo que ofrecen imágenes convencionales y tridimensionales. |
| Su et al., 2020 [3] | Clasificación de calidad de papa con imágenes de profundidad y CNN. | Fundamento para investigar modelos que clasifiquen papa Chaucha; sus resultados son antecedentes, no una medida del rendimiento esperado del sistema propuesto. |
 
## 5. Patentes relacionadas
 
Se seleccionaron patentes concedidas cuyo estado figura como activo en Google Patents (dato referencial, no una conclusión legal). Su revisión no implica que el proyecto reproduzca sus reivindicaciones ni demuestra novedad legal; para ello se requeriría una búsqueda de anterioridades más amplia.
 
**CN109030504B – Panoramic potato defect detection device and method based on virtual and real imaging combination** [4]. Patente china concedida el 2 de octubre de 2020 (titular: Zhengzhou University of Light Industry). Usa una sola cámara y espejos para obtener una imagen real superior y cuatro imágenes virtuales inferiores de la papa sin voltearla, las analiza con una red neuronal convolucional multicanal para detectar germinación, alteraciones superficiales, daños o deformaciones, y separa las papas defectuosas con una boquilla de aire sobre una banda transportadora. Vencimiento estimado: 2038.
 
**US9114436B2 – Method for Sorting Potato Products and Sorting Apparatus for Potato Products** [5]. Patente estadounidense concedida el 25 de agosto de 2015 (inventores: P. Berghmans, C. Fivez y J. Speybrouck), con equivalentes en Europa (EP2411164B1) y China (CN102421540B). Utiliza iluminación en longitudes de onda específicas y detección óptica para identificar condiciones no deseadas, y un dispositivo de retirada para separar los productos. Al emplear principios ópticos específicos, no debe asumirse que una cámara convencional detecte las mismas condiciones.
 
**US9527115B2 – Computer Vision and Machine Learning Software for Grading and Sorting Plants** [6]. Patente estadounidense concedida el 27 de diciembre de 2016 (titular: Carnegie Mellon University; vencimiento estimado: 2032). Describe un software de visión por computadora y aprendizaje automático que, sobre una banda transportadora, aísla cada planta en la imagen, clasifica sus píxeles por partes, calcula características, asigna una categoría configurable y separa la planta con un dispositivo como chorros de aire. Fue desarrollada para plantas de fresa de raíz desnuda, no para papa, por lo que sirve como referencia de arquitectura (visión, aprendizaje automático y separación) y no como antecedente específico de papa.
 
| Criterio | CN109030504B [4] | US9114436B2 [5] | US9527115B2 [6] |
|---|---|---|---|
| Producto | Papa | Papa | Plantas (fresa de raíz desnuda) |
| Enfoque | Visión con CNN y espejos | Detección óptica especializada | Visión por computadora y aprendizaje automático |
| Separación | Boquilla de aire | Dispositivo de retirada | Chorros de aire u otro dispositivo |
| Aporte al proyecto | Referencia más cercana: cámara, CNN y separación para papa | Método óptico alternativo | Arquitectura de clasificación y separación en banda |
 
## 6. Relación con Kartoffelmaschine
 
| Necesidad | Antecedente | Aplicación potencial |
|---|---|---|
| Obtener información visual | Visión artificial [2] | Capturar imágenes de cada papa |
| Clasificar por características visuales | CNN [3] | Investigar modelos para distinguir categorías |
| Analizar forma y geometría | Imágenes de profundidad [2], [3] | Evaluar si se requiere información 3D |
| Identificar características no deseadas | Visión y detección óptica [4]–[6] | Definir qué defectos pueden reconocerse con los recursos disponibles |
| Ejecutar la separación física | Sistemas de separación [4]–[6] | Integrar el resultado del análisis con transporte y separación |
 
Los antecedentes muestran que la clasificación automatizada de papa ya cuenta con soluciones previas, por lo que Kartoffelmaschine no es el primer sistema en usar estas tecnologías. Su oportunidad de desarrollo está en adaptar e integrar la clasificación a la papa Chaucha, seleccionar las características visuales relevantes, acoplar la clasificación con el transporte y la separación, y evaluar experimentalmente el sistema con los componentes disponibles. Su viabilidad deberá comprobarse en etapas posteriores.
 
## 7. Relación con los ODS
 
**ODS 12 (Producción y consumo responsables).** La meta 12.3 plantea reducir las pérdidas de alimentos en las cadenas de producción y suministro [7]. Kartoffelmaschine se relaciona con ella al investigar una herramienta de clasificación poscosecha que apoye una selección más uniforme. No obstante, la clasificación automática no garantiza por sí sola una reducción de pérdidas; para demostrarla habría que comparar indicadores de pérdidas y eficiencia con un procedimiento de referencia.
 
**ODS 9 (Industria, innovación e infraestructura).** Este objetivo promueve la innovación y la industrialización sostenible [8]. El proyecto se vincula con él al integrar visión por computadora, inteligencia artificial, electrónica y control en una operación agrícola poscosecha. Su contribución práctica deberá evaluarse en las siguientes etapas.
 
## 8. Limitaciones identificadas
 
- **Variabilidad del producto:** las papas difieren naturalmente en tamaño, forma y apariencia.
- **Iluminación:** sus cambios alteran la apariencia registrada en las imágenes.
- **Representatividad de los datos:** pocas muestras o imágenes poco variadas limitan la generalización del modelo.
- **Detección de defectos:** los defectos internos no siempre pueden identificarse con imágenes convencionales.
- **Tiempo de procesamiento e integración mecánica:** el análisis debe ser compatible con el tiempo disponible para ejecutar la separación.
- **Adaptación a la papa Chaucha:** los resultados de otras variedades no deben trasladarse sin evaluación experimental.
  
## 9. Conclusiones
 
La revisión identificó tecnologías utilizadas en la clasificación poscosecha de papa: visión por computadora, análisis tridimensional, aprendizaje automático y detección óptica [2]–[6]. Los artículos muestran que las imágenes permiten analizar características geométricas y visuales, y que los modelos de aprendizaje automático pueden clasificar según patrones de los datos [2], [3]. Las patentes presentan sistemas que integran inspección con clasificación y separación física [4]–[6].
 
En conjunto, los antecedentes revisados respaldan la viabilidad de investigar un sistema mecatrónico inteligente para el triaje poscosecha de papa Chaucha. Como resultado del TRL 1, Kartoffelmaschine cuenta con un fundamento científico y tecnológico sólido sobre el cual avanzar.
 
## 10. Referencias
 
[1] N. Cromme, A. B. Prakash, N. Lutaladio y F. Ezeta, Eds., *Strengthening Potato Value Chains: Technical and Policy Options for Developing Countries*. Roma, Italia: Food and Agriculture Organization of the United Nations, 2010. [En línea]. Disponible: https://www.fao.org/4/i1710e/i1710e.pdf
 
[2] Q. Su, N. Kondo, M. Li, H. Sun, D. F. Al Riza y H. Habaragamuwa, "Potato quality grading based on machine vision and 3D shape analysis," *Comput. Electron. Agric.*, vol. 152, pp. 261–268, sep. 2018, 
doi: 10.1016/j.compag.2018.07.012.
 
[3] Q. Su, N. Kondo, D. F. Al Riza y H. Habaragamuwa, "Potato quality grading based on depth imaging and convolutional neural network," *J. Food Qual.*, vol. 2020, art. no. 8815896, 2020, doi: 10.1155/2020/8815896.
 
[4] Zhengzhou University of Light Industry, "Panoramic potato defect detection device and method based on virtual and real imaging combination," China Patent CN109030504B, 2 oct. 2020. [En línea]. Disponible: https://patents.google.com/patent/CN109030504B/en
 
[5] P. Berghmans, C. Fivez y J. Speybrouck, "Method for sorting potato products and sorting apparatus for potato products," U.S. Patent 9 114 436 B2, 25 ago. 2015. [En línea]. Disponible: https://patents.google.com/patent/US9114436B2/en
 
[6] D. A. LaRose, C. C. Fromme, D. J. Stager, M. K. Sergi-Curfman, J. A. Bagnell, E. A. Cuzzillo y L. D. Baker, "Computer vision and machine learning software for grading and sorting plants," U.S. Patent 9 527 115 B2, 27 dic. 2016. [En línea]. Disponible: https://patents.google.com/patent/US9527115B2/en
 
[7] United Nations, "Goal 12: Ensure sustainable consumption and production patterns." [En línea]. Disponible: https://www.un.org/sustainabledevelopment/es/sustainable-consumption-production/
 
[8] United Nations, "Goal 9: Build resilient infrastructure, promote inclusive and sustainable industrialization and foster innovation." [En línea]. Disponible: https://www.un.org/sustainabledevelopment/es/infrastructure/

