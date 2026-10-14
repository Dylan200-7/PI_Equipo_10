
# Detección de género con SenseCraft AI

**Universidad:** Universidad Peruana Cayetano Heredia (UPCH)  
**Fecha:** 13/10/2026  
**Dispositivo:** XIAO ESP32S3 Sense

## 1. Ingreso a SenseCraft AI

Primero ingresamos a la plataforma [SenseCraft AI](https://sensecraft.seeed.cc/ai/) y entramos a la sección **Modelos**, donde encontramos diferentes modelos de inteligencia artificial disponibles.

![Biblioteca de modelos](imagenes/01_biblioteca_general.png)

*Figura 1. Biblioteca de modelos de SenseCraft AI.*

Después filtramos los modelos compatibles con **XIAO ESP32S3 Sense**, que era el dispositivo que estábamos utilizando.

![Modelos compatibles](imagenes/02_biblioteca_xiao.png)

*Figura 2. Modelos compatibles con XIAO ESP32S3 Sense.*

Entre las opciones seleccionamos **Detección de género**, un modelo preentrenado que permite detectar rostros y mostrar las etiquetas `male` y `female` con un nivel de confianza.

![Modelo seleccionado](imagenes/03_ficha_modelo_genero.png)

*Figura 3. Modelo de detección de género seleccionado.*

## 2. Conexión del dispositivo

Luego ingresamos a **Espacio de trabajo** y conectamos la XIAO ESP32S3 Sense a la laptop mediante USB.

Durante uno de los intentos apareció el mensaje **"No se encontraron dispositivos compatibles"**, por lo que inicialmente no pudimos ejecutar el modelo.

![Error de conexión](imagenes/04_conexion_sin_dispositivo.png)

*Figura 4. Problema durante la conexión del dispositivo.*

Después logramos establecer la conexión y comenzamos a utilizar la vista previa del modelo.

La configuración que utilizamos fue:

| Parámetro | Valor |
|---|---|
| Modelo | Detección de género |
| Confianza | 60 |
| Umbral IoU | 14 |
| Modo de inferencia | UART(GPIO) |

## 3. Pruebas de detección

### 3.1. Detección MALE [Josue Mogollon]

Para comenzar colocamos a uno de los integrantes frente a la cámara.

Observamos que el modelo detectó el rostro mediante un recuadro rojo y mostró la etiqueta `male` con una confianza de **91 %**.

![Detección male](imagenes/05_resultado_male.png)

*Figura 5. Resultado obtenido durante la detección male.*

### 3.2. Detección FEMALE [Dayra Kuang]

Después realizamos otra prueba colocando a una compañera frente a la cámara.

En esta ocasión apareció un recuadro verde alrededor del rostro, mostrando la etiqueta `female` con una confianza de **86 %**.

![Detección female](imagenes/06_resultado_female_adicional.png)

*Figura 6. Primera prueba con la etiqueta female.*

También realizamos otra captura cambiando un poco la posición frente a la cámara.

![Segunda detección female](imagenes/07_resultado_female.png)

*Figura 7. Segunda prueba de detección female.*

Con estas pruebas observamos cómo el modelo realizaba las detecciones en tiempo real y mostraba los resultados en la plataforma.

Cabe mencionar que las etiquetas son estimaciones visuales realizadas por el modelo y no determinan la identidad de género real de una persona.

## 4. Configuración GPIO

Después ingresamos a **Salida → GPIO** para configurar una acción relacionada con la detección.

Establecimos una condición para que el LED se active cuando el modelo detecte la etiqueta `male` con una confianza mayor a 54.

| Parámetro | Configuración |
|---|---|
| Objeto | male |
| GPIO | LED |
| Condición | Mayor que |
| Confianza | 54 |
| Estado inicial | LED apagado |
| Estado activo | LED encendido |

![Configuración GPIO](imagenes/08_configuracion_gpio_male.png)

*Figura 8. Configuración GPIO para la detección male.*

Con esta parte conocimos cómo se puede relacionar el resultado de una detección con una salida del dispositivo. En la captura quedó registrada la configuración, aunque no se muestra el encendido físico del LED.

## 5. Prueba en el laboratorio

Durante la actividad también tomamos una fotografía del trabajo realizado con SenseCraft AI y la XIAO ESP32S3 Sense.

![Prueba en laboratorio](imagenes/09_montaje_fisico.png)

*Figura 9. Prueba realizada durante el laboratorio.*

## 6. Resultados

| Prueba | Resultado | Confianza |
|---|---|---|
| Detección MALE | male | 91 % |
| Detección FEMALE | female | 86 % |
| Configuración GPIO | LED asociado a male | Mayor a 54 |

Durante las pruebas logramos visualizar ambas etiquetas en la plataforma junto con sus porcentajes de confianza.

Estos porcentajes corresponden a las predicciones observadas y no representan la precisión general del modelo.

## 7. Conclusión

En esta práctica aprendimos a utilizar un modelo preentrenado de SenseCraft AI y ejecutarlo con la XIAO ESP32S3 Sense.

Realizamos pruebas de detección en tiempo real y configuramos una condición GPIO relacionada con los resultados del modelo.

También aprendimos a manejar mejor la plataforma y a identificar algunos problemas que pueden aparecer durante la conexión del dispositivo.

## 8. Referencias

[1] Seeed Studio, "SenseCraft AI", *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/sensecraft-ai/overview/.

[2] Seeed Studio, "Configuración de salida GPIO en SenseCraft AI para XIAO ESP32S3 Sense", *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/sensecraft_ai_output_gpio_xiao/.
