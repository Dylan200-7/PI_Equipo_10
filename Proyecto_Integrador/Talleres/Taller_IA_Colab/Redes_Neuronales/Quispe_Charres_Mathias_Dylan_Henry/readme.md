# Redes neuronales - CNN, Keras y Perceptrón

En esta parte revisé el archivo de redes neuronales y traté de entender principalmente **qué hace cada cosa y para qué podría servirnos en el proyecto**.

No puse todo el código escrito porque se hace muy largo. Mejor coloqué capturas de las partes que me parecieron más importantes del `.py`.

---

## CNN

Una CNN es una red que sirve bastante para trabajar con imágenes.

Yo la entendí así: la red no mira la foto completa de frente como nosotros, sino que va revisando pequeñas partes y buscando patrones. Al inicio puede reconocer cosas simples como bordes o cambios de color, y luego con más capas va juntando esa información.

En el código se habla de `Conv2D`, `ReLU`, `MaxPool` y capas densas.

<p align="center">
  <img src="./imagenes/01_cnn_componentes.png" width="850">
</p>

### Lo que entendí de cada parte

- **Conv2D:** busca patrones en la imagen.
- **ReLU:** ayuda a dejar pasar los valores que sirven.
- **MaxPool:** reduce información, pero intenta quedarse con lo más importante.
- **Dense:** al final usa lo aprendido para decidir la clase.

---

## Dataset que se usó

En el ejercicio se usa TrashNet y se trabaja con imágenes de vidrio y plástico.

Primero se carga el dataset y se definen las clases que se van a utilizar.

<p align="center">
  <img src="./imagenes/02_cnn_dataset_inicio.png" width="850">
</p>

Después se descarga el dataset y se preparan las partes de entrenamiento, validación y prueba.

<p align="center">
  <img src="./imagenes/03_cnn_dataset_carga.png" width="850">
</p>

Esto sirve para practicar clasificación binaria, porque solo hay dos opciones:

- Vidrio.
- Plástico.

---

## Visualización de ejemplos

Antes de entrenar la red también podemos visualizar algunas imágenes del dataset.

Esto nos sirve para comprobar que las imágenes se están cargando correctamente y ver cómo son las dos clases con las que estamos trabajando.

<p align="center">
  <img src="./imagenes/04_cnn_visualizar_ejemplos.png" width="850">
</p>

---

## Modelo CNN

Esta es la parte donde se construye la CNN.

<p align="center">
  <img src="./imagenes/05_cnn_modelo_desde_cero.png" width="850">
</p>

Lo que vi es que va aumentando la cantidad de filtros:

- primero 16,
- luego 32,
- después 64.

También utiliza `ReLU` y `MaxPool`.

Luego pasa por una capa final que hace la clasificación.

No entendí todos los parámetros al comienzo, pero sí la idea general: **cada capa va sacando características diferentes de la imagen**.

---

## Entrenamiento

Después de crear la CNN se empieza a entrenar el modelo.

En esta parte se utilizan 8 épocas y en cada una se calcula la pérdida, accuracy y ROC-AUC.

<p align="center">
  <img src="./imagenes/06_cnn_entrenamiento.png" width="850">
</p>

Podemos ver que en cada época los valores van cambiando conforme la red aprende de las imágenes.

---

## Curvas de entrenamiento

Para entender mejor cómo está aprendiendo el modelo se muestran las curvas de entrenamiento.

<p align="center">
  <img src="./imagenes/07_cnn_curvas_entrenamiento.png" width="850">
</p>

En el archivo se indica que desde la época 4 comienza a mejorar la clasificación y llega aproximadamente a **63.27% de accuracy**.

También aparece un ROC-AUC de alrededor de **0.67 a 0.69**.

### ¿Qué significa?

Para mí significa que el modelo sí está aprendiendo, pero todavía no está clasificando de una manera demasiado buena.

O sea, ya encuentra diferencias entre vidrio y plástico, pero todavía se equivoca bastante.

---

## Evaluación final

Después del entrenamiento se prueba el modelo con imágenes que no utilizó directamente para aprender.

Aquí podemos ver el accuracy final, ROC-AUC y la matriz de confusión.

<p align="center">
  <img src="./imagenes/08_cnn_evaluacion_test.png" width="850">
</p>

La matriz de confusión ayuda a ver de una forma más clara cuántas imágenes fueron clasificadas correctamente y en cuáles se equivocó.

---

## Grad-CAM

Esta parte me pareció una de las más interesantes porque sirve para saber **qué zona de la imagen influyó en la decisión de la red**.

<p align="center">
  <img src="./imagenes/09_cnn_gradcam.png" width="850">
</p>

En la imagen podemos observar tres partes:

- La imagen original.
- El mapa de Grad-CAM.
- La superposición del mapa sobre la imagen.

La idea es que las zonas más claras tienen mayor importancia para la predicción.

Esto es útil porque no solo vemos el resultado, sino que también podemos revisar si el modelo está mirando la parte correcta de la imagen.

---

# Keras

Keras lo entendí más como una herramienta para crear redes neuronales de forma más sencilla.

En el ejemplo se usan reseñas de películas y se clasifican como positivas o negativas.

---

## Creación del modelo

La red tiene dos capas con 16 neuronas y una salida con `sigmoid`.

<p align="center">
  <img src="./imagenes/10_keras_creacion_modelo.png" width="850">
</p>

También se utiliza:

- `rmsprop` como optimizador.
- `binary_crossentropy` para calcular el error.
- `accuracy` como una de las métricas.

Lo importante de `sigmoid` es que ayuda a obtener un valor entre 0 y 1, lo cual sirve bastante cuando solo existen dos clases.

---

## Análisis del resultado

En Keras también vimos el problema del sobreajuste.

<p align="center">
  <img src="./imagenes/11_keras_analisis_resultado.png" width="850">
</p>

En el gráfico podemos ver dos curvas:

- La curva de entrenamiento.
- La curva de validación.

La forma más simple en la que entiendo el sobreajuste es:

> El modelo aprende demasiado bien los datos de entrenamiento, pero cuando le das datos nuevos puede empezar a fallar.

En el archivo aparece una exactitud de aproximadamente **86.1%** para este ejemplo.

---

## Dropout

También se utiliza Dropout para intentar reducir el sobreajuste.

<p align="center">
  <img src="./imagenes/12_keras_dropout.png" width="850">
</p>

Según lo que entendí, durante el entrenamiento se desactivan algunas neuronas de manera aleatoria.

Esto hace que la red no dependa siempre de las mismas neuronas y tenga que aprender usando diferentes combinaciones.

---

## Predicciones

Después de entrenar el modelo se puede utilizar para realizar predicciones.

<p align="center">
  <img src="./imagenes/13_keras_predicciones.png" width="850">
</p>

En este caso se hizo una predicción sobre una reseña y se obtuvo aproximadamente un **99.4% de probabilidad de que sea positiva**.

---

# Perceptrón

El perceptrón me pareció más fácil de entender porque es como una neurona básica.

Tiene:

- entradas,
- pesos,
- bias,
- una función de activación.

---

## Factores y funcionamiento

En el ejemplo se utilizan como entradas:

- temperatura,
- vibración.

También se definen pesos y un bias.

<p align="center">
  <img src="./imagenes/14_perceptron_factores_funcionamiento.png" width="850">
</p>

Después el perceptrón realiza una suma utilizando las entradas y sus pesos.

Finalmente aplica una función de activación para generar una salida.

---

## Resultados del perceptrón

En el código se prueban dos funciones de activación:

- función escalón,
- función `tanh`.

<p align="center">
  <img src="./imagenes/15_perceptron_resultados.png" width="850">
</p>

La función escalón devuelve solamente 0 o 1.

En cambio, `tanh` puede devolver valores entre -1 y 1.

La función de activación es importante porque transforma la suma que realiza la neurona en una salida que puede utilizar para tomar una decisión.

---

## Perceptrón AND y OR

También se probó el perceptrón utilizando compuertas lógicas.

<p align="center">
  <img src="./imagenes/16_perceptron_and_or.png" width="850">
</p>

En AND el resultado es 1 solamente cuando las dos entradas son 1.

En OR el resultado es 1 cuando al menos una de las entradas es 1.

Estos ejemplos permiten entender de una forma sencilla cómo una neurona puede separar diferentes datos.

---

## Compuerta XOR

Finalmente se probó XOR.

Primero se construye el gráfico con los diferentes puntos y fronteras de decisión.

<p align="center">
  <img src="./imagenes/17_perceptron_xor_inicio.png" width="850">
</p>

Después podemos observar gráficamente cómo se intenta separar los datos.

<p align="center">
  <img src="./imagenes/18_perceptron_xor_grafico.png" width="700">
</p>

La conclusión de esta parte es importante.

<p align="center">
  <img src="./imagenes/19_perceptron_xor_conclusion.png" width="700">
</p>

La idea principal es:

- **1 perceptrón no puede resolver XOR.**
- **2 perceptrones y una capa de salida sí pueden hacerlo.**

Esto ayuda a entender por qué una sola neurona no sirve para resolver cualquier problema y por qué las redes neuronales utilizan varias neuronas y capas.

---

## Funciones que me parecieron más importantes

### CNN

- `Conv2D`
- `ReLU`
- `MaxPool2D`
- `evaluate()`
- `train_one_epoch()`
- `grad_cam()`

### Keras

- `Sequential`
- `Dense`
- `sigmoid`
- `Dropout`
- `model.fit()`
- `model.predict()`

### Perceptrón

- `perceptron()`
- `step_function()`
- `tanh_activation()`

---

## Qué aprendí

Lo principal que saqué de esta práctica fue esto:

- El perceptrón es como la base de una red neuronal.
- Una sola neurona tiene limitaciones.
- Keras hace más fácil crear redes neuronales.
- Las CNN son buenas para trabajar con imágenes.
- No solo hay que mirar el accuracy.
- La matriz de confusión también ayuda a encontrar errores.
- El sobreajuste es algo que se debe controlar.
- Dropout ayuda a reducir el sobreajuste.
- Grad-CAM sirve para entender mejor qué está mirando una CNN.
- Los modelos se pueden guardar después de entrenarlos.

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
   - **Papa buena**
   - **Papa mala**
7. Esa decisión se manda al controlador.
8. Finalmente el mecanismo manda la papa al lado que corresponde.

<p align="center">
  <img src="./imagenes/20_kartoffelmachine_flujo_cnn.png" width="850">
</p>

Lo que más nos serviría del código de la práctica sería:

- la preparación de imágenes;
- la CNN;
- las funciones de entrenamiento;
- las métricas;
- el aumento de datos;
- Transfer Learning;
- Grad-CAM;
- guardar el modelo después de entrenarlo.

Lo que sí tendríamos que cambiar es el dataset.

En vez de usar vidrio y plástico, tendríamos que tener fotos reales de papas Chaucha separadas en buenas y malas.

También sería importante que las fotos se tomen con una iluminación lo más parecida posible a la que habrá dentro del módulo de Kartoffelmachine.

Esto es importante porque si entrenamos el modelo con un fondo o iluminación totalmente diferente, puede fallar cuando lo pongamos en el sistema real.

---

## Conclusión

Después de revisar el código, lo que más relación tiene con nuestro proyecto son las **CNN y Grad-CAM**, porque Kartoffelmachine trabaja directamente con imágenes.

El perceptrón ayuda más a entender la lógica básica de una neurona, mientras que Keras sirve para construir modelos de una forma más práctica.

La parte que nos faltaría para usar esto realmente en Kartoffelmachine sería crear nuestro propio dataset de papas buenas y malas y entrenar el modelo utilizando imágenes tomadas en condiciones parecidas a las del sistema real.