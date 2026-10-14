
# Detección de género con SenseCraft AI

**Universidad:** Universidad Peruana Cayetano Heredia (UPCH)  
**Fecha:** 13/10/2026  
**Plataforma:** SenseCraft AI  
**Dispositivo:** XIAO ESP32S3 Sense

## 1. Introducción

En esta práctica trabajé con SenseCraft AI para probar un modelo de inteligencia artificial que ya estaba entrenado. Elegí el modelo llamado **Detección de género**, el cual reconoce rostros y muestra las etiquetas `male` y `female` según las características que identifica en la imagen.

Para realizar las pruebas utilicé la placa XIAO ESP32S3 Sense con su cámara. También configuré una salida GPIO para que un LED pueda activarse cuando se cumpla una condición.

## 2. Materiales utilizados

- XIAO ESP32S3 Sense.
- Cámara del dispositivo.
- Laptop con conexión a Internet.
- Cable USB.
- Navegador Google Chrome.
- Plataforma SenseCraft AI.

## 3. Procedimiento

### 3.1. Búsqueda del modelo

Primero ingresé a la plataforma [SenseCraft AI](https://sensecraft.seeed.cc/ai/) y entré a la sección **Modelos**, donde encontré la biblioteca de modelos disponibles.

Revisé las opciones de detección y clasificación para conocer los modelos que se podían utilizar.

![Biblioteca de modelos](imagenes/01_biblioteca_general.png)

*Figura 1. Biblioteca de modelos de SenseCraft AI.*

Después seleccioné el filtro **XIAO ESP32S3 Sense** para visualizar los modelos compatibles con el dispositivo que estábamos utilizando.

![Modelos compatibles](imagenes/02_biblioteca_xiao.png)

*Figura 2. Modelos compatibles con XIAO ESP32S3 Sense.*

### 3.2. Selección del modelo

Entre los modelos disponibles seleccioné **Detección de género**.

Según la descripción de SenseCraft AI, este modelo utiliza Swift-YOLO y permite identificar rostros, mostrando las etiquetas `male` y `female` con un porcentaje de confianza.

En esta actividad no fue necesario entrenar un modelo nuevo, ya que utilizamos uno previamente entrenado.

![Modelo seleccionado](imagenes/03_ficha_modelo_genero.png)

*Figura 3. Modelo de detección de género seleccionado.*

### 3.3. Conexión del dispositivo

Luego ingresé a **Espacio de trabajo**, seleccioné XIAO ESP32S3 Sense e intenté conectar la placa mediante el cable USB.

Durante uno de los intentos apareció el mensaje **"No se encontraron dispositivos compatibles"**, por lo que no se podía acceder a las funciones del dispositivo.

![Error de conexión](imagenes/04_conexion_sin_dispositivo.png)

*Figura 4. Problema al intentar conectar el dispositivo.*

Posteriormente conseguimos establecer la conexión y continuar con las pruebas del modelo.

### 3.4. Prueba de detección MALE

Con el dispositivo conectado inicié la vista previa y coloqué a una persona frente a la cámara.

El modelo identificó el rostro mediante un recuadro rojo y mostró la siguiente predicción:

- **Etiqueta:** male
- **Confianza:** 91 %

También pude observar los datos que se iban generando en el registro del dispositivo.

![Detección male](imagenes/05_resultado_male.png)

*Figura 5. Resultado de la detección con la etiqueta male.*

### 3.5. Prueba de detección FEMALE

Después repetimos la prueba colocando a otra persona frente a la cámara.

En este caso, el modelo mostró un recuadro verde sobre el rostro y la etiqueta `female`.

El resultado observado fue:

- **Etiqueta:** female
- **Confianza:** 86 %

![Detección female](imagenes/06_resultado_female_adicional.png)

*Figura 6. Primera prueba de detección female.*

Realizamos otra captura cambiando un poco la posición de la persona frente a la cámara.

![Segunda detección female](imagenes/07_resultado_female.png)

*Figura 7. Segunda prueba de detección female.*

En ambas capturas el modelo consiguió mostrar la etiqueta correspondiente a la clase evaluada.

### 3.6. Configuración de GPIO

Después de realizar las pruebas ingresé a **Salida → GPIO** para configurar una acción relacionada con el modelo.

La condición establecida fue que el LED se active cuando el modelo detecte la etiqueta `male` con una confianza mayor a 54.

La configuración fue la siguiente:

| Parámetro | Valor |
|---|---|
| Objeto | male |
| GPIO | LED |
| Condición | Mayor que |
| Confianza | 54 |
| Estado inicial | LED apagado |
| Estado activo | LED encendido |

![Configuración GPIO](imagenes/08_configuracion_gpio_male.png)

*Figura 8. Configuración de la acción GPIO para la clase male.*

Esta parte permitió conocer cómo se puede relacionar una predicción de inteligencia artificial con una salida del dispositivo. La captura muestra la configuración de la regla, aunque no registra el encendido físico del LED.

### 3.7. Prueba realizada en el laboratorio

También registramos una fotografía del trabajo realizado en el laboratorio, donde se observa la laptop con SenseCraft AI y el dispositivo utilizado para las pruebas.

![Prueba en laboratorio](imagenes/09_montaje_fisico.png)

*Figura 9. Prueba del modelo durante la práctica.*

## 4. Resultados

| Prueba | Resultado | Confianza |
|---|---|---|
| Detección male | male | 91 % |
| Detección female | female | 86 % |
| Configuración GPIO | LED asociado a male | Mayor a 54 |

Los resultados mostraron que el modelo podía detectar rostros y asignar una de las dos etiquetas en tiempo real.

Los porcentajes corresponden a las predicciones mostradas durante las pruebas y no a la precisión general del modelo.

Cabe mencionar que las etiquetas son estimaciones visuales del modelo y no determinan la identidad de género de una persona.

## 5. Dificultades encontradas

Una de las dificultades fue la conexión inicial de la XIAO ESP32S3 Sense, ya que el navegador no detectaba ningún dispositivo compatible.

También observamos que el resultado dependía de la imagen que recibía la cámara, por lo que era importante colocar correctamente a la persona dentro del encuadre.

## 6. Conclusiones

En esta práctica aprendí a utilizar un modelo preentrenado desde SenseCraft AI y a ejecutarlo con la XIAO ESP32S3 Sense.

Pude observar las predicciones `male` y `female` en tiempo real y conocer cómo se muestran los niveles de confianza en la plataforma.

Además, aprendí a configurar una condición GPIO para relacionar los resultados del modelo con una salida LED.

## 7. Referencias

[1] Seeed Studio, "SenseCraft AI", *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/sensecraft-ai/overview/.

[2] Seeed Studio, "Configuración de salida GPIO en SenseCraft AI para XIAO ESP32S3 Sense", *Seeed Studio Wiki*. [En línea]. Disponible: https://wiki.seeedstudio.com/es/sensecraft_ai_output_gpio_xiao/.
