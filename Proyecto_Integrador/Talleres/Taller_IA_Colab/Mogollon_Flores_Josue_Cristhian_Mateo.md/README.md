# Taller de Inteligencia Artificial

## Análisis de Datos y Modelos de Regresión

En este laboratorio se trabajó con un conjunto de datos relacionado con el consumo de energía, considerando variables como `Temperatura`, `Horas_Operacion`, `Carga` y `Humedad`.

El trabajo permitió desarrollar diferentes etapas del análisis de datos y aprendizaje automático. Primero se realizó una exploración de la información mediante gráficos, posteriormente se analizaron las relaciones entre variables y finalmente se implementó un modelo de Regresión Lineal para generar predicciones.

El objetivo fue comprender cómo los datos pueden ser utilizados para encontrar patrones, establecer relaciones y obtener estimaciones mediante un modelo predictivo.

---

# 1. Exploración inicial del conjunto de datos


### Visualización de las variables disponibles


<img src="../../Recursos/Imágenes/foto1.png" alt="Visualización inicial del conjunto de datos" width="900">


En esta primera etapa se realizó una revisión general del conjunto de datos para identificar las variables disponibles y comprender la información con la que trabajará el modelo.

Los datos analizados corresponden al consumo energético e incluyen factores como temperatura, horas de operación, carga y humedad, los cuales serán utilizados posteriormente para determinar relaciones y realizar predicciones.


---

# 2. Distribución del Consumo de Energía


### Histograma del Consumo de Energía


<img src="../../Recursos/Imágenes/foto2.png" alt="Histograma del Consumo de Energía" width="900">


El siguiente análisis permitió observar cómo se distribuyen los valores correspondientes al consumo energético.

En el histograma se aprecia que la mayoría de registros se concentran en valores intermedios, mientras que los consumos demasiado bajos o elevados aparecen con menor frecuencia.

Esta visualización permite conocer el comportamiento general de la variable objetivo antes de realizar el entrenamiento del modelo.


---

# 3. Relación entre las Variables


### Matriz de Correlación


<img src="../../Recursos/Imágenes/foto3.png" alt="Matriz de Correlación" width="900">


Después de analizar la distribución del consumo, se evaluó la relación existente entre las variables mediante una matriz de correlación.

Esta herramienta permite identificar la intensidad de relación lineal entre dos variables.

El resultado más importante fue:

**`Horas_Operacion` → `Consumo_Energia` = 0.84**

Este valor representa una relación positiva fuerte, indicando que cuando aumentan las horas de funcionamiento existe una tendencia a incrementar el consumo energético.

También se identificó una relación positiva entre:

**`Carga` → `Consumo_Energia` = 0.34**

Mientras que:

- `Temperatura` → `Consumo_Energia` ≈ **0.098**
- `Humedad` → `Consumo_Energia` ≈ **0.063**

presentan una relación menor.

Es importante considerar que la correlación permite identificar comportamientos relacionados entre variables, pero no determina directamente una relación de causa y efecto.


---

# 4. Construcción del Modelo de Regresión Lineal


### Selección de variables de entrada


<img src="../../Recursos/Imágenes/foto4.png" alt="Variables utilizadas en el modelo" width="900">


Para desarrollar el modelo predictivo se realizó la separación entre las variables independientes y la variable objetivo.

Las variables de entrada proporcionan la información necesaria para que el algoritmo pueda encontrar patrones, mientras que `Consumo_Energia` representa el valor que el modelo busca estimar.


---

# 5. Coeficientes obtenidos por el Modelo


### Interpretación de los coeficientes de regresión


<img src="../../Recursos/Imágenes/foto5.png" alt="Coeficientes del modelo" width="900">


Después del entrenamiento del modelo se analizaron los coeficientes obtenidos para conocer la participación de cada variable dentro de la predicción.

Los resultados muestran que:

- Temperatura: 0.137
- Horas_Operacion: 1.668
- Carga: 0.096
- Humedad: 0.027


La variable con mayor influencia fue `Horas_Operacion`, resultado que coincide con el análisis realizado previamente mediante la matriz de correlación.


---

# 6. Comparación de Valores Reales y Predichos


### Consumo de Energía Real vs Predicción


<img src="../../Recursos/Imágenes/foto6.png" alt="Consumo Real vs Predicho" width="900">


Luego del entrenamiento del modelo se generaron predicciones utilizando los datos de prueba.

La gráfica permite comparar los valores reales del consumo energético frente a los valores estimados por la regresión.

Se observa una tendencia creciente donde las predicciones siguen un comportamiento similar al de los valores reales, aunque existen diferencias producidas por el error propio del modelo.


---

# 7. Análisis de los Residuos


### Residuos vs Valores Predichos


<img src="../../Recursos/Imágenes/foto7.png" alt="Análisis de residuos" width="900">


Los residuos representan la diferencia entre el valor observado y el valor calculado por el modelo.

En la gráfica se observa que los puntos se distribuyen alrededor del valor cero sin presentar una tendencia definida.

Este análisis permite evaluar el comportamiento de los errores y comprobar si existe algún patrón que pueda afectar el rendimiento del modelo.


---

# 8. Importancia de las Características


### Análisis mediante Árbol de Decisión


<img src="../../Recursos/Imágenes/foto8.png" alt="Importancia de características" width="900">


Como análisis complementario se utilizó un árbol de decisión para determinar la importancia relativa de las características utilizadas.

Se observa que:

- X2 presenta la mayor importancia.
- X1 ocupa el segundo lugar.
- X3 tiene una participación intermedia.

Esto permite identificar qué variables tienen mayor influencia dentro de las decisiones tomadas por el modelo.


---

# 9. Análisis Estadístico


### Resultados de OLS Regression


<img src="../../Recursos/Imágenes/foto9.png" alt="Resultados estadísticos del modelo" width="900">


Finalmente se realizó un análisis estadístico utilizando OLS Regression Results.

Estos resultados permiten evaluar el comportamiento del modelo mediante indicadores estadísticos, coeficientes y medidas que ayudan a comprender la participación de cada variable dentro de la regresión.


---

# 10. Conclusiones


### Aprendizajes obtenidos


<img src="../../Recursos/Imágenes/foto10.png" alt="Conclusiones finales" width="900">


Durante el desarrollo del taller comprendí que la creación de un modelo de inteligencia artificial requiere diferentes etapas, iniciando desde la exploración y análisis de datos hasta la interpretación de los resultados obtenidos.

También comprendí cómo la regresión lineal permite realizar predicciones utilizando información histórica y cómo herramientas estadísticas y gráficas ayudan a evaluar el comportamiento del modelo.

Este trabajo permitió conocer una aplicación práctica de la inteligencia artificial orientada al análisis de datos y generación de predicciones.
