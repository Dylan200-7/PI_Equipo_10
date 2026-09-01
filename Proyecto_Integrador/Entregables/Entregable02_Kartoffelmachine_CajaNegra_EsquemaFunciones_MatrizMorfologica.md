# Caja Negra, Esquema de Funciones y Matriz Morfológica — Kartoffelmaschine

## Caja Negra

<img src="Recursos/Imágenes/Caja_Negra_Kartoffelmachine.png" width="1000"/>

La **Caja Negra** representa de manera general el funcionamiento de **Kartoffelmachine**, un sistema mecatrónico automatizado diseñado para la **inspección y clasificación de papas Chaucha mediante visión artificial**.

Como entrada principal, el sistema recibe **papas Chaucha sin clasificar**. También recibe la **energía eléctrica** necesaria para el funcionamiento de los componentes mecánicos y electrónicos, además de información proporcionada por el usuario, como la **orden de inicio o parada**, los **parámetros de clasificación**, los **parámetros de operación** y la **configuración del proceso**.

Durante el funcionamiento, las papas son recibidas, orientadas, giradas y transportadas para permitir la captura de imágenes de diferentes zonas de su superficie. Estas imágenes son procesadas mediante un modelo de **Machine Learning basado en YOLO**, que determina si cada papa corresponde a la categoría **buena o mala**.

Como salidas principales se obtienen **papas clasificadas como buenas** y **papas clasificadas como malas**. Además, el sistema genera información sobre el proceso, como el **estado del sistema**, el **resultado de clasificación por papa**, la **cantidad de papas procesadas** y las **alertas o notificaciones mediante WiFi**. Debido al funcionamiento de motores y mecanismos, también se generan **calor, ruido y vibración disipados**.

### Tipos de flujo

- **Materia:** representa el desplazamiento físico de las papas.
- **Energía:** representa la alimentación eléctrica y la energía utilizada por el sistema.
- **Información:** representa órdenes, parámetros, señales, resultados y datos del proceso.

---

## Esquema de Funciones

<img src="Recursos/Imágenes/Esquema_Funciones_Kartoffelmachine.png" width="1200"/>

El **Esquema de Funciones** descompone Kartoffelmachine en los principales subsistemas que permiten realizar automáticamente el proceso de inspección y clasificación. El sistema está conformado por los subsistemas de **energía, control, sensores y visión, Machine Learning, actuadores y sistema mecánico**.

Estos subsistemas intercambian flujos de **materia, energía e información**, permitiendo que la papa avance desde la entrada hasta una de las dos salidas según el resultado obtenido por el modelo de visión artificial.

### Subsistema de energía

La energía eléctrica ingresa al sistema y pasa por las siguientes funciones:

1. **Recibir energía eléctrica.**
2. **Regular la energía.**
3. **Distribuir la energía** hacia el sistema de control, sensores, cámara, iluminación y actuadores.

Este subsistema proporciona los niveles de tensión necesarios para el funcionamiento adecuado de los componentes electrónicos y mecánicos.

### Subsistema de control

El sistema de control coordina el funcionamiento general de Kartoffelmachine. Sus principales funciones son:

1. **Detectar la señal de encendido o apagado.**
2. **Recibir la señal de los sensores.**
3. **Enviar las imágenes al sistema de inteligencia artificial.**
4. **Recibir el resultado generado por la IA.**
5. **Activar los actuadores según el resultado obtenido.**

De esta manera, el control actúa como enlace entre la detección de la papa, el procesamiento mediante inteligencia artificial y los mecanismos físicos del sistema.

### Subsistema de sensores y visión

Este subsistema permite detectar la presencia de la papa y obtener las imágenes necesarias para realizar su clasificación.

Sus funciones principales son:

1. **Detectar la papa en posición.**
2. **Capturar imágenes durante la rotación de la papa.**
3. **Enviar la señal digital al sistema de control.**

La rotación de la papa permite observar diferentes zonas de su superficie y obtener mayor información para el proceso de clasificación.

### Subsistema de Machine Learning — YOLO

El procesamiento mediante inteligencia artificial se realiza a partir de las imágenes capturadas durante la inspección.

El flujo de procesamiento es:

1. **Recibir las imágenes enviadas por el control.**
2. **Analizar las imágenes mediante el modelo YOLO.**
3. **Clasificar la papa como buena o mala.**
4. **Enviar el resultado de clasificación al sistema de control.**

El modelo de visión artificial permite identificar características o defectos visibles en la superficie de la papa y generar automáticamente el resultado de clasificación.

### Subsistema de actuadores

Los actuadores convierten las señales enviadas por el control en acciones físicas dentro del prototipo.

Sus principales funciones son:

1. **Girar los motores** encargados de la rotación y el transporte.
2. **Accionar la compuerta separadora.**
3. **Iluminar la zona de captura mediante LED.**
4. **Mostrar el resultado mediante un LED de color.**

### Sistema mecánico

El sistema mecánico se encarga directamente del desplazamiento y manipulación de las papas.

El flujo principal es:

```text
Papa sin clasificar
        ↓
Recibir papa
(Tolva)
        ↓
Sujetar y orientar papa
(Guía / rodillos en V)
        ↓
Rotar la papa 360°
y capturar imágenes
        ↓
Transportar papa
(Faja)
        ↓
Separar papa
(Compuerta)
      ↙     ↘
 Papa buena  Papa mala
 (Salida 1)  (Salida 2)
```

De esta manera, la papa pasa por las etapas de **alimentación, orientación, rotación, captura de imágenes, transporte y separación** hasta llegar al contenedor correspondiente.

### Señales principales del esquema

| Señal | Descripción |
| --- | --- |
| **Z** | Señal de encendido/apagado que habilita el funcionamiento general del sistema. |
| **A** | Señal relacionada con la posición de la papa y la interacción entre el sistema mecánico, sensores y control. |
| **B** | Imágenes enviadas desde el control hacia el sistema de Machine Learning. |
| **C** | Resultado de clasificación enviado por la IA al sistema de control. |
| **E** | Señal de accionamiento enviada hacia los actuadores. |

---

## Matriz Morfológica

<img src="Recursos/Imágenes/Matriz_Morfologica_Kartoffelmachine.png" width="1200"/>

La **Matriz Morfológica** presenta diferentes alternativas tecnológicas para cada una de las funciones necesarias en Kartoffelmachine. Las funciones se agrupan en cinco áreas principales: **energía, procesamiento y control de señales, mecánica, comunicación y material/estructura**.

A partir de las alternativas planteadas se desarrollaron tres soluciones preliminares.

---

### Solución Preliminar 1 — Funcional y viable para el prototipo

| Función | Elección |
| --- | --- |
| **T1. Proporcionar energía al sistema** | **T1.1 – Fuente AC 220 V** |
| **T2. Convertir la energía para los actuadores** | **T2.1 – Fuente switching 220 V → 12 V** |
| **T3. Alimentar Raspberry Pi y electrónica** | **T3.1 – Convertidor Buck 12 V → 5 V** |
| **T4. Procesar imágenes y controlar el sistema** | **T4.1 – Raspberry Pi 5** |
| **T5. Capturar imágenes de las papas** | **T5.1 – Raspberry Pi Camera V3** |
| **T6. Detectar el estado de la papa mediante IA** | **T6.1 – YOLOv8n** |
| **T7. Detectar presencia de una papa** | **T7.1 – Sensor fotoeléctrico IR** |
| **T8. Determinar posición y desplazamiento de las papas** | **T8.1 – Encoder rotativo** |
| **T9. Recibir y alimentar las papas al sistema** | **T9.1 – Tolva por gravedad** |
| **T10. Transportar las papas durante la inspección** | **T10.1 – Faja transportadora** |
| **T11. Girar y orientar la papa para visualizar distintas superficies** | **T11.1 – Rodillos en configuración V** |
| **T12. Accionar el mecanismo de giro** | **T12.1 – Motorreductor DC** |
| **T13. Separar papa buena y papa mala** | **T13.1 – Compuerta accionada por servomotor** |
| **T14. Recibir las papas clasificadas** | **T14.1 – Dos contenedores independientes** |
| **T15. Mostrar el estado de clasificación** | **T15.1 – LED indicadores** |
| **T16. Transmitir resultados del sistema** | **T16.1 – WiFi integrado de Raspberry Pi** |
| **T17. Permitir interacción con el operador** | **T17.1 – Interfaz web** |
| **T18. Construir la estructura principal** | **T18.1 – Perfiles de aluminio** |
| **T19. Fabricar soportes y piezas del prototipo** | **T19.1 – PETG impreso en 3D** |
| **T20. Proporcionar contacto adecuado con la papa durante el giro** | **T20.1 – Rodillo recubierto de TPU/goma** |

#### ¿Cómo sería?

Esta propuesta utiliza una **fuente AC de 220 V**, una fuente switching de 12 V y un convertidor Buck para proporcionar los niveles de tensión necesarios a los diferentes componentes.

Las papas ingresan mediante una **tolva por gravedad** y son desplazadas utilizando una **faja transportadora**. En la zona de inspección, cada papa es sujetada y orientada mediante **rodillos en configuración V**, mientras un **motorreductor DC** acciona el mecanismo encargado de hacerla girar.

El rodillo de contacto tendría un recubrimiento de **TPU o goma** para aumentar la fricción y permitir la rotación sin dañar significativamente la superficie de la papa.

Un **sensor fotoeléctrico IR** detecta la presencia de la papa y un **encoder rotativo** permite controlar su posición y desplazamiento. Una **Raspberry Pi Camera V3** captura las imágenes durante la rotación y estas son procesadas por una **Raspberry Pi 5 utilizando YOLOv8n**.

Luego de determinar si la papa es buena o mala, una **compuerta accionada por servomotor** la dirige hacia uno de los **dos contenedores independientes**. El sistema utiliza **LED indicadores**, conexión **WiFi** e **interfaz web** para mostrar y transmitir información del proceso.

La estructura principal se fabricaría utilizando **perfiles de aluminio**, mientras que los soportes y piezas especiales podrían ser impresos en **PETG**.

- **Ventaja:** Presenta un buen equilibrio entre costo, capacidad de procesamiento, facilidad de fabricación y funcionamiento continuo.
- **Desventaja:** Requiere sincronizar correctamente la faja, el giro de la papa, la captura de imágenes y la compuerta de separación.

---

### Solución Preliminar 2 — Mayor precisión y robustez

| Función | Elección |
| --- | --- |
| **T1. Proporcionar energía al sistema** | **T1.1 – Fuente AC 220 V** |
| **T2. Convertir la energía para los actuadores** | **T2.2 – Adaptador 12 V DC** |
| **T3. Alimentar Raspberry Pi y electrónica** | **T3.2 – Fuente USB-C 5 V** |
| **T4. Procesar imágenes y controlar el sistema** | **T4.2 – NVIDIA Jetson Orin Nano** |
| **T5. Capturar imágenes de las papas** | **T5.3 – Cámara global shutter** |
| **T6. Detectar el estado de la papa mediante IA** | **T6.2 – MobileNetV3** |
| **T7. Detectar presencia de una papa** | **T7.2 – Sensor ultrasónico** |
| **T8. Determinar posición y desplazamiento de las papas** | **T8.2 – Sensor Hall + imán** |
| **T9. Recibir y alimentar las papas al sistema** | **T9.2 – Tolva vibratoria** |
| **T10. Transportar las papas durante la inspección** | **T10.2 – Banda modular** |
| **T11. Girar y orientar la papa para visualizar distintas superficies** | **T11.2 – Dos bandas laterales** |
| **T12. Accionar el mecanismo de giro** | **T12.2 – Motor paso a paso** |
| **T13. Separar papa buena y papa mala** | **T13.2 – Empujador neumático** |
| **T14. Recibir las papas clasificadas** | **T14.2 – Dos canaletas inclinadas** |
| **T15. Mostrar el estado de clasificación** | **T15.2 – Pantalla OLED** |
| **T16. Transmitir resultados del sistema** | **T16.2 – Ethernet** |
| **T17. Permitir interacción con el operador** | **T17.3 – Pantalla táctil** |
| **T18. Construir la estructura principal** | **T18.3 – Acero inoxidable** |
| **T19. Fabricar soportes y piezas del prototipo** | **T19.3 – Acrílico cortado** |
| **T20. Proporcionar contacto adecuado con la papa durante el giro** | **T20.2 – Rodillo de silicona** |

#### ¿Cómo sería?

Esta alternativa utiliza componentes de mayor capacidad, como una **NVIDIA Jetson Orin Nano** y una **cámara global shutter**, permitiendo un procesamiento de imágenes más potente y una mejor captura de objetos en movimiento.

La alimentación se realiza mediante una **tolva vibratoria**, mientras que una **banda modular** transporta las papas. El movimiento y la orientación serían controlados mediante **dos bandas laterales** y un **motor paso a paso**.

La separación se realizaría con un **empujador neumático**, conduciendo las papas hacia **dos canaletas inclinadas**. Además, incorporaría una **pantalla OLED**, conexión Ethernet y una pantalla táctil para la interacción con el operador.

La estructura principal sería de **acero inoxidable**, con piezas fabricadas en acrílico.

- **Ventaja:** Ofrece mayor capacidad de procesamiento, precisión de captura, control de movimiento y robustez.
- **Desventaja:** Presenta un costo considerablemente mayor y aumenta la complejidad mecánica, electrónica y de fabricación.

---

### Solución Preliminar 3 — Alternativa de implementación diferente

| Función | Elección |
| --- | --- |
| **T1. Proporcionar energía al sistema** | **T1.2 – Batería 12 V** |
| **T2. Convertir la energía para los actuadores** | **T2.3 – Fuente regulable DC** |
| **T3. Alimentar Raspberry Pi y electrónica** | **T3.3 – Regulador LM2596** |
| **T4. Procesar imágenes y controlar el sistema** | **T4.3 – Mini PC** |
| **T5. Capturar imágenes de las papas** | **T5.2 – Cámara USB Full HD** |
| **T6. Detectar el estado de la papa mediante IA** | **T6.3 – EfficientNet-Lite** |
| **T7. Detectar presencia de una papa** | **T7.3 – Sensor láser** |
| **T8. Determinar posición y desplazamiento de las papas** | **T8.3 – Control por tiempo de la faja** |
| **T9. Recibir y alimentar las papas al sistema** | **T9.3 – Alimentador por faja inclinada** |
| **T10. Transportar las papas durante la inspección** | **T10.1 – Faja transportadora** |
| **T11. Girar y orientar la papa para visualizar distintas superficies** | **T11.3 – Base/plataforma giratoria** |
| **T12. Accionar el mecanismo de giro** | **T12.3 – Servomotor** |
| **T13. Separar papa buena y papa mala** | **T13.3 – Solenoide con paleta** |
| **T14. Recibir las papas clasificadas** | **T14.3 – Tolvas de almacenamiento** |
| **T15. Mostrar el estado de clasificación** | **T15.3 – Pantalla LCD/TFT** |
| **T16. Transmitir resultados del sistema** | **T16.3 – Bluetooth** |
| **T17. Permitir interacción con el operador** | **T17.2 – Botones físicos** |
| **T18. Construir la estructura principal** | **T18.2 – MDF / madera** |
| **T19. Fabricar soportes y piezas del prototipo** | **T19.2 – PLA impreso en 3D** |
| **T20. Proporcionar contacto adecuado con la papa durante el giro** | **T20.3 – Rodillo plástico texturizado** |

#### ¿Cómo sería?

Esta alternativa utiliza una **batería de 12 V**, un regulador LM2596 y un **Mini PC** como unidad de procesamiento. Las papas ingresan mediante un **alimentador por faja inclinada** y son transportadas hacia una **base o plataforma giratoria**.

La plataforma es accionada mediante un **servomotor**, mientras que una **cámara USB Full HD** captura las imágenes. La clasificación se realiza utilizando **EfficientNet-Lite**.

Después del análisis, un **solenoide con paleta** desvía la papa hacia una de las **tolvas de almacenamiento**. El sistema utiliza una pantalla LCD/TFT, Bluetooth y botones físicos para mostrar información e interactuar con el usuario.

La estructura podría fabricarse con **MDF o madera**, mientras que los soportes serían impresos en **PLA**.

- **Ventaja:** Permite experimentar con una arquitectura diferente y utiliza materiales de fabricación accesibles.
- **Desventaja:** La plataforma giratoria puede interrumpir el flujo continuo y el control por tiempo de la faja ofrece menor precisión para conocer la posición real de cada papa.

---

### Selección de la mejor solución

Después de comparar las tres propuestas, se selecciona la **Solución Preliminar 1** como la alternativa más adecuada para el desarrollo de **Kartoffelmachine**.

Esta solución es la que mejor se relaciona con la **Caja Negra** y el **Esquema de Funciones** planteados para el prototipo, debido a que integra una **Raspberry Pi 5**, una **Raspberry Pi Camera V3** y el modelo **YOLOv8n** para realizar la inspección mediante visión artificial.

En la parte mecánica utiliza una **tolva por gravedad**, una **faja transportadora** y **rodillos en configuración V**, permitiendo recibir, centrar, orientar y girar las papas durante la captura de imágenes. El **rodillo recubierto de TPU o goma** proporciona la fricción necesaria para realizar la rotación sin dañar significativamente la papa.

La combinación de un **sensor fotoeléctrico IR** y un **encoder rotativo** permite detectar la presencia de la papa y controlar mejor su posición durante el proceso. Una vez obtenida la clasificación mediante YOLOv8n, una **compuerta accionada por servomotor** dirige cada papa hacia el contenedor correspondiente.

A diferencia de la Solución 2, evita componentes de mayor costo y complejidad como una NVIDIA Jetson, un sistema neumático y una estructura completa de acero inoxidable. Frente a la Solución 3, mantiene un proceso más continuo y proporciona un mejor control sobre la orientación, el desplazamiento y la inspección de la papa.

Por estas razones, la **Solución Preliminar 1** representa la alternativa con mejor equilibrio entre **funcionalidad, costo, facilidad de fabricación, capacidad de procesamiento y viabilidad para construir el prototipo Kartoffelmachine**.

---

## Flujo general de Kartoffelmachine

```text
Papas Chaucha sin clasificar
            ↓
     Tolva por gravedad
            ↓
     Faja transportadora
            ↓
 Sensor fotoeléctrico IR
            ↓
  Rodillos en configuración V
            ↓
 Motorreductor + rodillo TPU/goma
            ↓
       Giro de la papa
            ↓
 Raspberry Pi Camera V3
            ↓
      Captura de imágenes
            ↓
       Raspberry Pi 5
            ↓
          YOLOv8n
            ↓
 Clasificación: buena / mala
            ↓
 Compuerta accionada por servomotor
          ↙       ↘
         ↓         ↓
    Papa buena   Papa mala
         ↓         ↓
 Contenedor 1   Contenedor 2
```

---

> **Nota para GitHub:** coloca las imágenes dentro de `Recursos/Imágenes/` con los nombres:
> `Caja_Negra_Kartoffelmachine.png`, `Esquema_Funciones_Kartoffelmachine.png` y `Matriz_Morfologica_Kartoffelmachine.png` para que se visualicen directamente desde este Markdown.
