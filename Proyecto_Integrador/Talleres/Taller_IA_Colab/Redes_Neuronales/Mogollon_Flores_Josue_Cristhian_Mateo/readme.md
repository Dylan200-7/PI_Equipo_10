# Informe de redes neuronales: de la clasificación de imágenes al perceptrón

## Introducción

Esta práctica tuvo como objetivo entender, de forma progresiva, cómo distintos modelos de aprendizaje automático "aprenden" a partir de ejemplos. En el notebook se recorrieron cuatro bloques: una **red neuronal convolucional (CNN)** construida con **PyTorch**, un modelo de **clasificación binaria con Keras**, y finalmente el funcionamiento de un **perceptrón** simple. En cada bloque se compararon distintas estrategias de entrenamiento para identificar qué factores ayudan a que un modelo generalice mejor y cuáles pueden hacer que se estanque o se sobreajuste.

A continuación se describe lo trabajado en cada sección, incluyendo los resultados numéricos obtenidos, y al final se incorpora un apartado donde se traslada lo aprendido hacia un proyecto propio: un sistema de clasificación de papas mediante visión artificial.

## 1. El dataset de trabajo

Para la parte de imágenes se usó **TrashNet**, un conjunto de fotografías de residuos. El ejercicio se limitó a dos categorías: **vidrio (`glass = 0`) y plástico (`plastic = 1`)**, con lo cual la tarea quedó definida como una **clasificación binaria**.

![01_ejemplos_vidrio_plastico.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/01_ejemplos_vidrio_plastico.png)

Las imágenes se repartieron en tres subconjuntos, cada uno con una función distinta:

- **Entrenamiento:** con estos ejemplos el modelo ajusta sus parámetros.
- **Validación:** se usan durante el entrenamiento para monitorear si el modelo mejora o empieza a estancarse.
- **Prueba:** se reservan y solo se usan al final, para medir el resultado real.

El reparto obtenido fue de **687 imágenes de entrenamiento, 147 de validación y 149 de prueba**. Mantener estos grupos separados permitió comprobar si las mejoras observadas durante el entrenamiento realmente se traducían en una mejor clasificación con datos nunca vistos.

## 2. Red neuronal convolucional (CNN)

Una **CNN** procesa la imagen por partes, buscando patrones locales (bordes, texturas, formas) que luego se combinan para tomar una decisión. La arquitectura definida en el notebook fue la siguiente:

```python
self.features = nn.Sequential(
    nn.Conv2d(1, 16, kernel_size=3, padding=1),
    nn.ReLU(),
    nn.MaxPool2d(2),

    nn.Conv2d(16, 32, kernel_size=3, padding=1),
    nn.ReLU(),
    nn.MaxPool2d(2),

    nn.Conv2d(32, 64, kernel_size=3, padding=1),
    nn.ReLU(),
    nn.AdaptiveAvgPool2d((1, 1))
)
self.classifier = nn.Sequential(
    nn.Flatten(),
    nn.Linear(64, num_classes)
)
```

Descripción rápida de cada capa:

- **`Conv2d`**: extrae características locales de la imagen mediante filtros.
- **`ReLU`**: introduce no linealidad, permitiendo aprender relaciones más complejas.
- **`MaxPool2d`**: reduce el tamaño de los mapas de características, quedándose con la información más relevante.
- **`Linear`**: combina todo lo extraído para producir la predicción final.

El `1` inicial indica que las imágenes se procesaron en escala de grises, mientras que `16`, `32` y `64` son la cantidad de filtros (patrones) que cada bloque aprende a detectar.

### 2.1. Entrenamiento desde cero

El primer modelo (`model_scratch`) se entrenó sin ningún conocimiento previo, durante 8 épocas:

```python
criterion = nn.CrossEntropyLoss()
optimizer = torch.optim.Adam(model_scratch.parameters(), lr=1e-3)

epochs = 8
for epoch in range(1, epochs + 1):
    train_loss = train_one_epoch(model_scratch, train_loader, optimizer, criterion)
    val_acc, val_auc, _, _, _ = evaluate(model_scratch, val_loader)
```

![02_cnn_curvas_entrenamiento.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/02_cnn_curvas_entrenamiento.png)

Durante el entrenamiento, la exactitud en validación fue subiendo de forma irregular, alcanzando un máximo cercano al **63,27 %** hacia la cuarta época, mientras que el ROC-AUC se mantuvo entre **0,63 y 0,69**. La pérdida de entrenamiento bajó de forma lenta pero constante, lo que indica que el modelo sí estaba aprendiendo, aunque con dificultad para separar bien ambas clases.

En la evaluación final sobre el conjunto de prueba, el modelo obtuvo:

- **Exactitud (accuracy):** 55,03 %
- **ROC-AUC:** 63,23 %

![03_cnn_matriz_confusion_scratch.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/03_cnn_matriz_confusion_scratch.png)

La matriz de confusión mostró 46 aciertos y 30 errores para la clase vidrio, y 36 aciertos y 37 errores para plástico, lo que confirma que el modelo todavía confundía bastante ambas categorías.

## 3. Data augmentation

Para intentar mejorar la generalización se aplicó **data augmentation**, generando pequeñas variaciones de las imágenes de entrenamiento:

```python
transform_aug = T.Compose([
    T.RandomRotation(degrees=10),
    T.RandomAffine(degrees=0, translate=(0.05, 0.05)),
    T.ToTensor()
])
```

- **`RandomRotation`**: rota levemente la imagen.
- **`RandomAffine`**: la desplaza un poco en el plano.
- **`ToTensor`**: la convierte al formato numérico que espera el modelo.

![04_comparacion_augmentation.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/04_comparacion_augmentation.png)

Con este cambio, la exactitud en prueba subió de **55,03 % a 61,07 %**, y el ROC-AUC pasó de **63,23 % a 65,92 %**. La mejora fue clara, aunque no muy grande: augmentar los datos ayuda a que el modelo no dependa de una única orientación o posición del objeto, pero no reemplaza la necesidad de más datos o de un modelo más robusto.

## 4. Transfer learning

Para aprovechar el conocimiento de un modelo ya entrenado con millones de imágenes, se utilizó **ResNet18** preentrenada:

```python
resnet = models.resnet18(weights=models.ResNet18_Weights.DEFAULT)
in_features = resnet.fc.in_features
resnet.fc = nn.Linear(in_features, num_classes)
resnet = resnet.to(device)
```

En una primera etapa se congelaron todos los parámetros excepto la última capa, para que el modelo solo tuviera que aprender a mapear sus características ya aprendidas a nuestras dos clases:

```python
for name, param in resnet.named_parameters():
    param.requires_grad = False

for param in resnet.fc.parameters():
    param.requires_grad = True
```

![05_transfer_learning_stage1.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/05_transfer_learning_stage1.png)

Ya en esta primera etapa, la exactitud en validación subió de manera notoria, llegando a valores cercanos al **70-73 %**, con un ROC-AUC que superó el **0,87**, muy por encima de lo logrado por la CNN entrenada desde cero.

## 5. Fine-tuning

Después se permitió que una parte adicional de la red (`layer4`) también se ajustara, junto con la capa de salida, usando una tasa de aprendizaje más pequeña para no perder el conocimiento previo:

```python
for name, param in resnet.named_parameters():
    if name.startswith("layer4") or name.startswith("fc"):
        param.requires_grad = True

trainable_params = [p for p in resnet.parameters() if p.requires_grad]
optimizer = torch.optim.Adam(trainable_params, lr=1e-4)
```

![06_transfer_learning_stage2.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/06_transfer_learning_stage2.png)

En esta etapa el aprendizaje mejoró de forma notable: la exactitud en validación llegó a **87,05 %** y el ROC-AUC a **95,28 %**.

![07_transfer_learning_matriz_confusion.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/07_transfer_learning_matriz_confusion.png)

En la evaluación final sobre el conjunto de prueba, el modelo con transfer learning y fine-tuning alcanzó:

- **Exactitud (accuracy):** 89,26 %
- **ROC-AUC:** 95,55 %

La matriz de confusión mostró 70 aciertos y solo 6 errores para vidrio, y 63 aciertos con 10 errores para plástico, una diferencia enorme respecto a la CNN entrenada desde cero.

### 5.1. Comparación general de resultados

| Estrategia | Exactitud en prueba | ROC-AUC en prueba |
|---|---:|---:|
| CNN desde cero | 55,03 % | 63,23 % |
| CNN con data augmentation | 61,07 % | 65,92 % |
| ResNet18 (transfer learning + fine-tuning) | 89,26 % | 95,55 % |

Los números dejan claro que reutilizar un modelo preentrenado y luego ajustarlo con cuidado fue, en esta práctica, la estrategia más efectiva, muy por encima de entrenar una red desde cero incluso con datos aumentados.

## 6. Grad-CAM: interpretando las decisiones del modelo

Para entender en qué se fija el modelo al clasificar, se implementó una versión simplificada de **Grad-CAM**, que genera un mapa de calor sobre la imagen de entrada:

```python
idx = 0
x, y = test_dataset_tl[idx]
cam, pred_class = grad_cam(resnet, x)
```

![08_gradcam.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/08_gradcam.png)

Las zonas más claras del mapa indican dónde puso más "atención" el modelo para tomar su decisión, mientras que las zonas oscuras aportaron poco. Esta herramienta permitió confirmar que el modelo no acertaba al azar, sino que efectivamente se apoyaba en regiones específicas de la imagen del objeto.

## 7. Clasificación binaria con Keras

En otra parte del notebook se trabajó con **Keras**, una librería que simplifica bastante la construcción de redes neuronales. Aquí el objetivo cambió: en lugar de imágenes, se usó el dataset **IMDB**, compuesto por reseñas de películas etiquetadas como negativas (`0`) o positivas (`1`).

El modelo base se definió así:

```python
model = models.Sequential()
model.add(layers.Dense(16, activation='relu', input_shape=(10000,)))
model.add(layers.Dense(16, activation='relu'))
model.add(layers.Dense(1, activation='sigmoid'))
```

```python
model.compile(optimizer='rmsprop',
              loss='binary_crossentropy',
              metrics=['accuracy'])

modelb = model.fit(partial_x_train,
                   partial_y_train,
                   epochs=20,
                   batch_size=512,
                   validation_data=(x_val, y_val))
```

En pocas palabras, **Keras permitió armar y entrenar la red en muy pocas líneas de código**. Al evaluar en el conjunto de prueba, el modelo alcanzó una **exactitud de 85,90 %**, con una pérdida cercana a **0,58**.

### 7.1. Sobreajuste

![09_keras_perdida_entrenamiento_validacion.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/09_keras_perdida_entrenamiento_validacion.png)

Al graficar la pérdida de entrenamiento junto a la de validación se observó un fenómeno de **sobreajuste**: la pérdida de entrenamiento siguió bajando en cada época, mientras que la de validación dejó de mejorar e incluso empezó a subir después de las primeras épocas. Esto significa que el modelo se estaba memorizando los ejemplos de entrenamiento en lugar de aprender patrones que se generalicen a reseñas nuevas.

### 7.2. Reducir el tamaño del modelo

Una primera estrategia para atenuar el sobreajuste fue reducir la cantidad de neuronas:

```python
model2 = models.Sequential()
model2.add(layers.Dense(4, activation='relu', input_shape=(10000,)))
model2.add(layers.Dense(1, activation='sigmoid'))
```

![10_keras_modelo_reducido.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/10_keras_modelo_reducido.png)

Con menos neuronas, la pérdida de validación se mantuvo estable por más épocas antes de empezar a subir, lo que indica un sobreajuste más leve, aunque el modelo sigue teniendo menos capacidad para captar relaciones complejas.

### 7.3. Regularización

Otra alternativa fue aplicar **regularización L2**, que penaliza a la red cuando sus pesos se vuelven demasiado grandes:

```python
model3 = models.Sequential()
model3.add(layers.Dense(16, activation='relu', input_shape=(10000,), kernel_regularizer=regularizers.l2(0.001)))
model3.add(layers.Dense(16, activation='relu', kernel_regularizer=regularizers.l2(0.001)))
model3.add(layers.Dense(1, activation='sigmoid'))
```

![11_keras_regularizacion.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/11_keras_regularizacion.png)

La regularización suavizó el crecimiento de la pérdida de validación en las últimas épocas, mostrando que penalizar pesos extremos ayuda a que el modelo no se especialice demasiado en los datos de entrenamiento.

### 7.4. Dropout

Por último se probó **dropout**, que apaga aleatoriamente una fracción de neuronas durante el entrenamiento:

```python
model4.add(layers.Dense(16, activation='relu', input_shape=(10000,)))
model4.add(layers.Dropout(0.5))
model4.add(layers.Dense(16, activation='relu'))
model4.add(layers.Dropout(0.5))
```

![12_keras_dropout.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/12_keras_dropout.png)

Al desactivar la mitad de las neuronas en cada paso de entrenamiento, la red se ve obligada a no depender de un pequeño grupo de ellas, lo que también contribuyó a reducir el sobreajuste observado.

### 7.5. Prueba de una predicción individual

Al revisar una predicción puntual (índice 10 del conjunto de prueba), el modelo asignó una probabilidad de **99,38 %** de que la reseña fuera positiva, lo cual sirvió para confirmar de forma concreta cómo se interpreta la salida de una red con activación sigmoide: un valor cercano a 1 indica alta confianza en la clase positiva.

## 8. Perceptrón

La última parte del notebook abordó el **perceptrón**, la unidad más básica de una red neuronal: recibe varias entradas, las combina mediante pesos y un sesgo (*bias*), y aplica una función de activación para decidir una salida.

```python
def step_function(x):
    return 1 if x >= 0 else 0

def perceptron(inputs, weights, bias, activation_func):
    weighted_sum = np.dot(inputs, weights) + bias
    output = activation_func(weighted_sum)
    return output
```

Como ejemplo práctico se simuló una posible alerta de sobrecalentamiento en un equipo industrial, a partir de dos señales:

```python
temperatura = 100
vibracion = 50
weights = np.array([0.5, -0.5])
bias = -30
inputs = np.array([temperatura, vibracion])
```

Con la función escalón, la salida fue **0** (sin alerta), y con la función tangente hiperbólica el resultado fue muy cercano a **-1**, mostrando que, aunque cambie la función de activación, ambas coincidieron en que la suma ponderada resultó negativa.

Luego se probó el comportamiento del perceptrón como compuertas lógicas **AND**, **OR** y **XOR**, variando los pesos y el sesgo. El perceptrón logró reproducir sin problema las compuertas AND y OR, pero no pudo resolver XOR por sí solo, ya que sus dos clases no se pueden separar con una sola línea recta.

![13_perceptron_xor.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/13_perceptron_xor.png)

Esto ayudó a visualizar por qué se necesita más de una neurona (una capa oculta) para resolver problemas que no son linealmente separables, como XOR.

## 9. Si llevamos estas ideas a nuestro proyecto

Si llevamos los conceptos aprendidos en la práctica a nuestro proyecto, el objetivo será desarrollar un sistema capaz de clasificar automáticamente papas mediante imágenes capturadas por una cámara, utilizando técnicas de Machine Learning y visión artificial. Para ello, contamos con una base de datos propia de imágenes de papas, las cuales serán utilizadas para entrenar un modelo que pueda reconocer patrones visuales relacionados con la condición del producto.

El modelo de Machine Learning que utilizaremos será YOLO (You Only Look Once), una arquitectura especializada en detección y clasificación de objetos en tiempo real. Mediante este modelo, el sistema podrá detectar la presencia de una papa dentro de la imagen y clasificarla según las categorías definidas previamente, por ejemplo, papa en buen estado o papa con defectos visibles.

![14_diagrama_flujo_papas_yolo.png](https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Proyecto_Integrador/Talleres/Taller_IA_Colab/Redes_Neuronales/Mogollon_Flores_Josue_Cristhian_Mateo/Imagenes/14_diagrama_flujo_papas_yolo.png)

Para mejorar el aprendizaje del modelo se aplicarán diferentes funciones y técnicas de Machine Learning:

- **Etiquetado de datos:** cada imagen de la base de datos tendrá una clasificación definida, permitiendo que el modelo conozca la condición real de cada papa durante el entrenamiento.
- **Data Augmentation:** permitirá generar variaciones de las imágenes mediante cambios de iluminación, rotación, escala o posición, aumentando la capacidad del modelo para reconocer papas en diferentes condiciones.
- **Transfer Learning:** se utilizará un modelo YOLO previamente entrenado con una gran cantidad de imágenes y se ajustará a nuestro problema específico, reduciendo el tiempo de entrenamiento y mejorando los resultados con una cantidad limitada de datos.
- **Evaluación del modelo:** se analizarán métricas como precisión, porcentaje de detecciones correctas y errores de clasificación para determinar el rendimiento del sistema.

Los resultados esperados serán realistas considerando la cantidad y calidad de imágenes disponibles. Se busca obtener un modelo capaz de detectar correctamente las papas y clasificarlas con una precisión aproximada entre 85% y 95%, dependiendo de factores como iluminación, variedad del producto, cantidad de imágenes utilizadas y calidad del etiquetado. Además, el sistema permitirá reducir la inspección manual y enviar el resultado de clasificación hacia la Raspberry Pi Pico.

## Conclusión

En conclusión, entender el rol del matching learning nos ayudo a comprender que este no solamente depende de elegir una arquitectura, sino también de la calidad de los datos, el entrenamiento y la evaluación de resultados. En nuestro proyecto, estas herramientas permitirán integrar visión artificial, inteligencia artificial y control electrónico para desarrollar un sistema automatizado de triaje poscosecha.

---

**Nota:** Se utilizó **IA** para mejorar y ordenar la redacción y las ideas del informe.
