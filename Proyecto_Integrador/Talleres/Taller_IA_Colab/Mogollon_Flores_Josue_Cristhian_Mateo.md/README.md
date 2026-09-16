# Taller de Inteligencia Artificial

## Análisis de Datos y Modelos de Regresión

En este taller se trabajó con un conjunto de datos de **consumo energético**, compuesto por las variables `Temperatura`, `Horas_Operacion`, `Carga` y `Humedad` como predictoras, y `Consumo_Energia` como variable objetivo.

El desarrollo siguió el flujo típico de un proyecto de aprendizaje automático: exploración de los datos, análisis de relaciones entre variables, construcción de un modelo de **Regresión Lineal**, evaluación de su desempeño mediante residuos, un análisis complementario de importancia de características con un **Árbol de Decisión**, y finalmente una validación estadística formal con **OLS (Mínimos Cuadrados Ordinarios)**.

El objetivo fue comprender cómo un conjunto de datos histórico puede transformarse en un modelo capaz de generar predicciones confiables, y cómo interpretar tanto sus resultados como sus limitaciones.

---

## 1. Exploración inicial del conjunto de datos

### Visualización de las variables disponibles

<img src="Recursos/Imágenes/foto1.png" alt="Visualización inicial del conjunto de datos" width="900">

Se realizó una revisión general del dataset (`df.head()`, `df.info()`, `df.describe()`) para identificar el tipo de dato de cada columna, verificar que no existieran valores nulos y conocer los rangos en que se mueve cada variable.

El conjunto de datos contiene 100 registros con cuatro variables independientes —temperatura, horas de operación, carga y humedad— que se utilizarán para explicar y predecir el consumo energético.

---

## 2. Distribución del Consumo de Energía

### Histograma del Consumo de Energía

<img src="Recursos/Imágenes/foto2.png" alt="Histograma del Consumo de Energía" width="900">

Antes de entrenar cualquier modelo es importante conocer cómo se comporta la variable objetivo. El histograma de `Consumo_Energia` muestra una distribución aproximadamente simétrica, con la mayoría de los registros concentrados en valores intermedios y una menor frecuencia de consumos extremos (muy bajos o muy altos).

Esta forma de distribución es una buena señal para un modelo lineal, ya que no se observan sesgos fuertes ni valores atípicos evidentes que puedan distorsionar el ajuste.

---

## 3. Relación entre las Variables

### Matriz de Correlación

<img src="Recursos/Imágenes/foto3.png" alt="Matriz de Correlación" width="900">

Se calculó la matriz de correlación de Pearson entre todas las variables numéricas para medir la fuerza y dirección de sus relaciones lineales. Los resultados más relevantes frente a `Consumo_Energia` fueron:

| Variable | Correlación | Interpretación |
|---|---|---|
| `Horas_Operacion` | **0.84** | Relación positiva **fuerte** |
| `Carga` | **0.34** | Relación positiva **moderada** |
| `Temperatura` | ≈ 0.098 | Relación **débil** |
| `Humedad` | ≈ 0.063 | Relación **débil** |

`Horas_Operacion` es, por amplio margen, la variable más asociada al consumo: a mayor tiempo de funcionamiento del equipo, mayor es el consumo energético registrado. `Carga` aporta una relación positiva más moderada, mientras que `Temperatura` y `Humedad` prácticamente no muestran asociación lineal con el consumo.

Es importante recalcar que la correlación mide únicamente asociación lineal, **no causalidad**: que dos variables se muevan juntas no implica que una sea la causa directa de la otra.

---

## 4. Construcción del Modelo de Regresión Lineal

### Selección de variables de entrada

<img src="Recursos/Imágenes/foto4.png" alt="Variables utilizadas en el modelo" width="900">

Se separaron las variables predictoras (`X` = `Temperatura`, `Horas_Operacion`, `Carga`, `Humedad`) de la variable objetivo (`y` = `Consumo_Energia`), y posteriormente se dividió el conjunto en entrenamiento (70%) y prueba (30%) usando `train_test_split` con `random_state=123`, de modo que el modelo se evalúe con datos que no vio durante el entrenamiento.

El modelo utilizado fue `LinearRegression` de scikit-learn, ajustado sobre el conjunto de entrenamiento.

---

## 5. Coeficientes obtenidos por el Modelo

### Interpretación de los coeficientes de regresión

<img src="Recursos/Imágenes/foto5.png" alt="Coeficientes del modelo" width="900">

Una vez entrenado el modelo (intercepto ≈ 2.74), se obtuvieron los siguientes coeficientes:

| Variable | Coeficiente | Interpretación |
|---|---|---|
| `Temperatura` | 0.137 | Por cada grado adicional, el consumo sube ~0.14 unidades |
| `Horas_Operacion` | **1.669** | Por cada hora adicional de operación, el consumo sube ~1.67 unidades |
| `Carga` | 0.096 | Efecto positivo leve |
| `Humedad` | 0.027 | Efecto casi nulo |

Los coeficientes confirman lo observado en la matriz de correlación: `Horas_Operacion` es, con diferencia, la variable con mayor peso dentro del modelo, seguida —muy por debajo— de `Temperatura` y `Carga`. `Humedad` prácticamente no contribuye a la predicción del consumo.

---

## 6. Comparación de Valores Reales y Predichos

### Consumo de Energía Real vs Predicción

<img src="Recursos/Imágenes/foto6.png" alt="Consumo Real vs Predicho" width="900">

Con el modelo ya entrenado, se generaron predicciones sobre el conjunto de prueba (`X_test`) y se compararon contra los valores reales (`y_test`) en un diagrama de dispersión.

Los puntos se alinean de forma cercana a la diagonal ideal (donde predicción = valor real), lo que indica que el modelo captura adecuadamente la tendencia general del consumo energético, aunque con cierta dispersión propia del error del modelo.

---

## 7. Análisis de los Residuos

### Residuos vs Valores Predichos

<img src="Recursos/Imágenes/foto7.png" alt="Análisis de residuos" width="900">

El residuo es la diferencia entre el valor real y el valor predicho (`y_test - predicciones`). Analizar su comportamiento permite verificar si el modelo lineal es adecuado para los datos.

En la gráfica de residuos vs. valores predichos, los puntos se distribuyen de forma aleatoria alrededor de cero, sin formar un patrón curvo ni un embudo (heterocedasticidad). Esto es una buena señal: sugiere que el modelo no está omitiendo relaciones no lineales importantes y que la varianza del error se mantiene razonablemente constante a lo largo del rango de predicciones.

---

## 8. Importancia de las Características (Árbol de Decisión)

### Análisis mediante Árbol de Decisión

<img src="Recursos/Imágenes/foto8.png" alt="Importancia de características" width="900">

Como análisis complementario —y **sobre un conjunto de datos sintético independiente**, generado con `make_regression` (6 variables `X1`–`X6`, no el dataset de consumo energético)— se entrenó un `DecisionTreeRegressor` para explorar otra forma de medir la importancia de las variables.

Las importancias relativas obtenidas fueron:

| Variable | Importancia relativa |
|---|---|
| **X2** | **0.537** (la más influyente) |
| X1 | 0.269 |
| X3 | 0.111 |
| X6 | 0.033 |
| X4 | 0.038 |
| X5 | 0.012 |

`X2` concentra más de la mitad del peso del modelo, seguida de `X1` y, en menor medida, `X3`; el resto de variables aporta muy poco. Este ejercicio sirve para mostrar que, además de los coeficientes de una regresión lineal, existen métodos basados en árboles que también permiten cuantificar qué variables explican mejor la variable objetivo.

---

## 9. Análisis Estadístico (OLS)

### Resultados de OLS Regression

<img src="Recursos/Imágenes/foto9.png" alt="Resultados estadísticos del modelo" width="900">

Para validar formalmente el modelo se ajustó una regresión por **Mínimos Cuadrados Ordinarios (OLS)** con `statsmodels` sobre el mismo conjunto sintético de la sección anterior. Los resultados más relevantes fueron:

- **R² = 0.976** y **R² ajustado = 0.974**: el modelo explica cerca del 97.6% de la variabilidad de la variable objetivo, un ajuste muy alto.
- **F-statistic = 628.6** (p ≈ 5.97e-73): el modelo en conjunto es altamente significativo.
- De los seis predictores, **x1, x2 y x3 son estadísticamente significativos** (p < 0.001), mientras que **x4, x5 y x6 no lo son** (p > 0.05) — coherente con que el dataset se generó con solo 3 variables informativas (`n_informative=3`).

Esto confirma, desde una perspectiva estadística formal, lo que ya se había observado con los coeficientes y con la importancia de características del árbol de decisión: solo una parte de las variables disponibles aporta información real al modelo.

---

## 10. Conclusiones

### Aprendizajes obtenidos

<img src="Recursos/Imágenes/foto10.png" alt="Conclusiones finales" width="900">

El desarrollo de este taller permitió comprender que construir un modelo de inteligencia artificial no se reduce a entrenarlo, sino que implica un proceso completo: explorar los datos, entender sus distribuciones y relaciones, seleccionar y entrenar el modelo, y —igual de importante— **validar sus resultados** mediante residuos, importancia de características y pruebas estadísticas.

También quedó claro que la regresión lineal es una herramienta poderosa e interpretable cuando existe una relación lineal fuerte entre las variables (como ocurrió con `Horas_Operacion`), pero que su desempeño depende de qué tan bien se cumplan sus supuestos, algo que se puede verificar con herramientas complementarias como el análisis de residuos, los árboles de decisión y el resumen estadístico de OLS.

En conjunto, este trabajo representa una aplicación práctica y completa de la inteligencia artificial orientada al análisis de datos y a la generación de predicciones confiables.

