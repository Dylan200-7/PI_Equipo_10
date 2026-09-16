# Taller de Inteligencia Artificial

## Análisis de Datos y Modelos de Regresión

En este taller se trabajó con un conjunto de datos de **consumo energético**, compuesto por cien registros y cuatro variables predictoras —`Temperatura`, `Horas_Operacion`, `Carga` y `Humedad`— junto con la variable objetivo `Consumo_Energia`, que representa la cantidad de energía consumida por un equipo o sistema en función de sus condiciones de operación.

El desarrollo del taller siguió el flujo típico de un proyecto de aprendizaje automático supervisado: primero se realizó una exploración descriptiva de los datos para conocer su estructura y calidad; después se analizaron las relaciones estadísticas entre las variables mediante una matriz de correlación; posteriormente se construyó y entrenó un modelo de **Regresión Lineal Múltiple**, evaluando su desempeño a través de la comparación entre valores reales y predichos y del análisis de sus residuos; como complemento, se utilizó un **Árbol de Decisión** para explorar otra forma de medir la importancia de las variables; y finalmente se realizó una validación estadística formal del modelo mediante **OLS (Mínimos Cuadrados Ordinarios)**.

El propósito general fue comprender, de manera práctica, cómo un conjunto de datos histórico puede transformarse en un modelo predictivo, qué información aporta cada etapa del análisis, y cómo interpretar correctamente tanto los resultados obtenidos como las limitaciones propias de un modelo lineal.

---

## 1. Exploración inicial del conjunto de datos

### Visualización de las variables disponibles

<img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Recursos/Im%C3%A1genes/foto1.png" alt="Visualización inicial del conjunto de datos" width="900">

La primera etapa de cualquier proyecto de análisis de datos consiste en conocer a fondo la información con la que se va a trabajar, antes de intentar construir un modelo. Por ello, se cargó el conjunto de datos desde el archivo `Data_PI_regresion.csv` y se utilizaron funciones como `df.head()`, `df.info()` y `df.describe()` para inspeccionar su contenido.

Con `df.head()` se visualizaron los primeros registros, confirmando que el dataset contiene las cinco columnas esperadas y que sus valores son numéricos y coherentes con el fenómeno que describen (por ejemplo, temperaturas entre 20 y 30 grados, y horas de operación entre 4 y 11). Con `df.info()` se verificó que no existieran valores nulos ni tipos de dato inconsistentes, lo cual es indispensable antes de entrenar un modelo, ya que datos faltantes o mal tipificados pueden generar errores o sesgos en el entrenamiento. Finalmente, `df.describe()` permitió conocer medidas estadísticas básicas —media, desviación estándar, mínimos y máximos— de cada variable, dando una primera idea de la escala y dispersión de los datos.

En conjunto, esta exploración inicial confirma que el dataset está limpio, bien estructurado y listo para las siguientes etapas de análisis.

---

## 2. Distribución del Consumo de Energía

### Histograma del Consumo de Energía

<img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Recursos/Im%C3%A1genes/foto2.png" alt="Histograma del Consumo de Energía" width="900">

Antes de construir el modelo, es fundamental entender cómo se distribuyen los valores de la variable que se busca predecir, en este caso `Consumo_Energia`. Para ello se generó un histograma con 25 bins, que agrupa los valores del consumo en intervalos y muestra la frecuencia con la que ocurre cada uno.

El histograma revela una distribución con forma aproximadamente simétrica y unimodal (es decir, con un único pico central), donde la mayoría de los registros se concentran en valores intermedios de consumo. Los valores muy bajos o muy altos aparecen con menor frecuencia, sin señales evidentes de valores atípicos extremos que pudieran distorsionar el análisis.

Esta característica es una buena noticia de cara al modelo de regresión lineal, ya que este tipo de modelo asume (entre otras cosas) que los residuos se distribuyen de forma aproximadamente normal. Una variable objetivo con una distribución razonablemente simétrica facilita que ese supuesto se cumpla y contribuye a que las predicciones del modelo sean más estables y confiables.

---

## 3. Relación entre las Variables

### Matriz de Correlación

<img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Recursos/Im%C3%A1genes/foto3.png" alt="Matriz de Correlación" width="900">

Una vez comprendida la distribución de la variable objetivo, el siguiente paso fue analizar cómo se relaciona cada variable predictora con `Consumo_Energia`. Para esto se calculó el coeficiente de correlación de Pearson entre todas las variables numéricas y se visualizó el resultado mediante un mapa de calor (`heatmap`), donde los tonos más intensos representan relaciones más fuertes.

Los resultados obtenidos frente a `Consumo_Energia` fueron los siguientes:

| Variable | Correlación | Interpretación |
|---|---|---|
| `Horas_Operacion` | **0.84** | Relación positiva **fuerte** |
| `Carga` | **0.34** | Relación positiva **moderada** |
| `Temperatura` | ≈ 0.098 | Relación **muy débil** |
| `Humedad` | ≈ 0.063 | Relación **muy débil** |

El hallazgo más relevante es que `Horas_Operacion` presenta una correlación de 0.84 con el consumo energético, lo cual se considera una relación lineal fuerte: a medida que aumenta el tiempo de funcionamiento del equipo, el consumo energético tiende a incrementarse de manera consistente. `Carga` también muestra una relación positiva, aunque de intensidad moderada, sugiriendo que equipos con mayor carga de trabajo tienden a consumir algo más de energía, sin que esta relación sea tan determinante como la anterior. Por su parte, `Temperatura` y `Humedad` presentan correlaciones cercanas a cero, lo que indica que, dentro de este conjunto de datos, no existe una asociación lineal relevante entre estas variables ambientales y el consumo energético.

Es importante subrayar que la correlación mide exclusivamente el grado de asociación lineal entre dos variables, pero **no implica causalidad**: el hecho de que dos variables se muevan de forma conjunta no significa necesariamente que una sea la causa directa de los cambios en la otra. Este análisis, sin embargo, resulta muy útil como guía para anticipar qué variables tendrán mayor peso dentro del modelo de regresión que se construirá a continuación.

---

## 4. Construcción del Modelo de Regresión Lineal

### Selección de variables de entrada

<img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Recursos/Im%C3%A1genes/foto4.png" alt="Variables utilizadas en el modelo" width="900">

Para poder entrenar el modelo predictivo, primero fue necesario definir con claridad cuáles variables actuarían como entradas (predictoras) y cuál sería la variable a estimar. Se definió `X` como el conjunto formado por `Temperatura`, `Horas_Operacion`, `Carga` y `Humedad`, y `y` como la variable objetivo `Consumo_Energia`.

Posteriormente, el conjunto de datos se dividió en dos subconjuntos mediante `train_test_split`: un 70% para entrenamiento y un 30% para prueba, fijando `random_state=123` para garantizar que la división sea reproducible. Esta separación es una práctica fundamental en aprendizaje automático, ya que permite entrenar el modelo con una parte de los datos y evaluarlo posteriormente con datos que nunca vio durante el entrenamiento, lo que da una medida más honesta de su capacidad real de generalización.

Con los conjuntos ya definidos, se instanció un modelo `LinearRegression` de la librería scikit-learn y se ajustó (`fit`) utilizando los datos de entrenamiento (`X_train`, `y_train`).

---

## 5. Coeficientes obtenidos por el Modelo

### Interpretación de los coeficientes de regresión

<img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Recursos/Im%C3%A1genes/foto5.png" alt="Coeficientes del modelo" width="900">

Una vez entrenado el modelo, se obtuvo un intercepto de aproximadamente **2.74** y los siguientes coeficientes para cada variable:

| Variable | Coeficiente | Interpretación |
|---|---|---|
| `Temperatura` | 0.137 | Por cada grado adicional de temperatura, el consumo aumenta en promedio ~0.14 unidades, manteniendo el resto de variables constantes |
| `Horas_Operacion` | **1.669** | Por cada hora adicional de operación, el consumo aumenta en promedio ~1.67 unidades |
| `Carga` | 0.096 | Efecto positivo, pero leve |
| `Humedad` | 0.027 | Efecto prácticamente nulo |

En un modelo de regresión lineal múltiple, cada coeficiente representa el cambio esperado en la variable objetivo ante un aumento de una unidad en la variable correspondiente, manteniendo las demás variables sin cambios. Bajo esta lógica, `Horas_Operacion` resulta ser, con una diferencia considerable, la variable con mayor impacto sobre el consumo energético: su coeficiente (1.669) es más de diez veces mayor que el de la siguiente variable más influyente (`Temperatura`, con 0.137). Esto es totalmente coherente con lo observado previamente en la matriz de correlación, donde esta misma variable ya destacaba como la más asociada al consumo.

`Carga` mantiene un aporte positivo pero mucho más discreto, mientras que `Humedad` tiene un coeficiente tan cercano a cero que su contribución práctica a la predicción del consumo es mínima. Esta coincidencia entre el análisis de correlación y los coeficientes del modelo refuerza la confianza en que `Horas_Operacion` es el factor determinante dentro de este sistema.

---

## 6. Comparación de Valores Reales y Predichos

### Consumo de Energía Real vs Predicción

<img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Recursos/Im%C3%A1genes/foto6.png" alt="Consumo Real vs Predicho" width="900">

Con el modelo ya entrenado, se generaron predicciones sobre el conjunto de prueba (`X_test`, que el modelo nunca utilizó durante el entrenamiento) y se compararon contra los valores reales correspondientes (`y_test`) mediante un diagrama de dispersión, donde el eje horizontal representa el consumo real y el eje vertical el consumo predicho por el modelo.

Si el modelo fuera perfecto, todos los puntos se ubicarían exactamente sobre una línea diagonal imaginaria (donde predicción = valor real). En la gráfica obtenida, los puntos se agrupan de forma cercana a esa diagonal, siguiendo una tendencia claramente creciente y consistente, lo cual indica que el modelo logra capturar de manera adecuada el comportamiento general del consumo energético. Existe, como es de esperar en cualquier modelo del mundo real, cierta dispersión alrededor de esa línea ideal, producto del error inherente al modelo y de factores no capturados por las variables disponibles, pero en general el ajuste visual es bueno.

---

## 7. Análisis de los Residuos

### Residuos vs Valores Predichos

<img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Recursos/Im%C3%A1genes/foto7.png" alt="Análisis de residuos" width="900">

El residuo de una predicción se define como la diferencia entre el valor real observado y el valor estimado por el modelo (`y_test - predicciones`). Analizar el comportamiento de los residuos es una de las formas más importantes de validar si un modelo de regresión lineal es apropiado para los datos, más allá de solo mirar qué tan cerca están las predicciones de los valores reales.

En la gráfica de residuos frente a los valores predichos, se observa que los puntos se distribuyen de manera aleatoria alrededor del valor cero, sin formar ningún patrón sistemático como una curva, una tendencia ascendente o descendente, o un "embudo" que se abre o se cierra (lo que se conoce como heterocedasticidad). Esta ausencia de patrones es una señal positiva por dos motivos principales: primero, sugiere que el modelo no está dejando de capturar alguna relación no lineal importante entre las variables; y segundo, indica que la magnitud del error del modelo se mantiene relativamente constante a lo largo de todo el rango de predicciones, en lugar de crecer o disminuir sistemáticamente para ciertos valores.

En conjunto, este análisis respalda la validez del modelo de regresión lineal como una herramienta adecuada para este conjunto de datos.

---

## 8. Importancia de las Características (Árbol de Decisión)

### Análisis mediante Árbol de Decisión

<img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Recursos/Im%C3%A1genes/foto8.png" alt="Importancia de características" width="900">

Como análisis complementario, y con el objetivo de explorar otra técnica distinta a la regresión lineal para medir la importancia de las variables, se generó un **conjunto de datos sintético independiente** utilizando la función `make_regression` de scikit-learn (importante notar que, a partir de esta sección, ya no se trabaja con el dataset original de consumo energético, sino con datos simulados de 6 variables `X1` a `X6`, de las cuales solo 3 fueron definidas como verdaderamente informativas al momento de generarlas).

Sobre este conjunto sintético se entrenó un `DecisionTreeRegressor`, un modelo que, a diferencia de la regresión lineal, construye reglas de decisión jerárquicas para predecir la variable objetivo, y que además permite calcular qué tan importante fue cada variable para reducir el error del árbol. Las importancias relativas obtenidas fueron:

| Variable | Importancia relativa |
|---|---|
| **X2** | **0.537** (la más influyente, más de la mitad del peso total) |
| X1 | 0.269 |
| X3 | 0.111 |
| X4 | 0.038 |
| X6 | 0.033 |
| X5 | 0.012 |

Los resultados muestran que `X2` concentra por sí sola más de la mitad de la importancia total del modelo, seguida de `X1` con un aporte considerable, y de `X3` con una participación más moderada pero aún relevante. Las variables restantes (`X4`, `X5` y `X6`) tienen una influencia marginal, casi despreciable, dentro de las decisiones del árbol. Este resultado es consistente con el diseño del propio conjunto sintético, generado con solo tres variables verdaderamente informativas, lo que confirma que el árbol de decisión fue capaz de identificar correctamente cuáles eran las variables relevantes y cuáles eran esencialmente ruido.

Este ejercicio ilustra un punto valioso: además de los coeficientes de una regresión lineal, existen otras familias de modelos —como los basados en árboles— que ofrecen una forma alternativa, y en ocasiones complementaria, de cuantificar la importancia relativa de cada variable dentro de un problema predictivo.

---

## 9. Análisis Estadístico (OLS)

### Resultados de OLS Regression

<img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Recursos/Im%C3%A1genes/foto9.png" alt="Resultados estadísticos del modelo" width="900">

Para cerrar el análisis con un respaldo estadístico más riguroso, se ajustó un modelo de regresión por **Mínimos Cuadrados Ordinarios (OLS)** utilizando la librería `statsmodels`, nuevamente sobre el conjunto de datos sintético descrito en la sección anterior. A diferencia de scikit-learn, `statsmodels` entrega un resumen estadístico detallado que permite evaluar no solo qué tan bien ajusta el modelo, sino también qué tan confiables son sus coeficientes desde un punto de vista estadístico.

De este resumen destacan los siguientes resultados:

- **R² = 0.976** y **R² ajustado = 0.974**: esto significa que el modelo es capaz de explicar cerca del 97.6% de la variabilidad total de la variable objetivo a partir de las variables predictoras, lo cual representa un ajuste muy alto.
- **F-statistic = 628.6**, con un valor p extremadamente pequeño (p ≈ 5.97e-73): esto indica que el modelo, en su conjunto, es altamente significativo desde el punto de vista estadístico, es decir, existe una probabilidad prácticamente nula de que estos resultados se deban simplemente al azar.
- Al observar los valores p de cada coeficiente individual, se encuentra que **x1, x2 y x3 son estadísticamente significativos** (con valores p muy por debajo de 0.001), mientras que **x4, x5 y x6 no lo son** (con valores p muy por encima de 0.05).

Este último punto es particularmente interesante porque confirma, ahora desde una perspectiva estadística formal y no solo visual o intuitiva, exactamente lo mismo que ya se había observado tanto en los coeficientes del modelo como en la importancia de características calculada por el árbol de decisión: de las seis variables disponibles en el conjunto sintético, solo tres aportan información genuinamente relevante para explicar la variable objetivo, mientras que las tres restantes se comportan como ruido estadístico. La coincidencia entre tres métodos distintos —coeficientes de regresión, importancia por árbol de decisión, y significancia estadística en OLS— es una muestra sólida de la robustez de estos hallazgos.

---

## 10. Conclusiones

### Aprendizajes obtenidos

<img src="https://raw.githubusercontent.com/Dylan200-7/PI_Equipo_10/main/Recursos/Im%C3%A1genes/foto10.png" alt="Conclusiones finales" width="900">

El desarrollo de este taller permitió comprender que construir un modelo de inteligencia artificial no se limita simplemente a entrenar un algoritmo y obtener predicciones, sino que implica un proceso completo y cuidadoso: explorar los datos disponibles, entender sus distribuciones y la calidad de la información, analizar las relaciones existentes entre las variables, seleccionar y entrenar un modelo adecuado, y —de manera igualmente importante— **validar rigurosamente sus resultados** a través de distintas herramientas complementarias, como el análisis de residuos, la importancia de características mediante árboles de decisión, y las pruebas estadísticas formales que ofrece un análisis OLS.

También quedó claro que la regresión lineal es una herramienta especialmente poderosa e interpretable cuando existe una relación lineal fuerte y clara entre las variables, tal como ocurrió con `Horas_Operacion` en el dataset de consumo energético. Sin embargo, su buen desempeño depende de que se cumplan ciertos supuestos estadísticos (como la distribución de los residuos o la ausencia de heterocedasticidad), los cuales no deben darse por sentados, sino verificarse explícitamente mediante las técnicas empleadas a lo largo de este taller.

En conjunto, este trabajo representa una aplicación práctica y bastante completa de los fundamentos de la inteligencia artificial aplicados al análisis de datos, mostrando cómo distintas técnicas —regresión lineal, árboles de decisión y análisis estadístico— pueden combinarse para construir modelos predictivos más confiables y, sobre todo, mejor entendidos por quien los desarrolla.
