# Segunda simulación estructural del módulo en V

## Modificación de las condiciones de carga

Luego de realizar una primera simulación estructural del módulo en V de **Kartoffelmachine**, se realizó una segunda evaluación modificando las fuerzas aplicadas sobre el sistema.

El objetivo de esta nueva simulación fue observar el comportamiento estructural del módulo frente a cargas mayores y considerar también una fuerza adicional aplicada sobre el rodillo inferior.

El modelo utilizado corresponde al mismo diseño desarrollado previamente en **Onshape**, compuesto por:

- Base estructural.
- Dos guías inclinadas en V.
- Dos soportes.
- Rodillo inferior.
- Eje del rodillo.

### Modelo utilizado

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/Onshape_Modulo_V1.png?raw=1" width="800"/>
</p>

<p align="center">
  <em>Figura 1. Modelo del módulo en V utilizado para la segunda simulación.</em>
</p>

---

## Tipo de análisis

La evaluación fue realizada en **SimScale** mediante un análisis:

### Static Structural

Este tipo de análisis permite estudiar el desplazamiento y comportamiento mecánico de la estructura cuando se encuentra sometida a fuerzas constantes.

---

# Material utilizado

Se mantuvo **PLA** como material para todos los componentes del modelo.

Las principales propiedades utilizadas fueron:

| Propiedad | Valor |
|---|---:|
| Material | PLA |
| Módulo de Young | 3.5 × 10⁹ Pa |
| Coeficiente de Poisson | 0.36 |
| Densidad | 1250 kg/m³ |
| Modelo del material | Elasticidad lineal |
| Comportamiento | Isotrópico |

### Asignación del material

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_PLA1.png?raw=1" width="800"/>
</p>

<p align="center">
  <em>Figura 2. Material PLA asignado a los cuatro sólidos del módulo.</em>
</p>

El material fue aplicado a:

- Part 1.
- Part 2.
- Part 3.
- Part 4.

---

# Configuración de la gravedad

Se mantuvo activada la gravedad con una magnitud de:

**9.81 m/s²**

La dirección fue configurada hacia la zona inferior del modelo.

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Gravedad1.png?raw=1" width="800"/>
</p>

<p align="center">
  <em>Figura 3. Configuración de la gravedad utilizada en la segunda simulación.</em>
</p>

Esta condición permite considerar el peso propio de los componentes durante el análisis estructural.

---

# Condición de fijación

Para mantener el módulo unido a una estructura rígida se utilizó nuevamente:

### Fixed Support 1

La condición fue aplicada sobre las caras correspondientes a la base del sistema.

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Fixed_Support1.png?raw=1" width="800"/>
</p>

<p align="center">
  <em>Figura 4. Condición Fixed Support aplicada sobre la base.</em>
</p>

Esta condición impide el desplazamiento de la base durante la aplicación de las fuerzas.

---

# Aplicación de fuerzas

En esta segunda simulación se utilizaron **tres fuerzas principales**:

- Force 2.
- Force 3.
- Force 4.

A diferencia de la simulación anterior, las cargas aplicadas sobre las guías fueron incrementadas y se añadió una carga adicional sobre el rodillo.

---

## Force 2

La primera fuerza fue aplicada sobre una de las guías del módulo.

Los componentes utilizados fueron:

| Componente | Valor |
|---|---:|
| Fx | 0 N |
| Fy | 0 N |
| Fz | **-15 N** |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Force_2_1.png?raw=1" width="800"/>
</p>

<p align="center">
  <em>Figura 5. Force 2 de 15 N aplicada sobre una de las guías.</em>
</p>

La fuerza se encuentra orientada verticalmente hacia abajo.

---

## Force 3

Sobre la guía opuesta se aplicó una fuerza de la misma magnitud.

Los componentes utilizados fueron:

| Componente | Valor |
|---|---:|
| Fx | 0 N |
| Fy | 0 N |
| Fz | **-15 N** |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Force_3_1.png?raw=1" width="800"/>
</p>

<p align="center">
  <em>Figura 6. Force 3 de 15 N aplicada sobre la segunda guía.</em>
</p>

La utilización de cargas iguales en ambas guías permite analizar el comportamiento del soporte V frente a una carga distribuida de manera aproximadamente simétrica.

---

## Force 4

También se incorporó una tercera fuerza sobre el **rodillo inferior**.

Los componentes utilizados fueron:

| Componente | Valor |
|---|---:|
| Fx | 0 N |
| Fy | 0 N |
| Fz | **-50 N** |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Force_4_1.png?raw=1" width="800"/>
</p>

<p align="center">
  <em>Figura 7. Force 4 de 50 N aplicada sobre el rodillo inferior.</em>
</p>

Esta carga adicional permite evaluar el comportamiento del módulo cuando el rodillo recibe una carga vertical considerablemente mayor que las aplicadas individualmente sobre las paredes de la V.

---

# Resumen de las fuerzas

| Fuerza | Fx | Fy | Fz | Componente |
|---|---:|---:|---:|---|
| Force 2 | 0 N | 0 N | **-15 N** | Guía izquierda |
| Force 3 | 0 N | 0 N | **-15 N** | Guía derecha |
| Force 4 | 0 N | 0 N | **-50 N** | Rodillo |

La carga externa total aplicada verticalmente corresponde a:

**15 N + 15 N + 50 N = 80 N**

Por lo tanto, el modelo fue evaluado bajo una carga externa total aproximada de:

## **80 N**

además del efecto producido por la gravedad.

---

# Mallado

En esta simulación se utilizó una malla menos fina que en la primera evaluación.

La reducción de la finura permitió disminuir considerablemente la cantidad de nodos y el costo computacional del análisis.

Los parámetros utilizados fueron:

| Parámetro | Configuración |
|---|---:|
| Algoritmo | Standard |
| Sizing | Automatic |
| Fineness | **3** |
| Celdas aproximadas | **3.9k** |
| Nodos aproximados | **7.7k** |

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Mallado1.png?raw=1" width="800"/>
</p>

<p align="center">
  <em>Figura 8. Malla utilizada para la segunda simulación estructural.</em>
</p>

Esta configuración permitió ejecutar la simulación con un costo computacional considerablemente menor.

---

# Optimización de la malla

Durante pruebas anteriores se utilizó una malla excesivamente fina, llegando aproximadamente a:

- 5 millones de nodos.
- Elementos de segundo orden.

Esta configuración produjo un error por falta de memoria durante la ejecución.

SimScale indicó:

`The machine ran out of memory`

Para solucionar este inconveniente se redujo la finura global de la malla.

La nueva configuración presentó aproximadamente:

- **3900 celdas.**
- **7700 nodos.**

Esto permitió ejecutar correctamente el nuevo análisis estructural.

---

# Ejecución de la simulación

La simulación correspondiente a estas nuevas condiciones fue ejecutada como:

### Static — Run 4

La ejecución finalizó correctamente.

Esto permitió obtener los campos de solución y analizar el desplazamiento producido por las nuevas cargas.

---

# Resultado de desplazamiento

El principal parámetro analizado fue:

## Displacement Z

<p align="center">
  <img src="https://github.com/Dylan200-7/PI_Equipo_10/blob/main/Recursos/Im%C3%A1genes/SimScale_Desplazamiento1.png?raw=1" width="800"/>
</p>

<p align="center">
  <em>Figura 9. Distribución del desplazamiento vertical obtenida en Run 4.</em>
</p>

De acuerdo con la escala mostrada por SimScale, el desplazamiento mínimo obtenido fue aproximadamente:

**−7.956 × 10⁻⁵ m**

Convirtiendo este valor a milímetros:

**−7.956 × 10⁻⁵ m × 1000**

se obtiene:

## **−0.07956 mm**

Por lo tanto, el desplazamiento vertical máximo hacia abajo observado fue aproximadamente:

## **0.080 mm**

El extremo positivo de la escala alcanzó aproximadamente:

**4.025 × 10⁻⁵ m**

equivalente a:

**0.04025 mm**

---

# Distribución del desplazamiento

En los resultados se observa que el desplazamiento no se distribuye de manera uniforme sobre toda la estructura.

Las zonas próximas a los soportes presentan menores desplazamientos, mientras que determinadas regiones de las guías muestran mayores variaciones.

La escala de colores permite identificar visualmente las regiones con diferentes magnitudes de desplazamiento.

Las zonas azules representan los desplazamientos negativos de mayor magnitud, mientras que las zonas amarillas y rojas corresponden a valores cercanos al extremo positivo de la escala.

---

# Resumen de resultados

| Parámetro | Resultado |
|---|---:|
| Material | PLA |
| Tipo de análisis | Estructural estático |
| Simulación | Run 4 |
| Force 2 | **15 N** |
| Force 3 | **15 N** |
| Force 4 | **50 N** |
| Carga externa total | **80 N** |
| Gravedad | 9.81 m/s² |
| Fineness de malla | 3 |
| Celdas | ≈ 3.9k |
| Nodos | ≈ 7.7k |
| Resultado evaluado | Displacement Z |
| Desplazamiento negativo máx. | **≈ 0.080 mm** |
| Desplazamiento positivo máx. | **≈ 0.040 mm** |

---

# Comparación con la primera simulación

En la simulación inicial se utilizaron cargas menores sobre las guías.

En esta segunda simulación se incrementaron las fuerzas y también se añadió una carga adicional sobre el rodillo.

| Configuración | Primera simulación | Segunda simulación |
|---|---:|---:|
| Fuerza guía 1 | 5 N vertical + componente lateral | **15 N vertical** |
| Fuerza guía 2 | 5 N vertical + componente lateral | **15 N vertical** |
| Fuerza sobre rodillo | No incluida | **50 N** |
| Carga externa total aprox. | Menor | **80 N** |
| Finura de malla | 8.5 | **3** |
| Desplazamiento Z máx. observado | ≈ 0.30 mm | **≈ 0.080 mm** |

La diferencia de desplazamiento entre ambas simulaciones no debe interpretarse únicamente a partir de la magnitud de las fuerzas, debido a que también se modificó considerablemente la discretización de la malla y la forma de aplicación de las cargas.

Por ello, ambas simulaciones corresponden a escenarios numéricos diferentes.

---

# Interpretación

La segunda simulación permitió comprobar el comportamiento del módulo frente a una condición de carga más elevada.

A pesar de aplicar aproximadamente **80 N de carga externa total**, el desplazamiento vertical máximo obtenido se mantuvo en un orden inferior a:

**0.1 mm**

El resultado obtenido fue aproximadamente:

## **0.080 mm**

Esto indica preliminarmente que el modelo presenta una elevada rigidez bajo las condiciones utilizadas.

Sin embargo, el resultado debe interpretarse como una evaluación preliminar, ya que todavía existen simplificaciones en la representación del sistema real.

---

# Simplificaciones

La segunda simulación continúa siendo una representación simplificada del mecanismo real.

No se incluyeron:

- La geometría real de una papa.
- Contacto físico entre papa y guías.
- Fricción papa-rodillo.
- Movimiento rotacional del rodillo.
- Torque producido por un motor.
- Rodamientos.
- Vibraciones.
- Movimiento de la faja.
- Impactos durante la alimentación.
- Tolva.
- Cámara.
- Componentes electrónicos.

Las cargas fueron representadas mediante fuerzas estáticas equivalentes.

---

# Conclusión

Se realizó una segunda simulación estructural del módulo en V de **Kartoffelmachine**, modificando las cargas utilizadas inicialmente.

En esta nueva configuración se aplicaron:

- **15 N** sobre la primera guía.
- **15 N** sobre la segunda guía.
- **50 N** sobre el rodillo inferior.

Esto representa una carga externa total aproximada de:

## **80 N**

Para evitar problemas de memoria observados durante pruebas anteriores, se optimizó la malla reduciendo la finura a **3**, obteniendo aproximadamente **3900 celdas y 7700 nodos**.

La simulación `Run 4` finalizó correctamente.

El desplazamiento vertical máximo hacia abajo obtenido fue aproximadamente:

## **0.080 mm**

Este resultado indica preliminarmente que la estructura presenta una deformación reducida bajo las condiciones de carga simuladas.

Las siguientes evaluaciones deberán incorporar progresivamente condiciones más cercanas al funcionamiento real, principalmente el contacto con una papa, la fricción con el rodillo y el movimiento generado durante la rotación.