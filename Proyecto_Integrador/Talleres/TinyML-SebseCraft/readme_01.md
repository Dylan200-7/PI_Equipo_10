
# Detección de género con SenseCraft AI

**Universidad:** Universidad Peruana Cayetano Heredia (UPCH)  
**Fecha:** 13/10/2026  
**Plataforma:** SenseCraft AI  
**Dispositivo:** XIAO ESP32S3 Sense

## 1. Introducción

En esta práctica utilizamos SenseCraft AI para probar un modelo de inteligencia artificial previamente entrenado, el cual permite detectar rostros y clasificarlos mediante las etiquetas `male` y `female`.

Nuestro objetivo fue conocer el funcionamiento de la plataforma, conectar la XIAO ESP32S3 Sense, ejecutar el modelo en tiempo real y configurar una salida GPIO según las detecciones realizadas.

## 2. Materiales utilizados

- XIAO ESP32S3 Sense.
- Cámara del dispositivo.
- Laptop.
- Cable USB.
- Navegador Google Chrome.
- Plataforma SenseCraft AI.

## 3. Procedimiento

### 3.1. Ingreso a SenseCraft AI

Primero ingresamos a la página oficial de [SenseCraft AI](https://sensecraft.seeed.cc/ai/) desde Google Chrome.

Una vez dentro, seleccionamos el apartado **Modelos**, donde encontramos la biblioteca con diferentes modelos de inteligencia artificial.

Revisamos las opciones disponibles para conocer qué modelos podíamos utilizar durante la práctica.

![Biblioteca de modelos](imagenes/01_biblioteca_general.png)

*Figura 1. Biblioteca de modelos de SenseCraft AI.*

### 3.2. Búsqueda del modelo

Después utilizamos el filtro de dispositivos compatibles y seleccionamos **XIAO ESP32S3 Sense**.

De esta manera pudimos visualizar únicamente los modelos disponibles para trabajar con nuestra placa.

![Modelos compatibles](imagenes/02_biblioteca_xiao.png)

*Figura 2. Modelos compatibles con XIAO ESP32S3 Sense.*

### 3.3. Selección del modelo de género

Entre los modelos disponibles seleccionamos **Detección de género**.

Según la descripción de la plataforma, este modelo utiliza Swift-YOLO y permite detectar rostros, mostrando un recuadro con la etiqueta y su confianza.

En esta actividad utilizamos el modelo directamente desde la biblioteca, sin necesidad de entrenarlo nuevamente.

![Modelo de género](imagenes/03_ficha_modelo_genero.png)

*Figura 3. Modelo preentrenado de detección de género.*

### 3.4. Conexión de la XIAO ESP32S3 Sense

Luego ingresamos a **Espacio de trabajo** y seleccionamos la XIAO ESP32S3 Sense.

Conectamos el dispositivo a la laptop mediante un cable USB e intentamos establecer comunicación desde el navegador.

Durante uno de los intentos apareció el mensaje **"No se encontraron dispositivos compatibles"**, por lo que inicialmente no pudimos continuar con la ejecución.

![Problema de conexión](imagenes/04_conexion_sin_dispositivo.png)

*Figura 4. Problema presentado al intentar conectar la XIAO.*

Posteriormente logramos conectar el dispositivo y continuar con las pruebas.

### 3.5. Ejecución del modelo

Una vez conectado el dispositivo, seleccionamos el modelo y comenzamos a utilizar la vista previa.

La plataforma mostraba la imagen de la cámara y los resultados de detección en tiempo real.

Durante las pruebas utilizamos la siguiente configuración:

| Parámetro | Valor |
|---|---|
| Modelo | Detección de género |
| Confianza | 60 |
| Umbral IoU | 14 |
| Modo de inferencia | UART(GPIO) |
| Etiquetas | male y female |

### 3.6. Prueba de detección MALE

Para realizar la primera prueba colocamos a uno de los integrantes del grupo frente a la cámara.

Observamos que el modelo detectaba el rostro mediante un recuadro rojo y mostraba la etiqueta `male`.

El resultado obtenido fue:

- **Etiqueta:** male.
- **Confianza:** 91 %.

![Detección male](imagenes/05_resultado_male.png)

*Figura 5. Resultado obtenido durante la detección male.*

También observamos que el registro del dispositivo mostraba información relacionada con las detecciones.

### 3.7. Prueba de detección FEMALE

Después realizamos otra prueba colocando a una compañera frente a la cámara.

En este caso el modelo mostró un recuadro verde alrededor del rostro y presentó la etiqueta `female`.

El resultado observado fue:

- **Etiqueta:** female.
- **Confianza:** 86 %.

![Detección female](imagenes/06_resultado_female_adicional.png)

*Figura 6. Primera prueba de detección female.*

También realizamos una segunda captura cambiando la posición frente a la cámara.

![Segunda detección female](imagenes/07_resultado_female.png)

*Figura 7. Segunda prueba de detección female.*

Con estas pruebas observamos que el modelo generaba predicciones mientras recibía imágenes de la cámara.

Las etiquetas corresponden a estimaciones visuales del modelo y no determinan la identidad de género real de una persona.

### 3.8. Configuración GPIO

Después de realizar las detecciones ingresamos a **Salida → GPIO**.

En esta sección configuramos una condición para que el LED se active cuando el modelo detecte la etiqueta `male` con una confianza mayor a 54.

Los parámetros utilizados fueron:

| Parámetro | Configuración |
|---|---|
| Objeto | male |
| GPIO | LED |
| Condición | Mayor que |
| Confianza | 54 |
| Estado inicial | LED apagado |
| Estado activo | LED encendido |

![Configuración GPIO](imagenes/08_configuracion_gpio_male.png)

*Figura 8. Configuración de GPIO para la detección male.*

Con esta parte conocimos cómo relacionar los resultados del modelo con una salida del dispositivo.

La captura muestra la condición configurada, aunque no permite comprobar físicamente el encendido del LED.

### 3.9. Evidencia de la práctica

Durante el desarrollo de la actividad también registramos una fotografía del equipo utilizado y de la detección que se estaba realizando.

![Prueba en laboratorio](imagenes/09_montaje_fisico.png)

*Figura 9. Prueba del modelo de detección de género en el laboratorio.*

## 4. Resultados obtenidos

| Prueba | Resultado | Confianza |
|---|---|---|
| Detección MALE | male | 91 % |
| Detección FEMALE | female | 86 % |
| Configuración GPIO | LED asociado a male | Mayor a 54 |

Durante las pruebas observamos que el modelo mostraba los rostros detectados mediante recuadros y asignaba una etiqueta con su respectivo nivel de confianza.

Los porcentajes corresponden a las predicciones observadas y no representan la precisión general del modelo.

## 5. Dificultades encontradas

Una de las dificultades fue la conexión inicial de la XIAO ESP32S3 Sense, ya que el navegador no encontraba dispositivos compatibles.

También tuvimos que explorar las opciones de SenseCraft AI para aprender a seleccionar el modelo, visualizar las detecciones y configurar las acciones GPIO.

## 6. Conclusiones

En esta práctica aprendimos a utilizar un modelo preentrenado de SenseCraft AI y ejecutarlo con la XIAO ESP32S3 Sense.

Logramos realizar pruebas de detección con las etiquetas `male` y `female`, obteniendo valores de confianza de 91 % y 86 %, respectivamente.

Además, conocimos cómo configurar una acción GPIO a partir de los resultados del modelo.

Esta actividad nos ayudó a comprender mejor cómo funcionan los modelos de visión artificial en tiempo real.

## 7. Referencias

[1] Seeed Studio, "SenseCraft AI", *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/sensecraft-ai/overview/.

[2] Seeed Studio, "Configuración de salida GPIO en SenseCraft AI para XIAO ESP32S3 Sense", *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/sensecraft_ai_output_gpio_xiao/.
