# Clasificación de objetos «TomaTodo» y «Celular» con SenseCraft AI

**Práctica de laboratorio | Universidad Peruana Cayetano Heredia (UPCH)**  
**Fecha:** 13 de octubre de 2026  
**Plataforma:** [SenseCraft AI](https://sensecraft.seeed.cc/ai/)  
**Dispositivo objetivo y de pruebas:** XIAO ESP32S3 Sense  
**Tipo de práctica:** Preparación de datos, entrenamiento y prueba de un modelo personalizado de clasificación de imágenes.

## 1. Introducción

En esta actividad trabajé con **SenseCraft AI** para crear y probar un modelo de inteligencia artificial capaz de clasificar imágenes en dos categorías: **`TomaTodo`** y **`Celular`**. A diferencia de la práctica con el modelo preentrenado de género, en este caso se utilizó un **modelo personalizado** que aparece en el espacio de trabajo con el nombre **`Xiao_20261013223033 (TomaTodo, Celular)`**, versión **`1.0.0`**.

Realicé las pruebas utilizando la **XIAO ESP32S3 Sense** y su sistema de cámara. También exploré la posibilidad de capturar imágenes de entrenamiento desde la **webcam de la laptop**, funcionalidad disponible en la interfaz de SenseCraft AI. Finalmente, configuré una condición de salida para encender un LED cuando la clase `TomaTodo` fuera reconocida con una confianza superior al umbral establecido.

> **Importante:** se trata de **clasificación de la imagen completa** en dos categorías. No es un sistema de detección con recuadros que ubique físicamente cada objeto en la escena.

## 2. Objetivos

- Explorar el entrenamiento de clasificación de imágenes de SenseCraft AI.
- Definir las clases `TomaTodo` y `Celular`.
- Documentar la opción de adquisición de imágenes desde webcam y la elección del dispositivo objetivo.
- Realizar pruebas de inferencia con el modelo entrenado desde la XIAO ESP32S3 Sense.
- Registrar los resultados de clasificación que muestra la plataforma.
- Configurar una regla GPIO/LED basada en la clase `TomaTodo`.
- Conservar el conjunto de imágenes en `datos.zip` y el modelo de inferencia en formato `.tflite` para su publicación posterior en GitHub.

## 3. Materiales y herramientas

| Elemento | Utilidad |
|---|---|
| XIAO ESP32S3 Sense | Dispositivo donde se probó el modelo |
| Cámara de la XIAO | Captura de objetos en el espacio de trabajo |
| Laptop con webcam | Alternativa para recolectar imágenes en la página de entrenamiento |
| Cable USB de datos | Conexión entre el dispositivo y la laptop |
| SenseCraft AI en Google Chrome | Recolección, entrenamiento, despliegue, prueba y GPIO |
| Tomatodo | Objeto de la primera categoría |
| Teléfono celular | Objeto de la segunda categoría |
| `datos.zip` | Archivo que contendrá las fotografías de las dos clases |
| `modelo_tomatodo_celular.tflite` | Archivo del modelo que se añadirá a este repositorio |

## 4. Preparación del modelo

### 4.1. Revisión de la biblioteca y compatibilidad

Antes de entrenar, revisé las herramientas y los filtros de la plataforma. SenseCraft AI permite seleccionar tareas de detección o clasificación, además de filtrar modelos por el hardware compatible. En nuestro caso se trabajó con la **XIAO ESP32S3 Sense**.

![Filtros y tipos de tareas](imagenes/05_filtros_de_modelos.png)

*Figura 1. Filtros de tareas y dispositivos compatibles disponibles en SenseCraft AI.*

### 4.2. Primer intento de conexión

En el espacio de trabajo de la XIAO, la interfaz mostró el aviso **«No está conectado al dispositivo. Por favor conéctese primero»**. Mientras la placa no estaba conectada, las opciones de carga de modelo y vista previa aparecían deshabilitadas.

![Dispositivo desconectado](imagenes/01_dispositivo_desconectado.png)

*Figura 2. Estado inicial del espacio de trabajo sin conexión al dispositivo.*

Se conservó esta captura para registrar una dificultad inicial. Las capturas de resultados posteriores evidencian que el sistema finalmente logró ejecutar el modelo; no se puede determinar solo con las imágenes qué ajuste resolvió la conexión.

### 4.3. Acceso a la sección de entrenamiento

Ingresé a **Modelos → Entrenamiento → Detección de Clasificación de Imágenes**. La plataforma presenta tres etapas: **recolección de datos de clasificación**, **entrenamiento** y **despliegue/vista previa**.

En la pantalla inicial aparecen dos categorías con los nombres provisionales `Class 1` y `Class 2`. Después, el modelo utilizado en las pruebas aparece con las etiquetas definitivas `TomaTodo` y `Celular`.

![Pantalla inicial de entrenamiento](imagenes/02_entrenamiento_clases_iniciales.png)

*Figura 3. Pantalla inicial del entrenamiento con dos clases aún sin muestras visibles.*

Las clases se pueden renombrar usando el ícono de edición, y SenseCraft AI permite agregar nuevas categorías, importar imágenes de un dataset existente o exportar las imágenes capturadas.

### 4.4. Uso de la cámara de la laptop para capturar imágenes

Seleccioné la opción **Webcam** como fuente de entrada en la sección de recolección. La cámara de la laptop mostró video dentro de la propia página, y se habilitó la opción **«Mantener para grabar»**, con la que se pueden capturar imágenes de entrenamiento.

![Webcam habilitada en entrenamiento](imagenes/04_entrenamiento_webcam.png)

*Figura 4. Acceso a la webcam desde SenseCraft AI para la recolección de imágenes.*

Esta captura demuestra que la **webcam se puede utilizar como fuente de imágenes durante el entrenamiento**. No demuestra que una webcam pueda sustituir a la XIAO como dispositivo conectado en el **Espacio de trabajo** o como destino de despliegue.

Para construir un dataset útil se deben incorporar fotografías de cada categoría desde diferentes ángulos, posiciones e iluminaciones y evitar que el modelo dependa únicamente del fondo. El **número exacto de fotografías utilizadas en esta práctica aún debe verificarse con `datos.zip`**, que se añadirá posteriormente.

### 4.5. Selección del dispositivo objetivo

En la etapa **Paso 2: Entrenar**, revisé las opciones de hardware y seleccioné **XIAO ESP32S3 Sense** como dispositivo objetivo. La plataforma ofrece otras alternativas, pero el modelo de esta práctica se evaluó en la XIAO.

![Menú de selección de hardware](imagenes/03_seleccion_dispositivo_objetivo.png)

*Figura 5. Opciones del dispositivo objetivo, incluida la XIAO ESP32S3 Sense.*

### 4.6. Modelo personalizado resultante

En las capturas de la etapa de pruebas se observa un modelo cargado con la siguiente información:

| Campo | Información visible |
|---|---|
| Nombre mostrado | `Xiao_20261013223033 (TomaTodo, Celular)` |
| Versión | `1.0.0` |
| Tipo | Clasificación de imágenes |
| Categorías | `TomaTodo` y `Celular` |
| Dispositivo | XIAO ESP32S3 Sense |
| Archivo para el repositorio | `modelo/modelo_tomatodo_celular.tflite` (pendiente de incorporar) |

Aunque el modelo aparece ejecutándose, las capturas proporcionadas **no incluyen el historial del entrenamiento, la cantidad de épocas ni las métricas de entrenamiento o validación**. Esos datos no se estiman ni se inventan en esta documentación.

## 5. Pruebas de clasificación

### 5.1. Prueba con un tomatodo

Primero coloqué un tomatodo frente a la cámara. La plataforma presentó la clasificación **`TomaTodo: 100 %`** y **`Celular: 0 %`** en el fotograma registrado. También se aprecia el panel con la información del modelo y los registros de inferencia.

![Resultado TomaTodo](imagenes/06_resultado_tomatodo.png)

*Figura 6. Prueba del modelo con un tomatodo; predicción mostrada de 100 %.*

### 5.2. Prueba con un celular

Después coloqué un teléfono celular en el área de visión. En la captura se muestra la categoría **`Celular: 89 %`** y **`TomaTodo: 0 %`**.

![Resultado Celular](imagenes/07_resultado_celular.png)

*Figura 7. Prueba del modelo con un celular; predicción mostrada de 89 %.*

### 5.3. Resumen de resultados

| N.º | Objeto presentado | Clase mostrada | Confianza registrada | Evidencia |
|---:|---|---|---:|---|
| 1 | Tomatodo | `TomaTodo` | 100 % | Figura 6 |
| 2 | Celular | `Celular` | 89 % | Figura 7 |

**Interpretación:** en los fotogramas documentados el modelo asignó la clase esperada a los objetos presentados. Los porcentajes son salidas puntuales de confianza, **no representan la exactitud del modelo sobre un conjunto de prueba**. Para calcular una matriz de confusión y métricas como precisión, recall o accuracy, se requeriría evaluar múltiples imágenes etiquetadas que no hayan sido usadas en el entrenamiento.

## 6. Configuración de salida GPIO

Luego ingresé a **Salida → GPIO** y registré una acción que relaciona la clasificación `TomaTodo` con el encendido de un LED.

| Campo | Valor observado |
|---|---|
| Objeto / categoría | `TomaTodo` |
| Salida | `LED` |
| Condición | Mayor que |
| Confianza | `60` |
| Estado predeterminado | LED apagado |
| Estado activo | LED encendido |

![GPIO TomaTodo](imagenes/08_configuracion_gpio_tomatodo.png)

*Figura 8. Regla GPIO configurada para la categoría `TomaTodo`, confianza mayor que 60.*

La regla busca activar la salida cuando se cumple la condición configurada. La captura **verifica la configuración en la interfaz**, pero **no documenta de manera concluyente el cambio físico del LED**. Para completar esta prueba se recomienda registrar una foto o video en la que se observe el LED apagado y encendido mientras se alternan los objetos.

## 7. Evidencia física del trabajo

Además de las pruebas en pantalla, tomé una fotografía del montaje en el laboratorio donde se aprecia el cableado y el uso de la cámara/sistema de visión durante la clasificación de objetos.

<p align="center"><img src="imagenes/09_montaje_fisico.png" alt="Pruebas físicas de objetos en el laboratorio" width="560"></p>

*Figura 9. Evidencia del montaje físico empleado para realizar las pruebas con objetos.*

## 8. Dataset y archivo del modelo

Como parte de la entrega se incorporarán **dos archivos** adicionales. No están incluidos todavía en esta versión, por lo que sus contenidos y propiedades técnicas están **pendientes de verificación**.

### 8.1. Dataset: `datos.zip`

El archivo `datos/datos.zip` contendrá las fotografías utilizadas para las clases `TomaTodo` y `Celular`, reunidas en un único ZIP. Se recomienda organizarlas internamente de esta manera:

```text
datos.zip
├── TomaTodo/
│   ├── imagen_001.jpg
│   └── ...
└── Celular/
    ├── imagen_001.jpg
    └── ...
```

**Esta estructura es una recomendación para organizar la entrega**, no una inspección del ZIP real. Cuando se agregue el archivo, conviene indicar cuántas imágenes contiene cada carpeta, el formato de las fotografías y, si se conoce, la separación entre entrenamiento y validación.

### 8.2. Modelo: `modelo_tomatodo_celular.tflite`

En la carpeta `modelo/` se guardará el archivo exportado en formato **TensorFlow Lite (`.tflite`)**:

```text
modelo/
└── modelo_tomatodo_celular.tflite
```

El archivo `.tflite` permitirá conservar el artefacto de inferencia correspondiente a esta práctica. **Su compatibilidad, tamaño, entradas, salidas y cuantización deberán comprobarse a partir del archivo real una vez añadido**, en lugar de inferirlos solamente por la extensión.

### 8.3. Estructura de esta carpeta en GitHub

```text
02_Clasificacion_TomaTodo_Celular/
├── README.md
├── imagenes/
│   ├── 01_dispositivo_desconectado.png
│   ├── 02_entrenamiento_clases_iniciales.png
│   ├── 03_seleccion_dispositivo_objetivo.png
│   ├── 04_entrenamiento_webcam.png
│   ├── 05_filtros_de_modelos.png
│   ├── 06_resultado_tomatodo.png
│   ├── 07_resultado_celular.png
│   ├── 08_configuracion_gpio_tomatodo.png
│   └── 09_montaje_fisico.png
├── datos/
│   └── datos.zip                       # Por añadir
└── modelo/
    └── modelo_tomatodo_celular.tflite  # Por añadir
```

> Cuando agregues los archivos, respeta los nombres de las carpetas o actualiza las referencias del README si utilizas otros nombres.

## 9. Dificultades y limitaciones

1. **Conexión del dispositivo:** inicialmente la XIAO aparecía desconectada; después se consiguió ejecutar el modelo.
2. **Fuente de cámara:** se observó que SenseCraft AI admite webcam para la recolección de datos, pero no se comprobó un despliegue del modelo directamente sobre la webcam como dispositivo de hardware.
3. **Cantidad de datos:** todavía no se ha inspeccionado el archivo ZIP para verificar el número de imágenes por clase.
4. **Resultados limitados:** se dispone de capturas representativas, no de una evaluación estadística independiente.
5. **Acción GPIO:** se registró la condición del LED, pero no una prueba visible de su estado físico.
6. **Modelo exportado:** falta incorporar y verificar el archivo `.tflite`.

## 10. Conclusiones

Con esta práctica aprendí a utilizar la sección de entrenamiento de SenseCraft AI para definir dos categorías, trabajar con la cámara de la laptop durante la recolección y seleccionar la XIAO ESP32S3 Sense como dispositivo objetivo. Posteriormente probé el modelo personalizado en el espacio de trabajo y registré una predicción de **100 % para `TomaTodo`** y **89 % para `Celular`** en los fotogramas seleccionados.

También configuré una regla GPIO para activar una salida LED cuando `TomaTodo` alcance una confianza mayor que 60. Los resultados evidencian el funcionamiento del flujo de clasificación a nivel de interfaz, mientras que una evaluación más completa requeriría inspeccionar el dataset, analizar el `.tflite`, probar más imágenes y comprobar la activación física del LED.

## 11. Referencias (formato IEEE)

[1] Seeed Studio, «Entrenamiento de Clasificación de Imágenes con SenseCraft AI», *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/sensecraft-ai/tutorials/sensecraft-ai-training-classification/. [Accedido: 13-oct-2026].

[2] Seeed Studio, «Entrena rápidamente modelos de clasificación de imágenes en línea con SenseCraft AI», *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/train_classification_model_online/. [Accedido: 13-oct-2026].

[3] Seeed Studio, «Configuración de la salida del modelo y GPIO en SenseCraft AI para XIAO ESP32S3 Sense», *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/sensecraft_ai_output_gpio_xiao/. [Accedido: 13-oct-2026].

---

**Estado de entrega:** documentación e imágenes incluidas; `datos.zip` y el archivo `.tflite` pendientes de incorporar. Antes de hacer público el repositorio, revisar que ninguna imagen del dataset o las capturas exponga información privada o rostros sin autorización.
