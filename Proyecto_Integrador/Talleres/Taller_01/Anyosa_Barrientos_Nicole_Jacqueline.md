# Diseño y análisis estructural de tolva compacta para Kartoffelmachine

# Contexto del proyecto

El presente modelo forma parte del desarrollo del prototipo
**Kartoffelmachine**, un sistema orientado al manejo automatizado de
papas mediante componentes mecánicos.

La tolva compacta desarrollada cumple la función de recibir las papas en
la etapa inicial del proceso, almacenarlas temporalmente y dirigirlas
hacia la zona inferior mediante una geometría inclinada.

El diseño considera:

- Capacidad aproximada para 20 papas medianas.
- Diseño compacto y fabricable.
- Resistencia frente al peso propio y carga del producto.
- Validación mediante simulación estructural en SimScale.

En esta versión del análisis se evaluó el comportamiento de la tolva
utilizando **PLA** como material, con el fin de compararlo frente a los
resultados obtenidos previamente con **acero (Steel)**.

---

# Modelo CAD

El modelo tridimensional fue desarrollado en **Onshape**.

Características:

| Parámetro      | Descripción            |
|----------------|-------------------------|
| Sistema        | Kartoffelmachine        |
| Componente     | Tolva de alimentación   |
| Software CAD   | Onshape                 |
| Geometría      | Tipo embudo              |
| Entrada        | Superior                |
| Salida         | Inferior                |

## Modelo en Onshape

[Ver modelo CAD en Onshape](https://cad.onshape.com/documents/bc39301f747fb6a18b64a2ca/w/2fa2b268fce199383b4f8ac7/e/a4d85209260ef7f4da386311?renderMode=0&uiState=6a9107e85c7f33612a2fdd3a)

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/nicole_onshape_model.png?raw=1" width="800"/>
</p>

---

# Análisis estructural

La evaluación fue realizada mediante **SimScale** utilizando un análisis
estructural estático.

## Simulación

[Ver simulación en SimScale]([[https://www.simscale.com/workbench/?pid=4499940546658918321&rru=d2182d79-83d6-4060-b9a3-3cbf4cab1c8a&sh=1&ci=fac46db1-6586-4c8d-8075-8ad184b23d28&ct=MESH&mt=SIMULATION_RESULT](https://www.simscale.com/workbench/?pid=7623883839998516883&rru=9b311964-5558-43e1-ac6a-c8988f54cf38&ci=03e88ee8-ec97-43b1-bc07-1fef8dfa0d6c&mt=SIMULATION_RESULT&ct=SOLUTION_FIELD)](https://www.simscale.com/workbench/?pid=7623883839998516883&mi=spec:ca080429-a24a-4a33-ac29-93cac2c179b4%2Cservice:SIMULATION%2Cstrategy:1))

---

# Material utilizado

Se asignó **PLA** como material estructural para esta prueba.

| Propiedad             | Valor            |
|------------------------|-------------------|
| Material                | PLA               |
| Modelo                  | Linear elastic    |
| Comportamiento          | Isotrópico        |
| Módulo de Young         | 3.5 × 10⁹ Pa      |
| Coeficiente de Poisson  | 0.36              |
| Densidad                | 1250 kg/m³        |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/nicole_material_pla.png?raw=1" width="800"/>
</p>

---

# Configuración de simulación

## Gravedad

Se consideró el peso propio de la estructura.

| Parámetro   | Valor    |
|-------------|----------|
| Magnitud    | 9.8 m/s² |
| eₓ          | 0 m      |
| e_y         | 0 m      |
| e_z         | -5 m     |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/nicole_gravedad.png?raw=1" width="800"/>
</p>

---

# Condición de fijación

Se aplicó una condición:

## Fixed Support

La fijación restringe los desplazamientos de las zonas de apoyo de la
tolva. Fue asignada sobre 1 cara del modelo (face 14).

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/nicole_fixed_support.png?raw=1" width="800"/>
</p>

---

# Aplicación de fuerza

Para representar la carga generada por aproximadamente 20 papas se
utilizó una fuerza equivalente.

Considerando una masa aproximada:

**F = m × g**

**F ≈ 5 × 9.81 = 49 N**

Se aplicó una carga con factor de seguridad, distribuida sobre 11 caras
del modelo:

## 100 N

| Componente | Valor   |
|------------|---------|
| Fx         | 0 N     |
| Fy         | 0 N     |
| Fz         | -100 N  |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/nicole_force.png?raw=1" width="800"/>
</p>

---

# Mallado

Configuración utilizada:

| Parámetro           | Valor      |
|----------------------|------------|
| Algoritmo            | Standard   |
| Sizing               | Automatic  |
| Curvature            | Automatic  |
| Fineness             | 9.8        |
| Celdas aproximadas   | 23.6k      |
| Nodos aproximados    | 35.2k      |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/nicole_mesh.png?raw=1" width="800"/>
</p>

---

# Resultado de simulación

El análisis permitió evaluar la distribución de esfuerzos mediante el
criterio de Von Mises.

| Parámetro                | Valor              |
|----------------------------|---------------------|
| Von Mises Stress (mínimo) | 2.078 × 10⁻¹ kPa    |
| Von Mises Stress (máximo) | 57.86 kPa           |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/nicole_result.png?raw=1" width="800"/>
</p>

---

# Resumen de resultados

| Parámetro          | Resultado             |
|----------------------|------------------------|
| Tipo de análisis     | Estructural estático  |
| Material              | PLA                    |
| Gravedad              | 9.8 m/s²               |
| Fuerza aplicada       | 100 N                  |
| Soporte                | Fixed Support          |
| Mallado                | Standard               |
| Fineness               | 9.8                    |
| Esfuerzo máx. (Von Mises) | 57.86 kPa          |

---

# Conclusiones

La simulación permitió validar una primera aproximación del diseño de la
tolva compacta para Kartoffelmachine utilizando PLA como material de
referencia.

El análisis permitió comprobar la configuración inicial de:

- Geometría CAD.
- Material.
- Restricciones.
- Carga aplicada.
- Mallado.

Como mejoras futuras se plantea:

- Incorporar espesores reales de fabricación.
- Modelar soldaduras y uniones.
- Integrar el bastidor completo.
- Analizar impactos producidos por la caída de papas.

---

# Justificación

Esta prueba se realizó utilizando **PLA** con el propósito de compararlo
frente a los resultados obtenidos previamente con **acero (Steel)**, ya
que ambos materiales representan dos etapas distintas del desarrollo del
prototipo. El PLA es el material con el que normalmente se fabrica el
prototipo físico mediante impresión 3D: es económico, ligero y fácil de
manufacturar, pero posee un módulo de Young mucho menor (3.5 × 10⁹ Pa
frente a 2.05 × 10¹¹ Pa del acero) y una densidad significativamente
más baja (1250 kg/m³ frente a 7870 kg/m³), lo que se traduce en una
estructura más flexible y con menor resistencia mecánica ante la misma
carga. El acero, en cambio, es el material previsto para una eventual
versión final o industrial de la tolva, ya que ofrece mayor rigidez y
resistencia estructural, a costa de un mayor peso y costo de
fabricación.

Al comparar ambas simulaciones bajo la misma fuerza aplicada (100 N) se
observa que, aunque el esfuerzo de Von Mises resultante en PLA
(57.86 kPa máximo) se mantiene dentro de un rango bajo respecto a su
límite de fluencia, la menor rigidez del material generaría mayores
deformaciones que en la versión de acero. Esta comparación permite
justificar el uso de PLA para validar la geometría y el comportamiento
general del prototipo a bajo costo durante la etapa de pruebas, mientras
que el acero se reserva para confirmar el desempeño estructural de la
versión definitiva de la tolva.

---

# Enlaces del proyecto

## Modelo CAD

[Abrir modelo en Onshape](https://cad.onshape.com/documents/bc39301f747fb6a18b64a2ca/w/2fa2b268fce199383b4f8ac7/e/a4d85209260ef7f4da386311?renderMode=0&uiState=6a9107e85c7f33612a2fdd3a)

## Simulación estructural

[Abrir simulación en SimScale]([https://www.simscale.com/workbench/?pid=4499940546658918321&rru=d2182d79-83d6-4060-b9a3-3cbf4cab1c8a&sh=1&ci=fac46db1-6586-4c8d-8075-8ad184b23d28&ct=MESH&mt=SIMULATION_RESULT](https://www.simscale.com/workbench/?pid=7623883839998516883&mi=spec:ca080429-a24a-4a33-ac29-93cac2c179b4%2Cservice:SIMULATION%2Cstrategy:1))
