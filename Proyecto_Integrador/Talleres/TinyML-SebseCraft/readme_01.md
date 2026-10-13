# Detección de género aparente con SenseCraft AI — XIAO ESP32S3 Sense

**Práctica de laboratorio | Universidad Peruana Cayetano Heredia (UPCH)**  
**Fecha:** 13 de octubre de 2026  
**Plataforma:** [SenseCraft AI](https://sensecraft.seeed.cc/ai/)  
**Dispositivo utilizado:** XIAO ESP32S3 Sense  
**Tipo de práctica:** Ejecución y evaluación básica de un modelo preentrenado de detección visual.

## 1. Introducción

En esta práctica utilicé **SenseCraft AI** para ejecutar un modelo de visión artificial previamente entrenado, denominado **«Detección de género»** en la biblioteca de la plataforma. El modelo genera dos etiquetas de salida, `male` y `female`, y muestra un recuadro sobre el rostro detectado acompañado de un valor de confianza.

El objetivo fue conocer el procedimiento para seleccionar un modelo compatible con la **XIAO ESP32S3 Sense**, visualizar sus predicciones en tiempo real y configurar una respuesta mediante la salida **GPIO/LED**. No entrené este modelo desde cero; el trabajo consistió en seleccionar, ejecutar y probar un modelo existente.

> **Alcance:** `male` y `female` son las *etiquetas estimadas por un modelo a partir de la imagen*. No representan una verificación de la identidad de género de una persona. Los valores de confianza mostrados en la interfaz tampoco equivalen a una medición de exactitud global del sistema.

## 2. Objetivos

- Explorar la biblioteca de modelos preentrenados de SenseCraft AI.
- Identificar un modelo compatible con XIAO ESP32S3 Sense.
- Establecer la comunicación entre la placa y la plataforma web.
- Evaluar visualmente las salidas `male` y `female` utilizando la cámara del dispositivo.
- Configurar una acción de salida LED condicionada por la detección.
- Registrar las capturas, los resultados y las limitaciones observadas.

## 3. Materiales y herramientas

| Elemento | Uso |
|---|---|
| XIAO ESP32S3 Sense | Ejecución del modelo y captura de video mediante su cámara |
| Cámara de la XIAO | Obtención de las imágenes de prueba |
| Cable USB de datos | Comunicación y alimentación desde la laptop |
| Laptop con Google Chrome | Acceso a SenseCraft AI y conexión serial desde el navegador |
| Modelo «Detección de género» | Modelo preentrenado seleccionado desde la biblioteca |
| SenseCraft AI | Selección, ejecución, monitoreo y configuración de GPIO |

## 4. Procedimiento realizado

### 4.1. Exploración de la biblioteca de modelos

Primero ingresé a **SenseCraft AI → Modelos → Biblioteca de modelos**. Revisé las categorías disponibles, incluyendo detección y clasificación, y observé las opciones de filtrado por dispositivo compatible. Esto permitió reducir la búsqueda a modelos que pueden utilizarse con la placa del laboratorio.

![Vista general de la biblioteca de modelos](imagenes/01_biblioteca_general.png)

*Figura 1. Vista general de los modelos disponibles en SenseCraft AI.*

A continuación utilicé el filtro **XIAO ESP32S3 Sense**, con el cual apareció el modelo «Detección de género» entre las alternativas de la biblioteca.

![Biblioteca filtrada por XIAO](imagenes/02_biblioteca_xiao.png)

*Figura 2. Biblioteca filtrada por compatibilidad con XIAO ESP32S3 Sense.*

### 4.2. Selección del modelo de detección de género

Abrí la ficha del modelo «Detección de género». En la descripción visible se indica que el modelo está basado en **Swift-YOLO** y corresponde a una tarea de detección. A diferencia de un clasificador que asigna una etiqueta a toda la imagen, esta prueba muestra una región delimitada sobre el rostro.

![Ficha del modelo de detección de género](imagenes/03_ficha_modelo_genero.png)

*Figura 3. Ficha del modelo preentrenado seleccionada en la biblioteca.*

### 4.3. Conexión del dispositivo y dificultad inicial

Ingresé a **Espacio de trabajo → XIAO ESP32S3 Sense** para establecer la conexión con el dispositivo por USB. Durante uno de los intentos, Google Chrome mostró la ventana de acceso al puerto serie con el mensaje **«No se encontraron dispositivos compatibles»**. En ese estado el espacio de trabajo también indicaba que no había ningún dispositivo conectado.

![Intento de conexión serial sin dispositivo disponible](imagenes/04_conexion_sin_dispositivo.png)

*Figura 4. Registro del intento fallido de conexión desde el navegador.*

Este problema demuestra que el modelo no podía ponerse en ejecución en ese momento. Posteriormente, las capturas de inferencia muestran que la placa sí llegó a estar conectada y ejecutando el modelo; no quedó documentado en las imágenes cuál fue el ajuste exacto que resolvió el intento anterior.

**Comprobaciones recomendadas si vuelve a ocurrir:** verificar que el cable USB transfiera datos, que el dispositivo sea detectado por Windows, que no exista otro programa ocupando el puerto serie y que Chrome tenga permiso para acceder a él. Estas comprobaciones son recomendaciones de diagnóstico, no acciones confirmadas en la evidencia.

### 4.4. Ejecución del modelo y configuración de inferencia

Una vez conectada la placa, trabajé en la pantalla de vista previa. Las capturas muestran los siguientes parámetros de ejecución:

| Parámetro | Valor visible |
|---|---|
| Modelo | Detección de género (preentrenado) |
| Etiquetas | `male`, `female` |
| Confianza mínima | `60` sobre 100 |
| Umbral IoU | `14` sobre 100 |
| Modo de inferencia al encender | `UART(GPIO)` |
| Tipo de resultado | Recuadro de detección y etiqueta con confianza |

El **umbral de confianza** se utiliza para filtrar predicciones por debajo de un valor configurado. El **IoU** está relacionado con el solapamiento de regiones detectadas; el efecto concreto del ajuste puede depender de la implementación del modelo.

### 4.5. Prueba de la etiqueta `male`

Coloqué a una persona frente a la cámara y comprobé que la interfaz mostrara el recuadro sobre el rostro. En la captura, el modelo devolvió la etiqueta **`male: 91`**, que corresponde a un nivel de confianza de **91/100** para esa predicción.

![Predicción male](imagenes/05_resultado_male.png)

*Figura 5. Predicción `male: 91` mostrada en la vista previa.*

### 4.6. Prueba de la etiqueta `female`

Repetí el procedimiento con otra persona frente a la cámara. El modelo mostró **`female: 86`**, con el recuadro ubicado sobre el rostro visible. Se conservan dos capturas de la misma clase para evidenciar la ejecución en diferentes encuadres.

![Predicción female en vista adicional](imagenes/06_resultado_female_adicional.png)

*Figura 6. Predicción `female: 86` en una primera vista de prueba.*

![Predicción female](imagenes/07_resultado_female.png)

*Figura 7. Predicción `female: 86` registrada en otro encuadre.*

### 4.7. Configuración de una acción GPIO para `male`

Después ingresé a **Salida → GPIO → Acciones de activación**. Configuré una regla para que la salida de tipo LED cambiara de estado cuando la etiqueta `male` superara el umbral indicado.

| Campo | Configuración registrada |
|---|---|
| Objeto o etiqueta | `male` |
| GPIO / salida | `LED` |
| Condición | Mayor que |
| Confianza | `54` |
| Estado predeterminado | LED apagado |
| Estado activo | LED encendido |

![Regla GPIO para male](imagenes/08_configuracion_gpio_male.png)

*Figura 8. Regla de activación del LED para `male` con confianza mayor que 54.*

Esta configuración **es distinta del umbral de confianza general de la vista previa (60)**. La captura permite verificar que la regla fue registrada en la interfaz, pero **no permite confirmar por sí sola que el LED se encendió físicamente** o que el comando se transmitió correctamente a la placa.

### 4.8. Evidencia del montaje en el laboratorio

Además de las capturas de pantalla, registré el montaje físico: una laptop con SenseCraft AI abierto y la conexión de cámara/dispositivo utilizada durante la demostración.

<p align="center"><img src="imagenes/09_montaje_fisico.png" alt="Montaje físico en el laboratorio" width="560"></p>

*Figura 9. Evidencia fotográfica de la práctica con la laptop y el sistema de visión.*

## 5. Resultados observados

| Prueba | Etiqueta mostrada | Confianza observada | Evidencia |
|---|---|---:|---|
| 1 | `male` | 91/100 | Figura 5 |
| 2 | `female` | 86/100 | Figuras 6 y 7 |
| 3 | Activación condicional del LED para `male` | Umbral >54 | Figura 8; solo configuración visible |

Durante la ejecución, SenseCraft AI también mostró mensajes de registro asociados con las predicciones y el rendimiento de las etapas de procesamiento. Estos registros evidencian que el modelo se encontraba realizando inferencias; no se utilizaron para calcular métricas de validación.

**Interpretación:** el objetivo de demostración se cumplió a nivel de interfaz, pues se observaron ambas etiquetas y sus recuadros. Con estas pocas capturas no es posible concluir una tasa de precisión, sensibilidad, exactitud ni desempeño general para otros participantes o entornos.

## 6. Dificultades y limitaciones

1. **Conexión serial:** en un intento no se detectó un dispositivo compatible, aunque posteriormente se registró la ejecución del modelo.
2. **Condiciones de iluminación y encuadre:** pueden afectar las predicciones; no se realizó una evaluación sistemática con diferentes escenarios.
3. **Alcance de las etiquetas:** el modelo estima clases visuales `male/female` y no determina la identidad personal ni la identidad de género real.
4. **Salida GPIO:** se documentó la configuración de la acción, pero no una medición eléctrica ni una fotografía concluyente del LED activado.
5. **Métricas:** la confianza de una predicción no sustituye una evaluación con conjunto de prueba etiquetado.

## 7. Conclusiones

En esta actividad aprendí a buscar un modelo preentrenado en SenseCraft AI, vincularlo con la XIAO ESP32S3 Sense y observar sus resultados de detección en tiempo real. Durante las pruebas registré las etiquetas `male: 91` y `female: 86`, junto con la configuración de una salida GPIO asociada a `male`.

La práctica también permitió identificar la importancia de la conexión serial y de registrar los errores durante el proceso. Como trabajo complementario, sería necesario repetir las pruebas bajo distintas condiciones y comprobar físicamente la respuesta del LED para evaluar el funcionamiento completo del sistema.

## 8. Referencias (formato IEEE)

[1] Seeed Studio, «Centro de Documentación de SenseCraft AI», *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/sensecraft-ai/sensecraft-ai-main/. [Accedido: 13-oct-2026].

[2] Seeed Studio, «Configuración de la salida del modelo y GPIO en SenseCraft AI para XIAO ESP32S3 Sense», *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/sensecraft_ai_output_gpio_xiao/. [Accedido: 13-oct-2026].

[3] Seeed Studio, «SenseCraft AI: Entrena e Implementa Modelos de Edge AI», *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/sensecraft-ai/overview/. [Accedido: 13-oct-2026].

---

**Nota para publicación:** las evidencias incluyen imágenes de personas y elementos de la interfaz del laboratorio. Antes de hacer público el repositorio, confirmar que se cuenta con permiso para difundir los rostros y revisar identificadores o datos de las capturas.
