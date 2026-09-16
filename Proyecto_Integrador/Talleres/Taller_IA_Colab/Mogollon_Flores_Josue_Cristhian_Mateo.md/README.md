# Análisis de Datos y Modelo de Regresión Lineal

En este trabajo se realizó un análisis de un conjunto de datos relacionado con el consumo de energía, utilizando diferentes técnicas de exploración, análisis estadístico y aprendizaje automático.

El objetivo fue comprender el comportamiento de las variables, identificar relaciones entre ellas y aplicar un modelo de regresión lineal para realizar predicciones.

---

# FOTO 1: Presentación de los datos

<img src="imagenes/foto1.png" alt="Presentación de los datos" width="900">

##  Descripción de la captura:

La imagen corresponde a la visualización inicial del conjunto de datos, donde se muestran las variables utilizadas:

- Temperatura
- Horas_Operacion
- Carga
- Humedad
- Consumo_Energia


### Explicación:

En esta primera etapa se realizó una revisión general de la información disponible con la finalidad de conocer la estructura del conjunto de datos.

Las variables analizadas representan diferentes factores que pueden relacionarse con el consumo energético, permitiendo identificar qué información será utilizada posteriormente para desarrollar el modelo predictivo.

---

# FOTO 2: Histograma del consumo de energía

<img src="imagenes/foto2.png" alt="Histograma del consumo de energía" width="900">

## 📸 Descripción de la captura:

La gráfica representa la distribución de la variable:

**Consumo_Energia**

### Explicación:

Se evaluó el comportamiento de la variable objetivo mediante un histograma, con la finalidad de observar cómo se distribuyen los valores registrados.

Se puede apreciar que la mayor concentración de datos se encuentra en valores intermedios, mientras que los consumos extremos presentan una menor frecuencia.

Este análisis permite conocer las características generales de los datos antes de aplicar el modelo de regresión.

---

# FOTO 3: Matriz de correlación

<img src="imagenes/foto3.png" alt="Matriz de correlación" width="900">

## 📸 Descripción de la captura:

Mapa de calor donde se muestra la relación entre las diferentes variables del conjunto de datos.

### Explicación:

La matriz de correlación permite identificar qué variables presentan una mayor relación lineal con el consumo energético.

El resultado más representativo fue:

**Horas_Operacion → Consumo_Energia = 0.84**

Esto indica una relación positiva fuerte, donde un incremento en las horas de funcionamiento está asociado con un aumento del consumo energético.

Por otro lado, variables como temperatura y humedad presentan una relación menor con la variable objetivo.

---

# FOTO 4: Variables utilizadas en el modelo

<img src="imagenes/foto4.png" alt="Separación de variables del modelo" width="900">

## 📸 Descripción de la captura:

Se muestran las variables independientes utilizadas como entrada del modelo:

- Temperatura
- Horas_Operacion
- Carga
- Humedad


### Explicación:

Para desarrollar el modelo predictivo fue necesario separar las variables de entrada y la variable que se desea estimar.

Las características seleccionadas funcionan como información de referencia para que el algoritmo pueda encontrar patrones y generar predicciones sobre el consumo energético.

---

# FOTO 5: Coeficientes del modelo

<img src="imagenes/foto5.png" alt="Coeficientes del modelo" width="900">

## 📸 Descripción de la captura:

Resultados obtenidos después del entrenamiento de la regresión lineal.

Valores principales:

- Temperatura: 0.137
- Horas_Operacion: 1.668
- Carga: 0.096
- Humedad: 0.027


### Explicación:

Después de entrenar el modelo se analizaron los coeficientes obtenidos para conocer la participación de cada variable dentro de la predicción.

La característica con mayor influencia fue **Horas_Operacion**, resultado que coincide con la relación encontrada previamente mediante la matriz de correlación.

---

# FOTO 6: Valores reales vs valores predichos

<img src="imagenes/foto6.png" alt="Consumo real vs predicho" width="900">

## 📸 Descripción de la captura:

Gráfica comparativa entre los valores reales del consumo energético y las predicciones realizadas por el modelo.

### Explicación:

Esta gráfica permite evaluar visualmente qué tan cerca se encuentran las predicciones respecto a los valores reales.

Se observa una tendencia creciente, indicando que el modelo logra representar correctamente el comportamiento general de los datos.

Sin embargo, existen diferencias entre algunos puntos debido al error natural presente en cualquier modelo predictivo.

---

# FOTO 7: Análisis de residuos

<img src="imagenes/foto7.png" alt="Valores residuales vs predichos" width="900">

## 📸 Descripción de la captura:

Gráfico donde se muestran los residuos obtenidos por el modelo.

### Explicación:

Los residuos representan la diferencia entre el valor real y el valor calculado por la regresión.

Al analizar la gráfica se observa que los errores se distribuyen alrededor del valor cero sin seguir un patrón definido.

Esto permite revisar el comportamiento del modelo y verificar cómo se distribuyen sus errores.

---

# FOTO 8: Importancia de características

<img src="imagenes/foto8.png" alt="Importancia relativa de características" width="900">

## 📸 Descripción de la captura:

Gráfico generado mediante un árbol de decisión donde se muestra la importancia relativa de cada característica.

### Explicación:

Como complemento del análisis se utilizó un árbol de decisión para identificar qué variables tienen mayor participación dentro del modelo.

Se observa que:

- X2 presenta la mayor importancia.
- X1 ocupa el segundo lugar.
- X3 tiene una participación intermedia.

Las demás variables tienen una influencia menor dentro del resultado obtenido.

---

# FOTO 9: Análisis estadístico del modelo

<img src="imagenes/foto9.png" alt="OLS Regression Results" width="900">

## 📸 Descripción de la captura:

Resumen estadístico generado mediante OLS Regression Results.

### Explicación:

Finalmente se realizó una evaluación estadística del modelo para complementar los resultados obtenidos.

Este análisis permite revisar indicadores como el ajuste del modelo, los coeficientes calculados y la participación de cada variable dentro de la regresión.

El resultado permite comprender con mayor detalle cómo funciona internamente el modelo predictivo.

---

# FOTO 10: Conclusión personal

<img src="imagenes/foto10.png" alt="Conclusión personal" width="900">

## 📸 Descripción de la captura:

Reflexión final sobre los conocimientos adquiridos durante el desarrollo del taller.

### Explicación:

Durante el desarrollo del taller comprendí que la creación de un modelo de inteligencia artificial requiere más que ejecutar un algoritmo.

Primero es necesario analizar la información, identificar patrones y comprender la relación existente entre las variables.

Además, aprendí cómo la regresión lineal permite realizar predicciones utilizando datos históricos y cómo herramientas como gráficos, correlaciones y análisis estadístico ayudan a interpretar los resultados obtenidos.

Este trabajo permitió conocer una aplicación práctica de la inteligencia artificial orientada al análisis de datos y generación de predicciones.
