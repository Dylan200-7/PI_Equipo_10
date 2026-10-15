# TinyML con Edge Impulse — Cargador y Mouse

En esta práctica desarrollamos un modelo de clasificación de imágenes para reconocer **cargadores** y **mouse**. Lo entrenamos en Edge Impulse y realizamos pruebas con Arduino IDE y SenseCraft usando la cámara XIAO ESP32S3 Sense.

## 1. Proyecto y dataset

Creamos nuestro proyecto en Edge Impulse y trabajamos con imágenes etiquetadas en dos clases: **Cargador** y **Mouse**.

![Proyecto en Edge Impulse](Imagenes/01_Proyecto_Edge_Impulse.png)

**Dataset:** Reunimos **100 imágenes JPG**, distribuidas en dos clases (50 de **Cargador** y 50 de **Mouse**). Se incluyen en `Data.zip`, con un ZIP y una carpeta etiquetada por cada clase.

## 2. Configuración y entrenamiento

Configuramos imágenes de **96 × 96 píxeles**, en formato **RGB**, y usamos **Transfer Learning (MobileNetV2)**. Entrenamos durante **30 ciclos**, con una tasa de aprendizaje de **0.0005**.

![Configuración del impulse](Imagenes/02_Diseno_Impulse.png)

![Procesamiento de las imágenes](Imagenes/03_Procesamiento_Imagen.png)

## 3. Pruebas estadísticas

**Prueba 1 — Validación del entrenamiento:** alcanzamos **100 % de accuracy** y **0.01 de loss** en el conjunto de validación mostrado por Edge Impulse.

![Resultados de entrenamiento y validación](Imagenes/04_Entrenamiento_Validacion.png)

**Prueba 2 — Evaluación del modelo:** en las imágenes de prueba obtuvimos **100 % de accuracy** y valores de **1.00** para precisión, recall y F1 promedio ponderados.

![Resultados del conjunto de prueba](Imagenes/06_Evaluacion_Modelo.png)

Estos resultados corresponden a los conjuntos evaluados en la plataforma.

## 4. Pruebas en Edge Impulse y Arduino IDE

Primero verificamos imágenes por separado: el modelo reconoció un **cargador** y un **mouse** con puntuaciones de **1.00** para su clase correspondiente.

![Clasificación de cargador](Imagenes/05_Prueba_Cargador.png)

![Clasificación de mouse](Imagenes/08_Prueba_Mouse.png)

Después exportamos el modelo cuantizado **int8** como biblioteca para Arduino IDE y realizamos pruebas con la cámara XIAO ESP32S3 Sense, revisando las predicciones en el monitor serie.

![Exportación de la biblioteca Arduino](Imagenes/07_Exportacion_Arduino.png)

![Prueba de cargador en Arduino IDE](Imagenes/12_Arduino_Cargador.png)

![Prueba de mouse en Arduino IDE](Imagenes/10_Arduino_Mouse.png)

## 5. Pruebas en SenseCraft

Importamos el modelo TensorFlow Lite en SenseCraft y comprobamos la clasificación de ambos objetos con la cámara.

![Cargador en SenseCraft](Imagenes/11_SenseCraft_Cargador.png)

![Mouse en SenseCraft](Imagenes/09_SenseCraft_Mouse.png)

## Archivos del proyecto

- `Imagenes/`: capturas y fotografías de nuestras pruebas.
- `Data.zip`: dataset original de 100 imágenes, agrupadas en `Cargador_images_50.zip` y `Mouse_images_50.zip`.
- `Modelo.zip`: contiene `Modelo_Arduino.zip` (biblioteca para Arduino IDE) y `Modelo_SenseCraft.tflite` (modelo para SenseCraft).

**Referencia:** [1] UPCH, *Guía TinyML con Edge Impulse*, material de laboratorio, 2026.
