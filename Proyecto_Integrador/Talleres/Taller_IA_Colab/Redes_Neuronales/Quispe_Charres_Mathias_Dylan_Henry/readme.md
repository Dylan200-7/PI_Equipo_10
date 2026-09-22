# Redes neuronales - CNN, Keras y Perceptrón

En esta parte revisé el archivo de redes neuronales y traté de entender principalmente **qué hace cada cosa y para qué podría servirnos en el proyecto**.

No puse todo el código escrito porque se hace muy largo. Mejor coloqué capturas de las partes que me parecieron más importantes del `.py`.

---

## CNN

Una CNN es una red que sirve bastante para trabajar con imágenes.

Yo la entendí así: la red no mira la foto completa de frente como nosotros, sino que va revisando pequeñas partes y buscando patrones. Al inicio puede reconocer cosas simples como bordes o cambios de color, y luego con más capas va juntando esa información.

En el código se habla de `Conv2D`, `ReLU`, `MaxPool` y capas densas.

<p align="center">
  <img src="imagenes/01_cnn_concepto_componentes_py.png" width="850">
</p>

### Lo que entendí de cada parte

* **Conv2D:** busca patrones en la imagen.
* **ReLU:** ayuda a dejar pasar los valores que sirven.
* **MaxPool:** reduce información, pero intenta quedarse con lo más importante.
* **Dense:** al final usa lo aprendido para decidir la clase.

---

## Dataset que se usó

En el ejercicio se usa TrashNet y se trabaja con imágenes de vidrio y plástico.

<p align="center">
  <img src="imagenes/02_cnn_dataset_py.png" width="850">
</p>

Esto sirve para practicar clasificación binaria, porque solo hay dos opciones.

---

## Modelo CNN

Esta es la parte donde se construye la CNN.

<p align="center">
  <img src="imagenes/04_cnn_modelo_simplecnn_py.png" width="850">
</p>

Lo que vi es que va aumentando los filtros:

* primero 16,
* luego 32,
* después 64.

Luego pasa por una capa final que hace la clasificación.

No entendí todos los parámetros al comienzo, pero sí la idea general: **cada capa va sacando características diferentes de la imagen**.

---

## Entrenamiento

La red se entrena varias épocas y se van guardando datos como pérdida, accuracy y ROC-AUC.

<p align="center">
  <img src="imagenes/06_cnn_entrenamiento_curvas_py.png" width="850">
</p>

En el archivo se indica que desde la época 4 mejora más y llega aproximadamente a **63.27% de accuracy**.

También aparece un ROC-AUC de alrededor de **0.67 a 0.69**.

<p align="center">
  <img src="imagenes/07_cnn_resultados_py.png" width="850">
</p>

### ¿Qué significa?

Para mí significa que el modelo sí está aprendiendo, pero todavía no está clasificando de una manera demasiado buena.

O sea, ya encuentra diferencias entre vidrio y plástico, pero todavía se equivoca bastante.

---

## Grad-CAM

Esta parte me pareció una de las más interesantes porque sirve para saber **qué zona de la imagen influyó en la decisión**.

<p align="center">
  <img src="imagenes/10_cnn_gradcam_py.png" width="850">
</p>

<p align="center">
  <img src="imagenes/11_cnn_gradcam_guardado_py.png" width="850">
</p>

La idea es que las zonas más claras son las que tuvieron más importancia para la predicción.

Esto es útil porque no solo vemos el resultado, sino que también podemos revisar si el modelo está mirando la parte correcta de la imagen.

---

# Keras

Keras lo entendí más como una herramienta para crear redes neuronales de forma más sencilla.

En el ejemplo se usan reseñas de películas y se clasifican como positivas o negativas.

La red tiene dos capas con 16 neuronas y una salida con `sigmoid`.

<p align="center">
  <img src="imagenes/14_keras_modelo_entrenamiento_py.png" width="850">
</p>

Lo importante de `sigmoid` es que ayuda a obtener un valor entre 0 y 1, lo cual sirve bastante cuando solo existen dos clases.

---

## Sobreajuste

En Keras también vimos el problema del sobreajuste.

<p align="center">
  <img src="imagenes/15_keras_resultado_sobreajuste_py.png" width="850">
</p>

La forma más simple en la que lo entiendo es:

> El modelo se aprende demasiado bien los datos de entrenamiento, pero cuando le das datos nuevos puede fallar.

En el archivo aparece una exactitud de aproximadamente **86.1%** para ese ejemplo.

---

## Dropout

También se usa Dropout.

<p align="center">
  <img src="imagenes/17_keras_dropout_prediccion_py.png" width="850">
</p>

Según lo que entendí, durante el entrenamiento se desactivan algunas neuronas para que la red no dependa siempre de las mismas.

En ese mismo ejemplo sale una predicción de **99.4%** para una reseña positiva.

---

# Perceptrón

El perceptrón me pareció más fácil de entender porque es como una neurona básica.

Tiene:

* entradas,
* pesos,
* bias,
* y una función de activación.

<p align="center">
  <img src="imagenes/18_perceptron_base_py.png" width="850">
</p>

En el ejemplo se usan temperatura y vibración.

Después la red suma las entradas con sus pesos y decide si hay alerta o no.

<p align="center">
  <img src="imagenes/22_perceptron_salida_real.png" width="850">
</p>

---

## AND, OR y XOR

Con AND y OR se puede ver que un perceptrón puede separar ciertos datos usando una línea.

<p align="center">
  <img src="imagenes/24_resultado_grafico_and_or.png" width="550">
</p>

Pero con XOR una sola línea no alcanza.

<p align="center">
  <img src="imagenes/25_resultado_grafico_xor.png" width="550">
</p>

Esto ayuda a entender por qué una sola neurona no sirve para resolver cualquier problema y por qué usamos varias capas.

---

## Funciones que me parecieron más importantes

* `perceptron()`
* `step_function()`
* `tanh_activation()`
* `evaluate()`
* `train_one_epoch()`
* `grad_cam()`

También son importantes:

* `Conv2D`
* `ReLU`
* `MaxPool2D`
* `Dropout`
* `sigmoid`

---

## Qué aprendí

Lo principal que saqué de esta práctica fue esto:

* El perceptrón es como la base de una red neuronal.
* Una sola neurona tiene limitaciones.
* Keras hace más fácil crear redes.
* Las CNN son buenas para imágenes.
* No solo hay que mirar accuracy.
* El sobreajuste es algo que hay que controlar.
* Grad-CAM sirve para entender mejor qué está mirando la red.
* Los modelos se pueden guardar después de entrenarlos.

---

## Cómo lo usaríamos en Kartoffelmachine

En nuestro proyecto la idea sería cambiar el problema de clasificación del ejemplo y usarlo con las papas Chaucha.

El flujo que pensamos sería así:

1. La papa entra a la zona de inspección.
2. Los rodillos hacen que vaya rotando.
3. La cámara toma imágenes de diferentes partes de la papa.
4. La imagen se prepara para que entre a la red.
5. Una CNN analiza cosas como manchas, forma, textura o daños visibles.
6. El modelo da una clasificación:

   * **Papa buena**
   * **Papa mala**
7. Esa decisión se manda al controlador.
8. Finalmente el mecanismo manda la papa al lado que corresponde.

<p align="center">
  <img src="imagenes/26_kartoffelmachine_flujo_cnn.png" width="850">
</p>

Lo que más nos serviría del código de la práctica sería:

* la preparación de imágenes;
* la CNN;
* las funciones de entrenamiento;
* las métricas;
* el aumento de datos;
* transfer learning;
* Grad-CAM;
* y guardar el modelo después de entrenarlo.

Lo que sí tendríamos que cambiar es el dataset. En vez de usar vidrio y plástico, tendríamos que tener fotos reales de papas Chaucha separadas en buenas y malas.

También sería importante que las fotos se tomen con una iluminación lo más parecida posible a la que habrá dentro del módulo de Kartoffelmachine, porque si entrenamos con un fondo o luz totalmente diferente, luego el modelo puede fallar cuando lo pongamos en el sistema real.

---

## Conclusión

Después de revisar el código, lo que más relación tiene con nuestro proyecto son las CNN y Grad-CAM, porque Kartoffelmachine trabaja con imágenes.

El perceptrón ayuda más a entender la lógica básica de una neurona, mientras que Keras sirve para construir modelos de forma más práctica.

La parte que nos faltaría para usar esto de verdad en Kartoffelmachine sería crear nuestro propio dataset de papas buenas y malas y entrenar el modelo con imágenes tomadas en condiciones parecidas a las del sistema real.
