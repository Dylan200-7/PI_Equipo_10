# Informe de regresión: Plomo (Pb) en Troy, Alabama — 2023

## Introducción

En este trabajo se analizaron datos de calidad del aire correspondientes al **año 2023** en la estación **TROY LEAD**, ubicada en **Troy, Alabama, Estados Unidos**. El componente estudiado fue el **Plomo (Pb)**, representado en el archivo por la variable `Daily Mean Lead Concentration`.

El archivo utilizado fue `Lead_daily_aqs_data_downloaded_2026-09-18_19_45_02.csv`, el cual contiene **106 registros** obtenidos de información publicada por la **United States Environmental Protection Agency (EPA)**. A diferencia de otros contaminantes medidos a diario, el plomo en este monitor se registra aproximadamente **una vez por semana**, por lo que el conjunto de datos es considerablemente más pequeño.

El objetivo fue aplicar y comparar tres modelos de regresión —**Regresión Lineal**, **Árbol de Decisión** y **Random Forest**— para estimar la concentración diaria de plomo a partir de variables derivadas de la fecha y del identificador de sonda del monitor.

Las variables utilizadas como predictoras fueron:

- `Mes`
- `Dia_Semana`
- `Fin_Semana`
- `Sen_Anual`
- `Cos_Anual`
- `Codigo_Sonda` (columna original `POC`)

La variable que se desea predecir es:

- `Pb_ugm3` (`Daily Mean Lead Concentration`)

---

## Metodología

### 1. Datos utilizados

Los datos analizados corresponden a:

- **Año:** 2023
- **Componente:** Plomo (Pb)
- **Lugar / geografía:** Troy, Alabama, Estados Unidos (estación TROY LEAD)
- **Cantidad de registros:** 106

Primero se cargó el archivo CSV y se revisaron las columnas, los tipos de datos y la cantidad de valores distintos por columna. Esto permitió identificar columnas constantes (estación, coordenadas, unidades, método de medición) que se descartaron por no aportar información al modelo. Después se derivaron variables a partir de la fecha (`Mes`, `Dia_Anio`, `Dia_Semana`, `Fin_Semana`, `Sen_Anual`, `Cos_Anual`) y se conservó `Codigo_Sonda` como variable adicional.

### 2. Variables del modelo

La variable dependiente fue:

- **`Pb_ugm3`**: concentración media diaria de plomo en el aire (µg/m3).

Las variables independientes fueron:

1. **`Mes`**: mes del año (1 a 12).
2. **`Dia_Semana`**: día de la semana (0 = lunes, 6 = domingo).
3. **`Fin_Semana`**: variable binaria (1 = sábado o domingo, 0 = resto de la semana).
4. **`Sen_Anual`** / **`Cos_Anual`**: transformación cíclica que representa la estacionalidad anual.
5. **`Codigo_Sonda`**: identificador de la sonda del monitor (`POC`).

> Se excluyó la columna `Daily AQI Value` porque el Índice de Calidad del Aire se calcula a partir de la propia concentración de plomo (además, en este archivo no tiene ningún dato registrado). Incluirla generaría fuga de información (*data leakage*).

El modelo lineal se puede representar de la siguiente manera:

$$
\mathrm{Pb} = \beta_0 + \beta_1(\mathrm{Mes}) + \beta_2(\mathrm{Dia\_Semana}) + \beta_3(\mathrm{Fin\_Semana}) + \beta_4(\mathrm{Sen\_Anual}) + \beta_5(\mathrm{Cos\_Anual}) + \beta_6(\mathrm{Codigo\_Sonda})
$$

Donde $\beta_0$ es el intercepto y los demás coeficientes representan el aporte de cada variable al modelo.

### 3. Funciones principales utilizadas

- **`train_test_split()`**: divide los datos en un grupo para entrenar el modelo y otro para probarlo.
- **`LinearRegression()`**: crea el modelo de regresión lineal.
- **`DecisionTreeRegressor()`**: crea el modelo de árbol de decisión (`max_depth=5`).
- **`RandomForestRegressor()`**: crea el modelo de bosque aleatorio (`n_estimators=200`).
- **`fit()`**: entrena cada modelo usando los datos de entrenamiento.
- **`predict()`**: calcula los valores estimados de plomo para los datos de prueba.
- **`mean_absolute_error()`, `mean_squared_error()`, `r2_score()`**: calculan las métricas de error entre los valores reales y los predichos.
- **`sm.OLS()`** (statsmodels): genera un resumen estadístico completo del modelo lineal (coeficientes, valores p, R² ajustado).

### 4. División de entrenamiento y prueba

Los datos fueron divididos con `train_test_split()` de la siguiente forma:

- **70 %** de los datos para entrenamiento (**74 registros**).
- **30 %** de los datos para prueba (**32 registros**).
- `random_state = 7` para mantener la misma división cada vez que se ejecuta el análisis.

### 5. Entrenamiento del modelo lineal

Después de separar los datos se creó el modelo con `LinearRegression()` y se entrenó utilizando `fit()`.

Los coeficientes obtenidos fueron:

| Variable | Coeficiente |
|---|---:|
| Mes | 0.0155 |
| Dia_Semana | -0.0517 |
| Fin_Semana | 0.1784 |
| Sen_Anual | -0.0017 |
| Cos_Anual | 0.0670 |
| Codigo_Sonda | -0.0213 |

El término de intersección fue aproximadamente **0.1705**.

---

## Resultados

### 1. Distribución del plomo

![Histograma de la concentración diaria de plomo](./imagenes/01_histograma_pb.png)

**Figura 1. Histograma de Pb.**

**Interpretación:** La mayoría de los valores de plomo se concentran en niveles bajos (cercanos a 0.05 µg/m3), con algunos valores más altos que aparecen con menor frecuencia.

Los valores descriptivos principales fueron:

| Estadístico | Pb (µg/m3) |
|---|---:|
| Número de registros | 106 |
| Media | 0.112 |
| Desviación estándar | 0.188 |
| Mínimo | 0.002 |
| Primer cuartil | 0.021 |
| Mediana | 0.049 |
| Tercer cuartil | 0.116 |
| Máximo | 1.237 |

### 2. Correlación entre variables

![Matriz de correlación](./imagenes/02_matriz_correlacion.png)

**Figura 2. Matriz de correlación.**

**Interpretación:** A diferencia de otros contaminantes, ninguna variable presenta una correlación fuerte con el plomo. La relación más notoria es con `Dia_Semana` (**-0.2072**), seguida de `Mes` (**0.1600**). El resto de las variables muestra correlaciones débiles (por debajo de 0.13 en valor absoluto).

### 3. Variables predictoras frente al plomo

![Variables predictoras frente a Pb](./imagenes/03_variables_vs_pb.png)

**Figura 3. Variables predictoras frente a Pb.**

**Interpretación:** Ninguna variable muestra una relación visual clara y directa con la concentración de plomo, lo cual es consistente con los valores bajos de correlación observados en la matriz.

### 4. Valores reales frente a valores predichos — Regresión Lineal

Luego de entrenar el modelo se utilizó `predict()` con los datos de prueba.

![Pb real frente a Pb predicho - Regresión Lineal](./imagenes/04_real_vs_predicho_lineal.png)

**Figura 4. Pb real frente a Pb predicho (Regresión Lineal).**

**Interpretación:** Los puntos no siguen de forma clara la línea diagonal de referencia, lo que indica que el modelo lineal tiene dificultades para predecir con precisión la concentración de plomo.

### 5. Métricas de error — Regresión Lineal

$$
\mathrm{MSE} = \frac{1}{n}\sum_{i=1}^{n}(y_i-\hat{y}_i)^2
$$

| Métrica | Valor |
|---|---:|
| MAE | 0.1125 |
| MSE | 0.0202 |
| RMSE | 0.1422 |
| R² | -3.0954 |

**Interpretación:** Un **R² negativo** indica que el modelo lineal predice peor que si simplemente se usara el promedio de los datos de entrenamiento como predicción constante. Esto sugiere que, con las variables disponibles y solo 106 registros, la relación entre la fecha y el plomo no logra capturarse de forma lineal.

### 6. Histograma de residuos

![Histograma de residuos](./imagenes/05_histograma_residuos.png)

**Figura 5. Histograma de residuos.**

**Interpretación:** Los residuos no se distribuyen de forma simétrica alrededor de cero; se observa una cola hacia valores positivos, señal de que el modelo subestima algunas concentraciones altas de plomo.

### 7. Residuos frente a valores predichos

![Residuos frente a valores predichos](./imagenes/06_residuos_vs_predicho.png)

**Figura 6. Residuos frente a valores predichos.**

**Interpretación:** Los residuos no se distribuyen de manera uniforme alrededor de cero, lo que refuerza que el modelo lineal no logra un ajuste adecuado para este conjunto de datos.

### 8. Árbol de Decisión y Random Forest

Dado el bajo desempeño del modelo lineal, se probaron dos modelos no lineales.

![Pb real frente a Pb predicho - Árbol de Decisión](./imagenes/07_real_vs_predicho_arbol.png)

**Figura 7. Pb real frente a Pb predicho (Árbol de Decisión).**

![Pb real frente a Pb predicho - Random Forest](./imagenes/08_real_vs_predicho_rf.png)

**Figura 8. Pb real frente a Pb predicho (Random Forest).**

| Modelo | MAE | RMSE | R² |
|---|---:|---:|---:|
| Regresión Lineal | 0.1125 | 0.1422 | -3.0954 |
| Árbol de Decisión | 0.0988 | 0.2175 | -8.5821 |
| Random Forest | 0.0849 | 0.1521 | -3.6842 |

**Interpretación:** Ninguno de los tres modelos logra un ajuste aceptable. El **Árbol de Decisión** obtiene el peor R², probablemente por sobreajuste dado el tamaño reducido del conjunto de datos. El **Random Forest** mejora ligeramente el MAE frente a los otros dos modelos, pero sigue sin explicar la variación del plomo.

### 9. Importancia de las variables (Random Forest)

![Importancia relativa de las variables](./imagenes/09_importancia_variables.png)

**Figura 9. Importancia relativa de las variables.**

| Variable | Importancia |
|---|---:|
| Mes | 0.3514 |
| Dia_Semana | 0.3134 |
| Sen_Anual | 0.1969 |
| Cos_Anual | 0.1115 |
| Fin_Semana | 0.0203 |
| Codigo_Sonda | 0.0066 |

**Interpretación:** Las variables relacionadas con el momento del año (`Mes`, `Sen_Anual`, `Cos_Anual`) y con el día de la semana (`Dia_Semana`) son las que más peso tienen dentro del Random Forest, mientras que `Codigo_Sonda` prácticamente no aporta información.

### 10. Resumen estadístico (statsmodels)

Al ajustar el modelo con `statsmodels` sobre el conjunto completo de datos se obtuvo un **R² de 0.114** (R² ajustado de **0.061**), con un valor p del estadístico F de **0.0566** (en el límite de la significancia estadística usual de 0.05). La única variable individualmente significativa fue `Dia_Semana` (p = 0.006); `Fin_Semana` se acercó al umbral de significancia (p = 0.069).

---

## Discusión

Los resultados muestran que, a diferencia de contaminantes con series de tiempo diarias y más registros, la concentración de plomo en la estación TROY LEAD **no presenta una relación fuerte ni lineal** con las variables de fecha disponibles. Esto se refleja tanto en la matriz de correlación (todas las variables por debajo de 0.21 en valor absoluto) como en los valores de R² obtenidos por los tres modelos, todos negativos en el conjunto de prueba.

Una causa probable es el **tamaño reducido del conjunto de datos** (106 registros, con mediciones aproximadamente semanales), lo que dificulta que cualquier modelo —lineal o basado en árboles— generalice correctamente a datos no vistos. El **Random Forest** obtuvo el mejor MAE de los tres modelos, pero ninguno alcanza un desempeño satisfactorio.

El resumen de `statsmodels` sobre el conjunto completo sugiere que existe cierta señal (R² = 0.114, con `Dia_Semana` como variable significativa), pero que esta señal es débil y no logra transferirse de forma consistente a un conjunto de prueba pequeño.

En conclusión, el análisis realizado permitió explorar la relación entre las variables de fecha y la concentración de plomo en Troy, Alabama, durante 2023, pero evidenció que se necesitarían más años de mediciones y/o variables externas (por ejemplo, fuentes industriales cercanas o condiciones meteorológicas) para construir un modelo predictivo más robusto.

---

## Referencias

[1] United States Environmental Protection Agency, "Outdoor Air Quality Data," EPA. [En línea]. Disponible en: https://www.epa.gov/outdoor-air-quality-data. [Accedido: 19-sep-2026].

[2] United States Environmental Protection Agency, "Data," EPA. [En línea]. Disponible en: https://www.epa.gov/data. [Accedido: 19-sep-2026].

[3] United States Environmental Protection Agency, *Lead_daily_aqs_data_downloaded_2026-09-18_19_45_02.csv*, datos diarios de calidad del aire para Troy, Alabama, 2023.

