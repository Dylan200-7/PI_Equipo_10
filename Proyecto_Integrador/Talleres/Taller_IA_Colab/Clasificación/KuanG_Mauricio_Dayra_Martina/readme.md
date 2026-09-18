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
  El código indicó:  Daily Max 1-hour NO2 Concentration  2157 non-null   float64
  Por lo que si se puede usar para la regresión lineal

3. Realización de la Regresión Lineal Simple
   En primer lugar se separaron los datos para entrenamiento y prueba:
   - 80 % → entrenamiento: Son los datos que se usarán para aprender la relación entre NO₂ y AQI
   - 20 % → prueba: Son los con datos que no utilizó durante el entrenamiento y se usaran para ver como funciona el modelo
   
   
