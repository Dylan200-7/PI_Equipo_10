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


