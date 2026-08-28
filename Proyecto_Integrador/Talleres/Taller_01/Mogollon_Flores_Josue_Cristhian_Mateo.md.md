# Diseño y análisis estructural de tolva compacta para Kartoffelmachine

# Contexto del proyecto

El presente modelo forma parte del desarrollo del prototipo
**Kartoffelmachine**, un sistema orientado al manejo automatizado de
papas mediante componentes mecánicos diseñados para controlar el flujo y
posicionamiento del producto.

Dentro del funcionamiento del sistema, la etapa inicial requiere un
mecanismo capaz de recibir las papas, almacenarlas temporalmente y
dirigirlas hacia la zona de procesamiento de manera controlada.

Para cumplir esta función se desarrolló una **tolva compacta de
alimentación**, cuyo objetivo es permitir el ingreso del producto por la
parte superior y conducirlo hacia una salida inferior mediante una
geometría inclinada.

El diseño busca cumplir con los siguientes criterios:

-   Diseño compacto y transportable.
-   Capacidad aproximada para 20 papas medianas.
-   Geometría simple para facilitar su fabricación.
-   Resistencia estructural frente al peso propio y la carga del
    producto.
-   Evaluación mediante simulación estructural utilizando elementos
    finitos.

------------------------------------------------------------------------

# Objetivo del análisis

El objetivo de esta primera evaluación es analizar el comportamiento
estructural de la tolva mediante un estudio estático realizado en
**SimScale**, considerando:

-   Peso propio de la estructura.
-   Carga equivalente generada por las papas almacenadas.
-   Condiciones de soporte del sistema.

El análisis permite identificar zonas críticas y obtener una primera
validación del diseño antes de una futura fabricación física.

------------------------------------------------------------------------

# Modelo CAD

El modelo tridimensional fue desarrollado en **Onshape** considerando
una tolva abierta superiormente para la alimentación de papas y una
salida inferior para la descarga controlada del producto.

Características principales:

-   Tolva compacta.
-   Geometría tipo embudo.
-   Sección superior de alimentación.
-   Zona inferior de descarga.

## Modelo en Onshape

[Ver modelo CAD en
Onshape](https://cad.onshape.com/documents/bc39301f747fb6a18b64a2ca/w/2fa2b268fce199383b4f8ac7/e/a4d85209260ef7f4da386311?renderMode=0&uiState=6a9107e85c7f33612a2fdd3a)

![Modelo CAD](images/onshape_model.png)

------------------------------------------------------------------------

# Simulación estructural

La simulación fue realizada en **SimScale** mediante un análisis
estático estructural.

## Simulación en SimScale

[Ver simulación en
SimScale](https://www.simscale.com/workbench/?pid=4499940546658918321&rru=d2182d79-83d6-4060-b9a3-3cbf4cab1c8a&sh=1&ci=fac46db1-6586-4c8d-8075-8ad184b23d28&ct=MESH&mt=SIMULATION_RESULT)

------------------------------------------------------------------------

# Material asignado

Se utilizó acero como material estructural para la simulación.

  Propiedad                            Valor
  ------------------------- ----------------
  Material                             Steel
  Modelo                      Linear elastic
  Dependencia direccional          Isotropic
  Módulo de Young             2.05 × 10¹¹ Pa
  Coeficiente de Poisson                0.28
  Densidad                        7870 kg/m³

![Material](images/material.png)

------------------------------------------------------------------------

# Condiciones de simulación

## Gravedad

Se consideró el peso propio de la estructura mediante una aceleración
gravitacional.

  Parámetro                     Valor
  ----------- -----------------------
  Magnitud                  9.81 m/s²
  Dirección     Eje vertical negativo

![Gravedad](images/gravedad.png)

------------------------------------------------------------------------

## Restricción fija

Se aplicó una condición **Fixed Support** en las zonas de apoyo de la
estructura para restringir los desplazamientos durante el análisis.

![Fixed Support](images/fixed_support.png)

------------------------------------------------------------------------

# Aplicación de carga

Para representar la carga generada por aproximadamente 20 papas medianas
se aplicó una fuerza equivalente.

Considerando una masa aproximada de 5 kg:

F = m × g

F ≈ 5 × 9.81 = 49 N

Para incluir un margen de seguridad se utilizó una carga de:

**100 N**

Configuración:

  Componente      Valor
  ------------ --------
  Fx                0 N
  Fy             -100 N
  Fz                0 N

![Fuerza aplicada](images/force.png)

------------------------------------------------------------------------

# Mallado

La generación de malla se realizó con los siguientes parámetros:

  Parámetro                Valor
  ------------------ -----------
  Algoritmo             Standard
  Sizing               Automatic
  Fineness                   8.9
  Celdas generadas         13.6k
  Nodos generados          19.9k

![Mallado](images/mesh.png)

------------------------------------------------------------------------

# Resultados

El análisis permitió obtener la distribución de esfuerzos mediante el
criterio de Von Mises y evaluar la respuesta estructural de la tolva
frente a las cargas aplicadas.

![Resultado simulación](images/result.png)

------------------------------------------------------------------------

# Conclusiones

El modelo desarrollado representa una primera aproximación de una tolva
compacta para el prototipo Kartoffelmachine.

La simulación permitió validar la configuración inicial del modelo CAD,
material, restricciones y cargas aplicadas.

Como siguientes etapas de mejora se plantea:

-   Incorporar espesores reales de fabricación.
-   Modelar uniones mecánicas y soldaduras.
-   Integrar el bastidor completo.
-   Realizar análisis dinámicos considerando el impacto de caída de
    papas.
