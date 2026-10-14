
# Clasificación de Tomatodo y Celular con SenseCraft AI

**Universidad:** Universidad Peruana Cayetano Heredia (UPCH)  
**Fecha:** 13/10/2026  
**Dispositivo:** XIAO ESP32S3 Sense

## 1. Preparación del entrenamiento

En esta actividad trabajamos con SenseCraft AI para entrenar un modelo que pudiera diferenciar dos objetos: un **tomatodo** y un **celular**.

Primero revisamos las opciones de clasificación disponibles en la plataforma.

![Filtros de modelos](imagenes/05_filtros_de_modelos.png)

*Figura 1. Opciones de clasificación de imágenes en SenseCraft AI.*

Luego ingresamos a **Modelos → Entrenamiento → Clasificación de imágenes**.

En esta sección encontramos dos categorías iniciales llamadas `Class 1` y `Class 2`, que podían modificarse según los objetos que queríamos reconocer.

Para nuestra práctica trabajamos con:

- **TomaTodo**
- **Celular**

![Categorías del modelo](imagenes/02_entrenamiento_clases_iniciales.png)

*Figura 2. Pantalla inicial para preparar las categorías del modelo.*

## 2. Recolección de imágenes

Para preparar el entrenamiento utilizamos imágenes del tomatodo y del celular.

También probamos la opción **Webcam** para utilizar la cámara de la laptop directamente desde SenseCraft AI.

La plataforma mostraba la vista previa y la opción **Mantener para grabar**, que permite recolectar imágenes para el entrenamiento.

![Webcam](imagenes/04_entrenamiento_webcam.png)

*Figura 3. Prueba de la webcam para recolectar imágenes.*

Las fotografías utilizadas se guardaron en un archivo llamado `datos.zip`, donde reunimos las imágenes de las dos categorías.

## 3. Entrenamiento del modelo

Después de preparar las categorías y las imágenes, continuamos con el entrenamiento.

Para ello revisamos los dispositivos compatibles y seleccionamos **XIAO ESP32S3 Sense**, ya que era la placa que utilizábamos durante el laboratorio.

![Selección del dispositivo](imagenes/03_seleccion_dispositivo_objetivo.png)

*Figura 4. Selección del dispositivo para el modelo.*

El modelo personalizado que utilizamos en las pruebas mostró la siguiente información:

| Parámetro | Información |
|---|---|
| Nombre | Xiao_20261013223033 |
| Versión | 1.0.0 |
| Tipo | Clasificación de imágenes |
| Categorías | TomaTodo y Celular |
| Dispositivo | XIAO ESP32S3 Sense |

Una vez disponible el modelo, continuamos con las pruebas para comprobar sus resultados.

## 4. Pruebas del modelo

Al ingresar al espacio de trabajo, inicialmente la plataforma indicaba que no había ningún dispositivo conectado.

![Dispositivo desconectado](imagenes/01_dispositivo_desconectado.png)

*Figura 5. Espacio de trabajo antes de conectar la XIAO.*

Posteriormente logramos conectar el dispositivo y ejecutar el modelo desde la vista previa.

### 4.1. Prueba con el TOMATODO

Primero colocamos el tomatodo frente a la cámara.

Observamos que el modelo mostró los siguientes resultados:

- **TomaTodo:** 100 %
- **Celular:** 0 %

![Clasificación Tomatodo](imagenes/06_resultado_tomatodo.png)

*Figura 6. Resultado obtenido con el tomatodo.*

En esta prueba el modelo identificó correctamente el objeto que estábamos mostrando.

### 4.2. Prueba con el CELULAR

Después retiramos el tomatodo y colocamos un celular frente a la cámara para comprobar si el modelo podía diferenciar ambos objetos.

Los resultados observados fueron:

- **Celular:** 89 %
- **TomaTodo:** 0 %

![Clasificación Celular](imagenes/07_resultado_celular.png)

*Figura 7. Resultado obtenido con el celular.*

Con esta prueba comprobamos que el modelo mostraba una predicción diferente dependiendo del objeto que colocábamos frente a la cámara.

## 5. Resultados obtenidos

| Prueba | Objeto reconocido | Confianza |
|---|---|---|
| 1 | TomaTodo | 100 % |
| 2 | Celular | 89 % |

Durante las pruebas el modelo logró clasificar correctamente los dos objetos.

Estos resultados corresponden a las capturas realizadas durante la práctica. Para conocer mejor el desempeño del modelo sería necesario realizar más pruebas con diferentes posiciones e iluminaciones.

### Configuración GPIO

También configuramos una acción GPIO para que el LED se active cuando el modelo detecte la categoría `TomaTodo` con una confianza mayor a 60.

| Parámetro | Configuración |
|---|---|
| Objeto | TomaTodo |
| GPIO | LED |
| Condición | Mayor que |
| Confianza | 60 |
| Estado inicial | LED apagado |
| Estado activo | LED encendido |

![GPIO Tomatodo](imagenes/08_configuracion_gpio_tomatodo.png)

*Figura 8. Configuración GPIO para la categoría TomaTodo.*

La captura muestra la regla configurada, aunque no permite verificar el encendido físico del LED.

### Prueba en el laboratorio

También registramos una fotografía de la prueba realizada con el tomatodo frente a la cámara del dispositivo.

![Prueba Tomatodo](imagenes/09_montaje_fisico%20%281%29.png)

*Figura 9. Prueba realizada con el tomatodo en el laboratorio.*

## 6. Archivos del modelo

Para mantener organizado nuestro trabajo guardamos tanto las imágenes utilizadas como el archivo del modelo.

**Dataset:** contiene las fotografías del tomatodo y del celular utilizadas durante el trabajo.

[Ver datos.zip](data.zip)

**Modelo entrenado:** archivo del modelo en formato TensorFlow Lite.

[Ver modelo .tflite](modelo_tomatodo_celular.tflite)

Estos archivos se incluirán en el repositorio para conservar los recursos de la práctica.

## 7. Conclusión

En esta actividad aprendimos a preparar imágenes y trabajar con las herramientas de entrenamiento de SenseCraft AI.

Logramos probar un modelo personalizado para diferenciar un tomatodo y un celular, obteniendo una confianza de 100 % y 89 %, respectivamente, en las pruebas registradas.

También conocimos cómo ejecutar el modelo en la XIAO ESP32S3 Sense y observar los resultados de clasificación en tiempo real.

## 8. Referencias

[1] Seeed Studio, "SenseCraft AI", *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/sensecraft-ai/overview/.

[2] Seeed Studio, "Entrenamiento de modelos de clasificación de imágenes", *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/train_classification_model_online/.
