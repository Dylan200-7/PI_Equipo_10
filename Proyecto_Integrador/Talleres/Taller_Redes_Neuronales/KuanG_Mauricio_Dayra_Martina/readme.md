# Práctica de redes neuronales
En el presente informé se explicarán los tres tipos de redes neuronales
1. CNN
2. Keras
3. Perceptrón

# Data Set

El data Set que se utilizó en esta ocasión. Contiene un conjunto de imágenes de vidrios y plásticos,
para la clasificación automática de residuos.
- Entrada: imágenes 2D de vidrio y plástico a escala de grises.

- Etiquetas: clasificación binaria.
  - (0) Vidrio
  - (1) Plástico
  
- Particiones: Las imágenes se dividen en conjuntos de train, validation y test mediante trash_dataset.py
  - 70 % entrenamiento
  - 15 % validación
  - 15 % prueba.

  Este archivo mantiene la compatibilidad con la CNN

# 1. CNN
CNN stands for Convolutional Neural Network. Esta es un tipo de red neuronal diseñada para trabajr con imágenes.
A continuación, se explicará su funcionamiento mediante el código brindado en clase

La idea general era que el modelo CNN, pueda clasificar correctamente la imagen del Data Set
Si es 0 o 1, es decir, si es vidrio o plástico.
La CNN aprende progresivamente:

píxeles
   ↓
bordes
   ↓
formas
   ↓
texturas
   ↓
patrones más complejos
   ↓
glass / plastic

1.1 Preparación del entorno

Para construir y entrenar la red neuronal, se importó la biblioteca "Pytorch"

1.2 Cargar el data set utilizando trashNet

TrashNet se utilizó para almacenar el conjunto de imágenes del Data Set
<p align="center">
  <img src="imagenes/CNN1.png" width="850">
</p>

1.3 Transformación inicial

Cómo ya se importó la librería PyTorch, se realizó las transformaciones que se necesitanban
para una mejor funcionalidad del modelo CNN

Con "transform_basic = T.Compose([
    T.ToTensor()
])"
Se permitió darle el formato PyTorch a la imagen que se suba.
"T.ToTensor" transforma toma la imagen y la convierte en un tensor de PyTorch

Luego se crearon los conjuntos de entrenamiento, prueba y validación

<p align="center">
  <img src="imagenes/CNN2.png" width="850">
</p>

1.4 Visualización de Ejemplos de imágenes

Se mostró algunos ejemplos de vidrio y plástico para revisar si los datos realmente se están leyendo bien antes de entrenar.

<p align="center">
  <img src="imagenes/Kera3.png" width="850">
</p>

1.4 Creación del modelo CNN
Se construyó una CNN sencilla desde cero para clasificar las imágenes de TrashNet.
La red está formada por tres capas convolucionales que extraen características de las imágenes:
1. nn.Conv2d(1, 16, ...) : Indica 1 canal de entrada y 16 de salida (capta 16 características)
2. nn.Conv2d(16, 32, ...)
3. nn.Conv2d(32, 64, ...)
Cada capa convolucional esta acompañada del filtro "Kernel" el cual aprende patrones para deterctar determinadas caracterísicas.
También, estan seguidas de ReLU y MaxPool para introducir no linealidad y reducir el tamaño espacial.

Después se evalúa el modelo con el conjunto de validación y se obtienen la accuracy (val_acc) y el AUC (val_auc)

<p align="center">
  <img src="imagenes/05_cnn_funciones_entrenamiento_py.png" width="850">
</p>

1.5 Entrenamiento del Modelo

En esta etapa se entrena la CNN. Se definió la función de perdida "CrossEntropyLoss", la cual mide qué tan diferentes son las 
predicciones del modelo e utiliza el optimizador Adam para actualizar los parámetros de la red, con una tasa de aprendizaje de 0.001. 
El modelo se entrenó durante 8 épocas y, en cada una, se calcula el "train_loss" utilizando las imágenes de entrenamiento. 

<p align="center">
  <img src="imagenes/05_cnn_funciones_entrenamiento_py.png" width="850">
</p>

Luego se graficó para ver si el modelo estaba aprendiendo

<p align="center">
  <img src="imagenes/05_cnn_funciones_entrenamiento_py.png" width="850">
</p>

A partir de la época 4 se tiene un mejor porcentaje de accuracy - 63.27%
Por lo que, puedo decir que si hay evidencia de aprendizaje moderado

1.5 Evaluación Final en Test

Finalmente, se pruebó el modelo con datos que no utilizó directamente durante el entrenamiento.
<p align="center">
  <img src="imagenes/05_cnn_funciones_entrenamiento_py.png" width="850">
</p>

1.6 Grad Cam

Una parte resaltante del código, ya que permitió ver en que parte de la imagen se fijó más 
el modelo CNN red para hacer la predicción, y por ende si evaluaba las zonas de mayor importancia.
- zonas claras/amarillas = más influencia
- zonas oscuras/moradas = menor influencia

---

# 2. Keras

En Keras se trabajó con reseñas de películas
Del mismo modo, sigue siendo clasificación binaria:
* negativa,
* positiva.

2.1 Transformación inicial

Se convirtieron las palabras a una representación numérica. Así como con ToTensor.(),
la función vectorizar() transformó las reseñas, representadas mediante índices de palabras, en vectores binarios de 10 000 posiciones

De esta manera, x_train y x_test contienen las reseñas convertidas a una representación numérica que puede recibir el modelo.

<p align="center">
  <img src="imagenes/Kera1.png" width="850">
</p>

2.2 Creación de Keras

Primero se creó una arquitectura Sequential formada por dos capas
1. model.add(layers.Dense(16, activation='relu', input_shape=(10000,)))
2. model.add(layers.Dense(16, activation='relu'))
En esta red enuronal cada neurona de la capa está conectada con las de la siguiente
Además, cada una de las 16 neuronas con activación ReLU, para la no linealidad.
Y una capa final de una neurona con activación Sigmoid: transforma el resultado a un valor entre [0.1]
para la clasificación binaria

<p align="center">
  <img src="imagenes/Kera2.png" width="850">
</p>

2.3 Entrenamiento

El entrenamiento, a comparación, resulta mucho mas sencillo 
fit() entrena la red:
- epochs=20: el modelo recorrere el conjunto de entrenamiento 20 veces.
- batch_size=512: el modelo procesa 512 ejemplos por vez antes de actualizar los parámetro

<p align="center">
  <img src="imagenes/Kera3.png" width="850">
</p>

1.4 Tabla de Análisis de Resultado

La tabla en un inicio muestra a ambas labels estan en bajada, entonces indica que 
el modelo esta aprendiendo, disminuyendo su error.
No obstante, la curva de validación empieza a subir a partir de la mitad,
El modelo no trabaja bien los datos nuevos
Unicamente funciona bien con los datos de entrenamiento 

<p align="center">
  <img src="imagenes/Kera4.png" width="850">
</p>

1.5 Dropout

Para reducir el sobreajuste, durante el entrenamiento se desactivan aleatoriamente 
el 50% de las neuronas Ello obliga a la red a aprender de diferentes combinaciones de neuronas

<p align="center">
  <img src="imagenes/Kera5.png" width="850">
</p>

<p align="center">
  <img src="imagenes/Kera6.png" width="850">
</p>

---

# 3. Perceptrón

El perceptrón es una neurona sencilla.

Primero recibe valores, después cada valor tiene un peso, se suma todo junto con el bias y finalmente se aplica una función.

En la práctica se usa primero con temperatura y vibración, pero después se prueba con compuertas lógicas.

## AND y OR

<p align="center">
  <img src="imagenes/19_perceptron_resultados_and_or_py.png" width="850">
</p>

La salida usando los mismos valores del código queda así:

<p align="center">
  <img src="imagenes/23_perceptron_salida_and_or.png" width="850">
</p>

Luego se dibujan las fronteras de decisión.

<p align="center">
  <img src="imagenes/20_perceptron_grafico_and_or_py.png" width="850">
</p>

AND y OR sí pueden resolverse con una separación lineal.

---

## XOR

Con XOR cambia la situación.

<p align="center">
  <img src="imagenes/21_perceptron_xor_py.png" width="850">
</p>

Para XOR una sola neurona no alcanza.

Por eso en el código se concluye que:

* 1 perceptrón no puede resolver XOR.
* con más de una neurona y una capa de salida sí se puede.

Esto ayuda bastante para entender por qué las redes neuronales necesitan varias neuronas.

---

# Cosas importantes del código

Para mí las cosas principales que se deben recordar son:

### De CNN

* Conv2D
* ReLU
* MaxPool
* Adam
* evaluate()
* train_one_epoch()
* Grad-CAM

### De Keras

* Sequential
* Dense
* sigmoid
* binary_crossentropy
* regularización
* Dropout

### Del perceptrón

* pesos
* bias
* suma ponderada
* función escalón
* tanh

## Aplicación al proyecto: Kartoffelmaschine

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

# Conclusión

De los tres temas, el que más serviría directamente para Kartoffelmachine sería la CNN.
Keras también nos puede ayudar si queremos construir el modelo más rápido, mientras que el perceptrón sirve principalmente para entender cómo funciona una neurona.
Antes de implementar algo real todavía tendríamos que recolectar imágenes de papas Chaucha, etiquetarlas y probar si la red realmente puede diferenciar papas buenas y malas.
