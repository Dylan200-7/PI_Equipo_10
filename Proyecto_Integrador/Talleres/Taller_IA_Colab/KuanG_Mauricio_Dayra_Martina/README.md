Taller de IA: Regresión lineal y Análisis de Datos

En el taller del día de hoy se ha trabajado con librerías como NumPy, Matplotlib, Seaborn, Pandas, Scikit-learn y Statsmodels, las cuales permiten trabajar con data pesada, realizar cálculos, gráficos y construir modelos de regresión,

En primer lugar, se importó una Data utilizando la librería Pandas y esta se editó mediante DataFrame. Del mismo modo, la librería Numpy permitió realizar cálculos numéricos y trabajar con arreglos. Además, con el uso de matplotlib y seaborn se pudo realizar gráficas de diferentes variables.

Lo más destacado fue cuando se separaron los datos en dos grupos utilizando train_test_split:
•	70 % para entrenamiento
•	30 % para prueba

1. Regresión Lineal

Este es un método que permite encontrar una relación entre diferentes variables de entrada y una variable de salida. 
En el taller, se utilizó para intentar predecir el Consumo_Energia a partir de distintas características. 
Para ello, se crea un modelo con “LinearRegression” de Scikit-learn, se guardó como lm y se entrenó utilizando los datos disponibles. Una vez entrenado, se pudo utilizar "lm.predict(X_test)" para obtener las predicciones del consumo de energía para nuevos datos.

2. Random Forrest

La función “make_regression” permitió generar datos artificiales para probar diferentes modelos de regresión. 
En el taller, se generaron 100 muestras con 6 características, de las cuales solamente 3 son informativas, es decir, realmente influyen en la variable de salida. 
Además, se agrega ruido para hacer que los datos sean más realistas y se utiliza una semilla aleatoria para obtener resultados reproducibles. 
Estos datos pueden utilizarse posteriormente para entrenar un modelo como Random Forest, que aprende la relación entre las características y la variable de salida y permite realizar predicciones. 
De esta manera, “make_regression” se encarga de generar los datos, mientras que Random Forest se encarga de aprender de ellos y predecir resultados.

3. Standard Error y T-statistic

Primero se determinó cuántos datos y cuántas variables tiene el conjunto de entrenamiento.
n = X_train.shape[0] indica la cantidad de datos u observaciones que tenemos. 
k = X_train.shape[1] indica la cantidad de variables independientes utilizadas por el modelo. En el caso trabajado en el taller, k corresponde a 4 variables.

Luego se calculan los grados de libertad mediante “dfN = n - k” Los grados de libertad representan la cantidad de información disponible para estimar el error del modelo después de considerar las variables utilizadas.
Después de entrenar el modelo de regresión lineal, se utilizan los datos de entrenamiento para obtener las predicciones:”train_pred = lm.predict(X_train)”. Esto permite comparar los valores que el modelo predice con los valores reales de Y_train. De esta manera podemos evaluar qué tan cerca están las predicciones de los valores reales.

Para calcular el error se resta el valor real al valor predicho: 
“train_error = np.square(train_pred - Y_train)”
Después, todos estos errores se suman y se guardan. Para calcular el Standard Error para cada variable. 
El error estándar permite conocer qué tanta incertidumbre existe alrededor de cada coeficiente estimado por el modelo. 
Una vez obtenido el error estándar, se calcula el t-statistic y compara el tamaño del coeficiente con su error estándar. 
Por lo tanto, permite observar qué tan grande es el coeficiente en relación con la incertidumbre de su estimación.

4. Árbol de decisiones

En el taller también pudimos observar otra opción de regresión lineal. A través de DecisionTreeRegressor, se creó un árbol de decisiones para regresión, para predecir un valor numérico.
Se trabajó de la misma manera con Consumo_Energia. El árbol funciona realizando diferentes divisiones sobre las variables de entrada.
En el modelo realizado en clase se estableció "max_depth=5", lo que significa que el árbol puede tener como máximo cinco niveles de decisión. 

Después de entrenar el árbol, se realizan predicciones utilizando los datos de prueba:
“test_pred = tree_model.predict(X_test)”. Aquí “X_test2 contiene datos que el modelo no utilizó durante el entrenamiento. 
El árbol utiliza lo que aprendió para intentar predecir los valores correspondientes de "Y_test". Luego se crea un gráfico de dispersión. En el eje X se colocan los valores reales de `Y_test` y en el eje Y se colocan los valores predichos por el árbol.
Finalmente, se calcula el Mean Squared Error (MSE) que permite evaluar numéricamente el desempeño del árbol de decisión.

5. Statsmodels

Finalmente, se vió de manera rápida, una última forma de realizar una regresión utilizando Statsmodels.
Con OLS pudo realizar una regresión lineal por mínimos cuadrados ordinarios y obtener un resumen estadístico bastante completo del modelo.
