# 🥔 Taller 01 — Modelado y Simulación del Módulo en V

## Kartoffelmachine

En este taller se desarrolló el modelado mecánico inicial de uno de los módulos principales del proyecto **Kartoffelmachine**, específicamente el sistema encargado de posicionar y permitir la rotación de cada papa durante su recorrido por la faja transportadora.

El diseño fue realizado inicialmente en **Onshape** y posteriormente fue importado a **SimScale** para realizar una primera evaluación mediante análisis estructural estático.

---

# 1. Objetivo

El objetivo de esta etapa fue diseñar y analizar un módulo mecánico capaz de mantener una papa centrada durante su desplazamiento y permitir posteriormente su rotación mediante un rodillo inferior.

El módulo está compuesto principalmente por:

- Una base estructural.
- Dos guías inclinadas formando una V.
- Un rodillo inferior.
- Un eje central para el rodillo.
- Dos soportes estructurales.
- Un sistema de fijación hacia la base.

Este módulo posteriormente será repetido varias veces a lo largo de una faja transportadora, de manera que cada papa pueda ocupar su propia posición durante el proceso de inspección.

---

# 2. Modelado en Onshape

## 2.1 Diseño inicial

El modelado comenzó en **Onshape**, utilizando un `Part Studio`.

Inicialmente se crearon las siguientes piezas:

1. Base.
2. Guía izquierda.
3. Guía derecha.
4. Rodillo inferior.
5. Eje del rodillo.

Las dos guías fueron colocadas con una inclinación simétrica para formar una geometría en V.

Esta geometría permite mantener la papa centrada y evita que se desplace lateralmente durante el movimiento.

---

## 2.2 Rodillo inferior

En la parte inferior de la V se colocó un rodillo cilíndrico.

Este rodillo tiene como función futura generar la rotación de la papa.

La idea es que el rodillo sea accionado mediante un motor y que posteriormente cuente con un recubrimiento de mayor fricción, como:

- Goma.
- Caucho.
- Silicona.
- TPU.

Esto permitirá transferir el movimiento del rodillo hacia la superficie de la papa.

---

## 2.3 Incorporación de soportes

Durante el desarrollo inicial se detectó qu e las dos paredes de la V se encontraban separadas de la base y no tenían una conexión estructural adecuada.

Esto podía producir problemas durante el análisis estructural, ya que las cargas aplicadas sobre las guías no tenían una trayectoria adecuada hacia la base.

Para solucionar este problema se añadieron dos soportes estructurales.

Los soportes permiten transmitir las cargas desde las guías hacia la base.

### Modelo final desarrollado en Onshape

![Modelo del módulo V desarrollado en Onshape](../../Recursos/Imágenes/Onshape_Modulo_V.png)

El modelo incluye:

- Base.
- Guía izquierda.
- Guía derecha.
- Rodillo.
- Eje.
- Soporte izquierdo.
- Soporte derecho.

---

# 3. Importación a SimScale

Una vez finalizado el modelo en Onshape, se importó la geometría hacia **SimScale**.

El objetivo fue realizar un análisis estructural estático para observar el comportamiento del módulo frente a cargas equivalentes al peso y presión ejercida por una papa.

---

# 4. Problemas encontrados durante la importación

Durante la primera importación se presentó un error relacionado con un cuerpo superficial.

SimScale detectó una geometría denominada:

`Surface 1`

Esta pieza tenía:

- Área.
- Cero volumen.

Por lo tanto, era considerada una superficie y no un sólido tridimensional.

El análisis estructural utilizado requería cuerpos sólidos.

Para solucionar el problema se eliminó la superficie que no era necesaria para el análisis.

Después de esta modificación, el modelo quedó compuesto únicamente por sólidos.

---

# 5. Configuración del análisis

Se utilizó un análisis:

## Static Structural

Este análisis permite estudiar el comportamiento de una estructura frente a cargas constantes.

El objetivo principal fue evaluar:

- Desplazamiento.
- Deformación.
- Comportamiento de las guías.
- Transmisión de cargas hacia la base.

---

# 6. Material

Se seleccionó **PLA** como material preliminar.

La elección se realizó considerando que el prototipo podría fabricarse parcialmente mediante impresión 3D.

Los parámetros utilizados fueron:

| Propiedad | Valor |
|---|---:|
| Módulo de Young | 3.5 × 10⁹ Pa |
| Coeficiente de Poisson | 0.36 |
| Densidad | 1250 kg/m³ |
| Comportamiento | Elástico lineal |
| Dependencia | Isotrópica |

El material fue asignado a todos los sólidos del modelo.

### Asignación de PLA

![Asignación de material PLA en SimScale](../../Recursos_Imagenes/SimScale_PLA.png)

---

# 7. Gravedad

Se activó la gravedad dentro del modelo.

Se utilizó una magnitud de:

**9.81 m/s²**

orientada hacia la dirección vertical negativa.

### Configuración de gravedad

![Configuración de gravedad](../../Recursos_Imagenes/SimScale_Gravedad.png)

La gravedad permite considerar el peso propio de los componentes durante la simulación.

---

# 8. Fixed Support

Para representar que la base del módulo estará sujeta al chasis principal de Kartoffelmachine, se utilizó una condición:

## Fixed Support

Esta condición restringe completamente el movimiento de las caras seleccionadas.

### Configuración del Fixed Support

![Fixed Support aplicado en la base](../../Recursos_Imagenes/SimScale_Fixed_Support.png)

Esta condición representa que la base estará firmemente unida a la estructura principal.

---

# 9. Aplicación de fuerzas

Para representar aproximadamente la carga ejercida por una papa sobre ambas guías se utilizaron dos fuerzas.

Estas fuerzas fueron aplicadas sobre las superficies inclinadas de la V.

---

## 9.1 Force 2

La primera fuerza fue aplicada sobre una de las paredes.

Los valores utilizados fueron:

| Componente | Valor |
|---|---:|
| Fx | 0 N |
| Fy | 5 N |
| Fz | -5 N |

### Force 2

![Force 2 aplicada sobre una guía](../../Recursos_Imagenes/SimScale_Force_2.png)

La componente vertical negativa representa una carga dirigida hacia abajo.

La componente lateral representa la fuerza ejercida hacia uno de los lados de la V.

---

## 9.2 Force 3

En la guía opuesta se utilizó una fuerza similar, pero con dirección lateral contraria.

Los valores fueron:

| Componente | Valor |
|---|---:|
| Fx | 0 N |
| Fy | -5 N |
| Fz | -5 N |

### Force 3

![Force 3 aplicada sobre la otra guía](../../Recursos_Imagenes/SimScale_Force_3.png)

De esta manera se representa aproximadamente una distribución simétrica de carga sobre ambas superficies.

---

# 10. Contactos entre componentes

Durante las primeras pruebas se detectó que algunas partes del modelo no se encontraban correctamente conectadas.

Esto provocaba que SimScale identificara algunos componentes como cuerpos independientes sin interacción.

Para solucionar este problema se realizaron modificaciones en Onshape y se incorporaron soportes físicos.

Después de actualizar el modelo se configuraron los contactos necesarios entre los componentes.

Finalmente, SimScale detectó:

**Contacts (3)**

Esto permitió que las fuerzas se transmitieran correctamente entre las piezas.

---

# 11. Mallado

Una vez configurados:

- Material.
- Gravedad.
- Fuerzas.
- Contactos.
- Fixed Support.

se procedió a generar la malla.

Se utilizó:

| Parámetro | Configuración |
|---|---|
| Algorithm | Standard |
| Sizing | Automatic |
| Fineness | 8.5 |

### Mallado del módulo

![Mallado generado en SimScale](../../Recursos_Imagenes/SimScale_Mallado.png)

La malla obtenida contó aproximadamente con:

- **3.4 millones de celdas**
- **5 millones de nodos**

La geometría fue dividida en numerosos elementos pequeños para permitir el cálculo mediante elementos finitos.

---

# 12. Ejecución

Una vez configurado el modelo se ejecutó:

## Static — Run 1

La simulación finalizó correctamente.

También se confirmó que la generación de la malla terminó sin errores.

---

# 13. Resultado de desplazamiento

El principal resultado evaluado inicialmente fue:

## Displacement Z

Este parámetro representa el desplazamiento vertical de la estructura.

### Resultado obtenido

![Resultado de desplazamiento vertical](../../Recursos_Imagenes/SimScale_Desplazamiento.png)

La escala muestra aproximadamente un desplazamiento mínimo de:

**−2.984 × 10⁻⁴ m**

Al convertirlo a milímetros:

**−2.984 × 10⁻⁴ m × 1000**

Resultado:

**≈ −0.2984 mm**

Por lo tanto, el desplazamiento vertical máximo aproximado fue:

## 0.30 mm

También se observa un desplazamiento positivo máximo cercano a:

**2.006 × 10⁻⁵ m**

equivalente aproximadamente a:

**0.020 mm**

---

# 14. Interpretación

Los resultados muestran que las zonas más alejadas de los soportes presentan un mayor desplazamiento.

Esto es coherente con el comportamiento esperado de una placa sometida a carga.

El desplazamiento máximo obtenido fue aproximadamente:

**0.30 mm**

Este valor es pequeño en comparación con las dimensiones generales del módulo.

Por lo tanto, de manera preliminar, el diseño presenta una rigidez suficiente para continuar con el desarrollo del prototipo.

Sin embargo, este resultado no debe considerarse todavía como una validación definitiva del sistema final.

---

# 15. Simplificaciones realizadas

Para esta primera simulación se realizaron varias simplificaciones.

No se incorporaron todavía:

- La papa como cuerpo físico.
- Fricción entre papa y rodillo.
- Movimiento del rodillo.
- Motor.
- Torque.
- Movimiento de la faja.
- Tolva.
- Cámara.
- Raspberry Pi.
- Sistema de separación.
- Impactos producidos por la caída de las papas.

La carga ejercida por la papa fue representada mediante fuerzas equivalentes sobre las paredes de la V.

El objetivo de esta etapa fue únicamente evaluar preliminarmente el comportamiento estructural del módulo.

---

# 16. Problemas encontrados y soluciones

Durante el desarrollo se identificaron distintos problemas.

| Problema | Causa | Solución |
|---|---|---|
| Sheet bodies detected | Existía una superficie sin volumen | Se eliminó `Surface 1` |
| Piezas sin interacción | Algunas piezas no tenían contactos | Se configuraron contactos |
| Guías sin conexión con la base | El diseño inicial no tenía soportes | Se añadieron soportes en Onshape |
| Simulación no ejecutaba correctamente | Había cuerpos estructuralmente aislados | Se corrigió la geometría |
| Necesidad de representar la carga de una papa | La papa no se modeló como cuerpo sólido | Se utilizaron fuerzas equivalentes |
| Diseño inicialmente poco fabricable | Las paredes en V parecían suspendidas | Se incorporaron soportes estructurales |

---

# 17. Evolución del diseño

El modelo fue modificándose durante el proceso de simulación.

Inicialmente estaba compuesto principalmente por:

- Base.
- Dos placas en V.
- Rodillo.

Posteriormente se añadieron soportes que conectan las placas inclinadas con la base.

Esto permitió obtener una geometría más:

- Realista.
- Estructuralmente coherente.
- Fabricable.
- Compatible con el análisis en SimScale.

El proceso de simulación también ayudó a identificar problemas que no eran evidentes únicamente mediante la visualización del modelo.

---

# 18. Integración con Kartoffelmachine

El módulo desarrollado representa una sola posición para una papa.

El sistema completo contempla el uso de múltiples módulos distribuidos sobre una faja transportadora.

Cada papa se ubicará en una V individual.

Posteriormente se integrarán:

- Faja transportadora.
- Varias posiciones en V.
- Tolva.
- Cámara de reconocimiento.
- Iluminación.
- Raspberry Pi.
- Modelo de visión artificial.
- Motor de rotación.
- Sistema de separación.

El rodillo inferior permitirá que la papa cambie de orientación mientras avanza.

La cámara podrá capturar múltiples vistas y posteriormente el sistema de visión artificial determinará si la papa corresponde a una categoría:

- Buena.
- Mala.

---

# 19. Trabajo futuro

Como siguiente etapa se plantea:

1. Modelar la faja transportadora completa.
2. Repetir el módulo en V varias veces.
3. Diseñar la tolva.
4. Incorporar el soporte de la cámara.
5. Incorporar el motor del rodillo.
6. Definir el mecanismo de transmisión.
7. Analizar la rotación de la papa.
8. Evaluar la interacción entre papa y rodillo.
9. Incorporar el sistema de clasificación final.
10. Integrar todos los componentes en un único modelo.

---

# 20. Conclusión

Se desarrolló satisfactoriamente un primer modelo mecánico del módulo de posicionamiento y rotación de papas utilizando **Onshape**.

El diseño está compuesto por una geometría en V y un rodillo inferior que permitirá posteriormente generar la rotación de cada papa.

Durante el desarrollo se identificó la necesidad de añadir soportes que conectaran las guías inclinadas con la base, permitiendo obtener una estructura más realista y físicamente construible.

Posteriormente el modelo fue importado a **SimScale**, donde se configuró un análisis estructural estático.

Se definieron:

- Material PLA.
- Gravedad.
- Fuerzas.
- Fixed Support.
- Contactos.
- Mallado.
- Simulación.

El análisis permitió obtener un desplazamiento vertical máximo aproximado de:

## 0.30 mm

Este resultado representa una primera evaluación virtual del subsistema mecánico.

A partir de este módulo se continuará desarrollando la estructura completa de Kartoffelmachine, integrando la faja transportadora, múltiples soportes en V, tolva, cámara, sistema de rotación y mecanismo de clasificación automática.