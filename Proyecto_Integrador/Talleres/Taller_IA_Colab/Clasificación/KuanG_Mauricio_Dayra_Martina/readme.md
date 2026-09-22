Actividad: Regresión Lineal
datos:
  - Caso de estudio: Phoenix-Mesa-Scottsdale, Arizona
  - Periodo analizado: 2022
  - Fuente de datos: United States Environmental Protection Agency (EPA)

1. Modelo de Regresión
  Para la presente actividad, se escogió el modelo de regresión lineal simple.
  Entonces, se definió:
  - 1 variable x: independiente
  - 1 variable Y: dependiente
  
  Recordemos que la regresión lineal busca una relación de la siguiente forma: y=bo​+b1(​x)

2. Definición de Variables 
  Se definió como variables X,y
   X = Daily Max 1-hour NO2 Concentration
   y = Daily AQI Value

  En palabras mas simples, el objetivo fue estudiar cómo cambia el AQI diario en función de la concentración de NO₂ reportada diariamente.
  Se escogió a "Daily Max 1-hour NO2 Concentration" como variable independiente ya que el dataset puso en evidencia que el "Daily AQI Value"
  y el "Daily Max 1-hour NO2 Concentration" están muy estrechamente relacionados por cómo se calcula el AQI.
  Muy a parte, en la sección 3 del código, se consulto que los tipos de datos utilizadas en la regresión fueran numéricas.
  El código indicó:  Daily Max 1-hour NO2 Concentration - 2157 - non-null - float64
  Por lo que si se puede usar para la regresión lineal

4. Realización de la Regresión Lineal Simple
   En primer lugar, se importó "LinearRegression"
   En segundo lugar, se separaron los datos para entrenamiento y prueba:
   - 80 % → entrenamiento: Son los datos que se usarán para aprender la relación entre NO₂ y AQI
   - 20 % → prueba: Son los con datos que no utilizó durante el entrenamiento y se usaran para ver como funciona el modelo
   - Y se escogió una semilla de 42
   Luego, se creó el modelo mediante "modelo = LinearRegression()" y se mejoró mediante ".fit()"

5. Ecuación de la Recta
   Como se mencionó anteriormente, la recta tiene la forma: y=bo​+b1(​x), entonces se encontraron los datos de la pendiente y el intercento.
   Para:
   1. Daily AQI value = y
   2. Daily Max 1-hour NO2 Concentratio = x
   3. Pendiente = 0.951
   4. Intercepto: -0.295
   Entoncones la recta queda de la forma: y = 0.951(x) - 0.295

    Podemos interpretar que por cada incremento de una unidad en la concentración de NO₂, el AQI estimado aumenta aproximadamente 0.95 unidades.
    Además, el intercepto representa el Daily AQI value estimado cuando la concentración de NO₂ es cero, es decir -0.295, mientras que la pendiente
     representa cuánto cambia el AQI por cada unidad adicional de NO₂.

7. Predicciones
   Creamos la variable "y_pred" para que el modelo pueda predecir valores usando "X_test"
   Consiguiente, evaluamos el modelo, se importó las métricas de evaluación, haciendo uso de "y_pred" y "y_test", se obtuvieron los siguientes valores:
   1. MAE: 0.2678868849198018 - Indica cuanto se equivoca el modelo en promedio
   2. RMSE: 0.3319004254171387 - Indica los errores mas altos en las predicciónes
   3. R²: 0.9991211157783192 - Mientras el valor se acerque mas a 1, significa que se realizaron buenas predicciones
   
   En otras palabras, el valor de R² de indica que la concentración de NO₂ explica a la variabilidad observada del AQI en el conjunto de datos.
    Existe una relación lineal muy considerable entre las dos variables.

  Finalmente, se interpretó la pendiente y se representó gráficamente la recta de regresión lineal simple.
   
   
