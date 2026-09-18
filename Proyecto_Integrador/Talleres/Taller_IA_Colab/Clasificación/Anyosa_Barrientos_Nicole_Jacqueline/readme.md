# Análisis de la concentración de CO durante el año 2023

## 1. Introducción

En este trabajo se realizó un análisis de datos de concentración de monóxido de carbono (CO) correspondientes al año 2023. El objetivo fue conocer las características principales de los datos y aplicar modelos de regresión para estimar la concentración máxima de CO durante 8 horas.

Se utilizaron dos métodos: **Regresión Lineal** y **Random Forest**.

## 2. Metodología

Se trabajó con el archivo `Data_CO.csv`. Primero se realizó un análisis exploratorio de los datos mediante tablas, estadísticas descriptivas y gráficos.

La variable que se quiso predecir fue:

* `Daily Max 8-hour CO Concentration`

Para los modelos se utilizaron como variables predictoras:

* `Daily Obs Count`
* `Site Latitude`
* `Site Longitude`

Los datos se dividieron en **70 % para entrenamiento y 30 % para prueba**, utilizando `random_state=123`.

Para evaluar los modelos se utilizaron las métricas **MAE, MSE, RMSE y R²**.

## 3. Análisis exploratorio

Primero se revisó la información general del conjunto de datos y sus estadísticas descriptivas.

Luego se realizaron gráficos de dispersión, un histograma y un gráfico de densidad para observar la distribución de la concentración de CO.

También se calculó la matriz de correlación de las variables numéricas y se representó mediante un mapa de calor.

Estos gráficos permitieron observar la distribución de los datos y la relación entre las variables utilizadas.

## 4. Regresión Lineal

Se aplicó un modelo de Regresión Lineal utilizando las tres variables seleccionadas.

Los resultados obtenidos fueron:

* **MAE:** 0.1149
* **MSE:** 0.0287
* **RMSE:** 0.1693
* **R²:** 0.0369

El modelo presentó un R² bajo, lo que indica que las variables seleccionadas explican una parte pequeña de la variación de la concentración de CO.

## 5. Random Forest

Se aplicó un modelo **Random Forest Regressor** utilizando 100 árboles y `random_state=123`.

Los resultados obtenidos fueron:

* **MAE:** 0.1024
* **MSE:** 0.0246
* **RMSE:** 0.1568
* **R²:** 0.1734

Además, se calculó la importancia de las variables utilizadas en el modelo.

## 6. Resultados

Los resultados de ambos modelos fueron:

| Modelo           |    MAE |    MSE |   RMSE |     R² |
| ---------------- | -----: | -----: | -----: | -----: |
| Regresión Lineal | 0.1149 | 0.0287 | 0.1693 | 0.0369 |
| Random Forest    | 0.1024 | 0.0246 | 0.1568 | 0.1734 |

En este conjunto de datos, Random Forest obtuvo un menor MAE, MSE y RMSE, además de un mayor R² que la Regresión Lineal.

## 7. Conclusiones

Se realizó el análisis exploratorio de los datos de CO del año 2023 y se aplicaron los modelos de Regresión Lineal y Random Forest.

La Regresión Lineal presentó un R² de **0.0369**, mientras que Random Forest presentó un R² de **0.1734**.

De acuerdo con las métricas obtenidas, los dos modelos presentan errores en sus predicciones, aunque Random Forest obtuvo mejores resultados en este conjunto de datos.

## 8. Referencias

[1] U.S. Environmental Protection Agency, “Exploratory Data Analysis,” EPA.

[2] R. Henderson, *Six Sigma Quality Improvement with Minitab*, 2nd ed. Wiley, 2011.

