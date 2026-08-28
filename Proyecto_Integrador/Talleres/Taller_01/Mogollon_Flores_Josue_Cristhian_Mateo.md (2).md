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
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/onshape_model.png?raw=1" width="800"/>
</p>

---

# Análisis estructural

La evaluación fue realizada mediante **SimScale** utilizando un análisis
estructural estático.

## Simulación

[Ver simulación en SimScale](https://www.simscale.com/workbench/?pid=4499940546658918321&rru=d2182d79-83d6-4060-b9a3-3cbf4cab1c8a&sh=1&ci=fac46db1-6586-4c8d-8075-8ad184b23d28&ct=MESH&mt=SIMULATION_RESULT)

---

# Material utilizado

Se asignó **Steel** como material estructural.

| Propiedad             | Valor            |
|------------------------|-------------------|
| Material                | Steel             |
| Modelo                  | Linear elastic    |
| Comportamiento          | Isotrópico        |
| Módulo de Young         | 2.05 × 10¹¹ Pa    |
| Coeficiente de Poisson  | 0.28              |
| Densidad                | 7870 kg/m³        |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/material.png?raw=1" width="800"/>
</p>

---

# Configuración de simulación

## Gravedad

Se consideró el peso propio de la estructura.

| Parámetro   | Valor              |
|-------------|--------------------|
| Magnitud    | 9.81 m/s²          |
| Dirección   | Vertical negativa  |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/gravedad.png?raw=1" width="800"/>
</p>

---

# Condición de fijación

Se aplicó una condición:

## Fixed Support

La fijación restringe los desplazamientos de las zonas de apoyo de la
tolva.

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/fixed_support.png?raw=1" width="800"/>
</p>

---

# Aplicación de fuerza

Para representar la carga generada por aproximadamente 20 papas se
utilizó una fuerza equivalente.

Considerando una masa aproximada:

**F = m × g**

**F ≈ 5 × 9.81 = 49 N**

Se aplicó una carga con factor de seguridad:

## 100 N

| Componente | Valor   |
|------------|---------|
| Fx         | 0 N     |
| Fy         | -100 N  |
| Fz         | 0 N     |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/force.png?raw=1" width="800"/>
</p>

---

# Mallado

Configuración utilizada:

| Parámetro           | Valor      |
|----------------------|------------|
| Algoritmo            | Standard   |
| Sizing               | Automatic  |
| Fineness             | 8.9        |
| Celdas aproximadas   | 13.6k      |
| Nodos aproximados    | 19.9k      |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/mesh.png?raw=1" width="800"/>
</p>

---

# Resultado de simulación

El análisis permitió evaluar la distribución de esfuerzos mediante el
criterio de Von Mises.

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/result.png?raw=1" width="800"/>
</p>

---

# Resumen de resultados

| Parámetro          | Resultado             |
|----------------------|------------------------|
| Tipo de análisis     | Estructural estático  |
| Material              | Steel                  |
| Gravedad              | 9.81 m/s²              |
| Fuerza aplicada       | 100 N                  |
| Soporte                | Fixed Support          |
| Mallado                | Standard               |
| Fineness               | 8.9                    |

---

# Conclusiones

La simulación permitió validar una primera aproximación del diseño de la
tolva compacta para Kartoffelmachine.

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

# Enlaces del proyecto

## Modelo CAD

[Abrir modelo en Onshape](https://cad.onshape.com/documents/bc39301f747fb6a18b64a2ca/w/2fa2b268fce199383b4f8ac7/e/a4d85209260ef7f4da386311?renderMode=0&uiState=6a9107e85c7f33612a2fdd3a)

## Simulación estructural

[Abrir simulación en SimScale](https://www.simscale.com/workbench/?pid=4499940546658918321&rru=d2182d79-83d6-4060-b9a3-3cbf4cab1c8a&sh=1&ci=fac46db1-6586-4c8d-8075-8ad184b23d28&ct=MESH&mt=SIMULATION_RESULT)
