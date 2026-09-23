# Redes neuronales - CNN, Keras y Perceptrón

En esta práctica revisé tres temas principales: CNN, Keras y Perceptrón. La idea fue entender de manera general cómo funcionan y ver qué parte nos podría servir para Kartoffelmachine.

---

## CNN

Las CNN son redes neuronales utilizadas principalmente para trabajar con imágenes. Yo lo entendí como una red que va buscando características pequeñas de una imagen, como bordes o texturas, y poco a poco junta esa información para poder clasificarla.

<p align="center">
  <img src="./imagenes/01_cnn_componentes.png" width="850">
</p>

Las partes principales que vimos fueron Conv2D, ReLU, MaxPool y las capas densas. Cada una cumple una función diferente durante el análisis de la imagen.

### Dataset

Para practicar se utilizó TrashNet, usando imágenes de vidrio y plástico.

<p align="center">
  <img src="./imagenes/02_cnn_dataset_inicio.png" width="850">
</p>

<p align="center">
  <img src="./imagenes/03_cnn_dataset_carga.png" width="850">
</p>

Los datos se separaron en entrenamiento, validación y prueba.

También se mostraron algunos ejemplos para comprobar que las imágenes se habían cargado correctamente.

<p align="center">
  <img src="./imagenes/04_cnn_visualizar_ejemplos.png" width="850">
</p>

### Modelo CNN

Después se creó una CNN desde cero.

<p align="center">
  <img src="./imagenes/05_cnn_modelo_desde_cero.png" width="850">
</p>

El modelo comienza con 16 filtros, luego pasa a 32 y finalmente a 64. La idea es que mientras avanza por las capas pueda reconocer características cada vez más importantes.

### Entrenamiento

El modelo se entrenó durante 8 épocas.

<p align="center">
  <img src="./imagenes/06_cnn_entrenamiento.png" width="850">
</p>

Luego se graficaron los resultados para observar si realmente estaba aprendiendo.

<p align="center">
  <img src="./imagenes/07_cnn_curvas_entrenamiento.png" width="850">
</p>

A partir de la época 4 se nota una mejora y se llega aproximadamente a 63.27% de accuracy. El ROC-AUC se mantiene alrededor de 0.67 a 0.69.

Para mí esto indica que sí existe aprendizaje, aunque todavía el modelo comete varios errores.

### Evaluación

Al final se prueba el modelo con datos que no utilizó directamente durante el entrenamiento.

<p align="center">
  <img src="./imagenes/08_cnn_evaluacion_test.png" width="850">
</p>

La matriz de confusión permite ver cuántas imágenes clasificó correctamente y en cuáles se equivocó.

### Grad-CAM

Grad-CAM fue una de las partes que más me llamó la atención porque permite ver qué zona de una imagen tomó más en cuenta la red para hacer una predicción.

<p align="center">
  <img src="./imagenes/09_cnn_gradcam.png" width="850">
</p>

Esto sería útil porque no solo tenemos el resultado, sino que también podemos revisar si la IA está observando la parte correcta de la imagen.

---

## Keras

Keras permite crear y entrenar redes neuronales de una forma más sencilla.

En este ejemplo ya no se usaron imágenes, sino reseñas de películas que tenían que clasificarse como positivas o negativas.

<p align="center">
  <img src="./imagenes/10_keras_creacion_modelo.png" width="850">
</p>

Se utilizaron dos capas de 16 neuronas y una capa final para realizar la clasificación.

### Sobreajuste

También vimos el problema del sobreajuste.

<p align="center">
  <img src="./imagenes/11_keras_analisis_resultado.png" width="850">
</p>

Yo lo entendí como cuando el modelo aprende demasiado bien los datos con los que entrenó, pero después empieza a fallar cuando recibe datos nuevos.

En este ejemplo se obtuvo aproximadamente 86.1% de exactitud.

### Dropout

Para reducir el sobreajuste también se utilizó Dropout.

<p align="center">
  <img src="./imagenes/12_keras_dropout.png" width="850">
</p>

Durante el entrenamiento algunas neuronas se desactivan temporalmente para que la red no dependa siempre de las mismas.

Finalmente también se hicieron predicciones.

<p align="center">
  <img src="./imagenes/13_keras_predicciones.png" width="850">
</p>

En este caso una de las reseñas obtuvo aproximadamente 99.4% de probabilidad de ser positiva.

---

## Perceptrón

El perceptrón fue la parte más sencilla de entender porque funciona como una neurona básica.

Recibe entradas, utiliza pesos y un bias, y finalmente genera una salida.

<p align="center">
  <img src="./imagenes/14_perceptron_factores_funcionamiento.png" width="850">
</p>

En el ejemplo se utilizaron temperatura y vibración como entradas.

Después se probaron dos funciones de activación diferentes.

<p align="center">
  <img src="./imagenes/15_perceptron_resultados.png" width="850">
</p>

La función escalón devuelve 0 o 1, mientras que tanh puede devolver valores entre -1 y 1.

### AND y OR

También se probó el perceptrón con las compuertas AND y OR.

<p align="center">
  <img src="./imagenes/16_perceptron_and_or.png" width="850">
</p>

Con estos ejemplos se puede ver cómo una neurona separa datos dependiendo de sus entradas.

### XOR

Finalmente se probó XOR.

<p align="center">
  <img src="./imagenes/17_perceptron_xor_inicio.png" width="850">
</p>

<p align="center">
  <img src="./imagenes/18_perceptron_xor_grafico.png" width="700">
</p>

<p align="center">
  <img src="./imagenes/19_perceptron_xor_conclusion.png" width="700">
</p>

La conclusión principal fue que un solo perceptrón no puede resolver XOR. Se necesitan más neuronas y una capa de salida.

Esto ayuda a entender por qué las redes neuronales reales utilizan varias neuronas y varias capas.

---

## Qué aprendí

De esta práctica me quedo principalmente con lo siguiente:

- El perceptrón ayuda a entender cómo funciona una neurona artificial.
- Keras facilita la creación de redes neuronales.
- Las CNN son muy útiles cuando trabajamos con imágenes.
- No siempre basta con revisar el accuracy.
- El sobreajuste puede hacer que un modelo funcione bien entrenando, pero mal con datos nuevos.
- Grad-CAM permite entender mejor qué está observando una CNN.

---

## Aplicación en Kartoffelmachine

De todo lo visto, la CNN es lo que más relación tiene con nuestro proyecto.

La idea sería reemplazar las imágenes de vidrio y plástico por imágenes reales de papas Chaucha.

El funcionamiento sería:

1. La papa entra a la zona de inspección.
2. Los rodillos hacen que la papa rote.
3. La cámara toma imágenes mientras gira.
4. Las imágenes se preparan para ingresar al modelo.
5. La CNN analiza características como manchas, forma, textura o daños.
6. Se determina si la papa es buena o mala.
7. La Raspberry Pi recibe y procesa la decisión.
8. El mecanismo dirige la papa al contenedor correspondiente.

<p align="center">
  <img src="./imagenes/20_kartoffelmachine_flujo_cnn.png" width="850">
</p>

Para aplicarlo realmente tendríamos que crear nuestro propio dataset con fotos de papas buenas y malas.

También sería importante tomar las imágenes con una iluminación parecida a la que tendrá el módulo real, para que el modelo no tenga problemas cuando se implemente en Kartoffelmachine.

---

## Conclusión

Esta práctica me ayudó a entender mejor cómo una red neuronal puede aprender a partir de datos.

Para Kartoffelmachine lo más útil sería trabajar con una CNN, porque nuestro sistema necesita analizar imágenes de las papas para poder clasificarlas.

Más adelante tendríamos que tomar nuestras propias fotos, entrenar el modelo y probar qué tan bien logra diferenciar una papa buena de una mala.
