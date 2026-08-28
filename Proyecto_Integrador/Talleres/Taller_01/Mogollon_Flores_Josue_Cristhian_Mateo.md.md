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

# Diseño de la pieza

El modelo tridimensional fue desarrollado en **Onshape** como parte del
sistema mecánico de **Kartoffelmachine**.

La tolva tiene como función recibir las papas en la etapa inicial del
proceso y guiarlas hacia la zona inferior del sistema mediante una
geometría tipo embudo.

Características principales:

  Característica       Descripción
  -------------------- ------------------------
  Tipo de componente   Tolva de alimentación
  Sistema              Kartoffelmachine
  Software CAD         Onshape
  Geometría            Tipo embudo
  Entrada              Superior abierta
  Salida               Inferior para descarga
  Capacidad estimada   20 papas medianas

## Modelo CAD

[Ver modelo en
Onshape](https://cad.onshape.com/documents/bc39301f747fb6a18b64a2ca/w/2fa2b268fce199383b4f8ac7/e/a4d85209260ef7f4da386311?renderMode=0&uiState=6a9107e85c7f33612a2fdd3a)

```{=html}
<p align="center">
```
`<img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/Onshape_Tolva.png?raw=1" width="800"/>`{=html}
```{=html}
</p>
```
```{=html}
<p align="center">
```
`<em>`{=html}Figura 1. Modelo CAD de la tolva compacta desarrollada en
Onshape.`</em>`{=html}
```{=html}
</p>
```

------------------------------------------------------------------------

# Análisis estructural

El modelo fue evaluado en **SimScale** mediante un análisis estructural
estático.

[Ver simulación en
SimScale](https://www.simscale.com/workbench/?pid=4499940546658918321&rru=d2182d79-83d6-4060-b9a3-3cbf4cab1c8a&sh=1&ci=fac46db1-6586-4c8d-8075-8ad184b23d28&ct=MESH&mt=SIMULATION_RESULT)

------------------------------------------------------------------------

# Material utilizado

Para la simulación se utilizó **Steel** como material estructural.

  Propiedad                           Valor
  ------------------------ ----------------
  Material                            Steel
  Modelo del material        Linear elastic
  Comportamiento                 Isotrópico
  Módulo de Young            2.05 × 10¹¹ Pa
  Coeficiente de Poisson               0.28
  Densidad                       7870 kg/m³

```{=html}
<p align="center">
```
`<img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Material_Tolva.png?raw=1" width="800"/>`{=html}
```{=html}
</p>
```
```{=html}
<p align="center">
```
`<em>`{=html}Figura 2. Asignación del material Steel en
SimScale.`</em>`{=html}
```{=html}
</p>
```

------------------------------------------------------------------------

# Configuración de simulación

## Gravedad

Se incorporó la gravedad para considerar el peso propio de la
estructura.

  Parámetro                     Valor
  ----------- -----------------------
  Magnitud                  9.81 m/s²
  Dirección     Eje vertical negativo

```{=html}
<p align="center">
```
`<img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Gravedad_Tolva.png?raw=1" width="800"/>`{=html}
```{=html}
</p>
```

------------------------------------------------------------------------

## Condición de fijación

Para representar el apoyo de la tolva dentro del sistema se configuró:

### Fixed Support

La condición restringe los desplazamientos de la zona seleccionada.

```{=html}
<p align="center">
```
`<img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Fixed_Support_Tolva.png?raw=1" width="800"/>`{=html}
```{=html}
</p>
```

------------------------------------------------------------------------

# Aplicación de fuerzas

Para representar la carga generada por aproximadamente 20 papas medianas
se aplicó una fuerza equivalente.

Considerando una masa aproximada de 5 kg:

**F = m × g**

**F ≈ 5 × 9.81 = 49 N**

Para incluir un margen de seguridad se utilizó una carga de:

## 100 N

Configuración:

  Componente      Valor
  ------------ --------
  Fx                0 N
  Fy             -100 N
  Fz                0 N

```{=html}
<p align="center">
```
`<img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Force_Tolva.png?raw=1" width="800"/>`{=html}
```{=html}
</p>
```

------------------------------------------------------------------------

# Generación de malla

La malla se generó utilizando:

  Parámetro                  Valor
  -------------------- -----------
  Algoritmo               Standard
  Sizing                 Automatic
  Fineness                     8.9
  Celdas aproximadas         13.6k
  Nodos aproximados          19.9k

```{=html}
<p align="center">
```
`<img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Mallado_Tolva.png?raw=1" width="800"/>`{=html}
```{=html}
</p>
```

------------------------------------------------------------------------

# Resultado de la simulación

El resultado principal evaluado corresponde a la distribución de
esfuerzos mediante el criterio de Von Mises.

```{=html}
<p align="center">
```
`<img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Result_Tolva.png?raw=1" width="800"/>`{=html}
```{=html}
</p>
```

------------------------------------------------------------------------

# Resumen del análisis

  Parámetro                           Resultado
  ---------------------- ----------------------
  Tipo de análisis         Estructural estático
  Material                                Steel
  Gravedad                            9.81 m/s²
  Fuerza aplicada                         100 N
  Condición de soporte            Fixed Support
  Mallado                              Standard
  Fineness                                  8.9

------------------------------------------------------------------------

# Conclusiones

El modelo desarrollado representa una primera aproximación de una tolva
compacta para el prototipo **Kartoffelmachine**.

La simulación permitió validar la configuración inicial del modelo CAD,
material, restricciones y cargas aplicadas.

Como siguientes etapas de mejora se plantea:

-   Incorporar espesores reales de fabricación.
-   Modelar uniones mecánicas y soldaduras.
-   Integrar el bastidor completo.
-   Realizar análisis dinámicos considerando la caída e impacto de
    papas.

------------------------------------------------------------------------

# Enlaces del proyecto

## Modelo CAD

[**Abrir modelo en
Onshape**](https://cad.onshape.com/documents/bc39301f747fb6a18b64a2ca/w/2fa2b268fce199383b4f8ac7/e/a4d85209260ef7f4da386311?renderMode=0&uiState=6a9107e85c7f33612a2fdd3a)

## Simulación estructural

[**Abrir simulación en
SimScale**](https://www.simscale.com/workbench/?pid=4499940546658918321&rru=d2182d79-83d6-4060-b9a3-3cbf4cab1c8a&sh=1&ci=fac46db1-6586-4c8d-8075-8ad184b23d28&ct=MESH&mt=SIMULATION_RESULT)
