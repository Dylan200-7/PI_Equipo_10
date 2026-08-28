# 🥔 Taller 01 — Modelado y Simulación del Módulo en V

## Kartoffelmachine

En este taller se desarrolló el modelado mecánico inicial de uno de los módulos principales del proyecto **Kartoffelmachine**, específicamente el sistema encargado de posicionar y permitir la rotación de cada papa durante su recorrido por la faja transportadora.

El diseño fue realizado inicialmente en **Onshape** y posteriormente fue importado a **SimScale** para realizar una primera evaluación mediante análisis estructural estático.

---

## 1. Objetivo

El objetivo de esta etapa fue diseñar y analizar un módulo mecánico capaz de mantener una papa centrada durante su desplazamiento y permitir posteriormente su rotación mediante un rodillo inferior.

El módulo está compuesto principalmente por:

- Una base estructural.
- Dos guías inclinadas formando una V.
- Un rodillo inferior.
- Un eje central para el rodillo.
- Dos soportes estructurales.
- Un sistema de fijación hacia la base.

Este módulo posteriormente podrá repetirse varias veces a lo largo de una faja transportadora, de manera que cada papa ocupe su propia posición durante el proceso de inspección.

---

## 2. Modelado en Onshape

### 2.1 Diseño inicial

El modelado fue realizado utilizando **Onshape** mediante un `Part Studio`.

Inicialmente se desarrollaron las piezas principales del módulo:

1. Base.
2. Guía izquierda.
3. Guía derecha.
4. Rodillo inferior.
5. Eje del rodillo.

Las dos guías fueron ubicadas de forma inclinada para obtener una geometría en **V**.

Esta geometría tiene como finalidad mantener la papa centrada durante su recorrido y reducir sus desplazamientos laterales.

---

### 2.2 Rodillo inferior

En la zona inferior de la V se incorporó un rodillo cilíndrico.

La función de este elemento será permitir la rotación de la papa durante la etapa de inspección.

Posteriormente, el rodillo podrá ser accionado mediante un motor y recubierto con un material de mayor fricción, como:

- Goma.
- Caucho.
- Silicona.
- TPU.

El incremento de fricción permitirá transmitir el movimiento del rodillo hacia la superficie de la papa.

---

### 2.3 Incorporación de soportes

Durante el desarrollo inicial se identificó que las dos guías inclinadas se encontraban separadas de la base.

Esto representaba un problema estructural, ya que las fuerzas ejercidas sobre las guías no tenían una trayectoria física adecuada hacia la estructura inferior.

Para solucionar este problema se incorporaron dos soportes estructurales que conectan las guías en V con la base.

De esta manera, las cargas pueden ser transmitidas desde las guías hacia la estructura principal.

### Modelo desarrollado en Onshape

<p align="center">
  <img src="Recursos/Imágenes/Onshape_Modulo_V.png" width="800"/>
</p>

<p align="center">
  <em>Figura 1. Modelo del módulo en V desarrollado en Onshape.</em>
</p>

El modelo desarrollado está compuesto por:

- Base estructural.
- Guía izquierda.
- Guía derecha.
- Soporte izquierdo.
- Soporte derecho.
- Rodillo inferior.
- Eje central.

---

## 3. Importación a SimScale

Una vez finalizado el modelo principal en Onshape, la geometría fue importada hacia **SimScale**.

El objetivo fue realizar una primera evaluación del comportamiento mecánico del módulo utilizando un análisis estructural estático.

---

## 4. Problemas encontrados durante la importación

Durante la primera importación se detectó un error relacionado con un cuerpo superficial.

SimScale identificó una geometría denominada:

`Surface 1`

Esta pieza presentaba área, pero no volumen, por lo que había sido creada como una superficie y no como un sólido tridimensional.

El análisis estructural utilizado requiere sólidos para realizar correctamente los cálculos.

Por este motivo, la superficie que no era necesaria para el análisis fue eliminada.

Después de esta corrección, el modelo quedó compuesto únicamente por cuerpos sólidos.

---

## 5. Configuración del análisis estructural

En SimScale se utilizó un análisis:

### Static Structural

Este análisis permite estudiar el comportamiento de una estructura frente a cargas constantes.

En esta primera etapa se buscó evaluar principalmente:

- El desplazamiento de las guías.
- La deformación del módulo.
- La transmisión de cargas hacia la base.
- El comportamiento estructural preliminar.

---

## 6. Material utilizado

Para el análisis se utilizó **PLA** como material preliminar.

Esta elección se realizó considerando la posibilidad de fabricar parte del prototipo mediante impresión 3D.

Los principales parámetros utilizados fueron:

| Propiedad | Valor |
|---|---:|
| Módulo de Young | 3.5 × 10⁹ Pa |
| Coeficiente de Poisson | 0.36 |
| Densidad | 1250 kg/m³ |
| Comportamiento | Elástico lineal |
| Dependencia | Isotrópica |

El PLA fue asignado a los cuatro sólidos presentes en el análisis:

- Part 1.
- Part 2.
- Part 3.
- Part 4.

### Configuración del material PLA

<p align="center">
  <img src="Recursos/Imágenes/SimScale_PLA.png" width="800"/>
</p>

<p align="center">
  <em>Figura 2. Asignación del material PLA a los componentes del modelo.</em>
</p>

---

## 7. Configuración de la gravedad

También se incorporó la gravedad al modelo.

Se utilizó una magnitud de:

**9.81 m/s²**

dirigida hacia la dirección vertical negativa del sistema.

### Configuración de gravedad

<p align="center">
  <img src="Recursos/Imágenes/SimScale_Gravedad.png" width="800"/>
</p>

<p align="center">
  <em>Figura 3. Configuración de la gravedad dentro del análisis estructural.</em>
</p>

Esta condición permite considerar el peso propio de los componentes durante la simulación.

---

## 8. Condición Fixed Support

Para representar la conexión del módulo con la estructura principal de Kartoffelmachine, se utilizó una condición de:

### Fixed Support

Esta condición restringe el desplazamiento de las superficies seleccionadas de la base.

### Fixed Support aplicado

<p align="center">
  <img src="Recursos/Imágenes/SimScale_Fixed_Support.png" width="800"/>
</p>

<p align="center">
  <em>Figura 4. Condición Fixed Support aplicada sobre la base del módulo.</em>
</p>

Esta configuración representa que la base se encuentra firmemente sujeta a la estructura de la máquina.

---

## 9. Aplicación de fuerzas

Para representar de manera simplificada la carga que ejercería una papa sobre ambas paredes de la V, se utilizaron dos fuerzas.

Estas cargas fueron aplicadas sobre las superficies inclinadas.

---

### 9.1 Force 2

Para una de las guías se configuraron los siguientes valores:

| Componente | Valor |
|---|---:|
| Fx | 0 N |
| Fy | 5 N |
| Fz | -5 N |

### Configuración de Force 2

<p align="center">
  <img src="Recursos/Imágenes/SimScale_Force_2.png" width="800"/>
</p>

<p align="center">
  <em>Figura 5. Fuerza aplicada sobre una de las guías en V.</em>
</p>

La componente vertical negativa representa una carga dirigida hacia abajo.

La componente lateral representa la presión ejercida sobre uno de los lados de la V.

---

### 9.2 Force 3

En la guía contraria se aplicó una fuerza similar, pero con dirección lateral opuesta.

Los valores utilizados fueron:

| Componente | Valor |
|---|---:|
| Fx | 0 N |
| Fy | -5 N |
| Fz | -5 N |

### Configuración de Force 3

<p align="center">
  <img src="Recursos/Imágenes/SimScale_Force_3.png" width="800"/>
</p>

<p align="center">
  <em>Figura 6. Fuerza aplicada sobre la segunda guía en V.</em>
</p>

La utilización de componentes laterales opuestas permite representar de manera aproximada la carga generada por una papa apoyada entre ambas superficies inclinadas.

---

## 10. Contactos entre componentes

Durante las primeras pruebas se detectó que algunas piezas se encontraban estructuralmente aisladas.

Inicialmente las paredes en V no tenían una conexión física adecuada con la base.

Debido a ello, SimScale no podía transmitir correctamente las fuerzas entre los distintos componentes.

Para solucionar el problema se realizaron modificaciones en Onshape y se incorporaron soportes estructurales.

Después de actualizar la geometría se configuraron los contactos correspondientes entre las diferentes piezas.

Finalmente, el modelo contó con:

**Contacts (3)**

Estos contactos permiten transmitir las cargas entre los componentes durante el análisis.

---

## 11. Generación de la malla

Una vez configurados:

- Material.
- Gravedad.
- Fixed Support.
- Fuerzas.
- Contactos.

se procedió a generar la malla del modelo.

Los principales parámetros utilizados fueron:

| Parámetro | Configuración |
|---|---|
| Algorithm | Standard |
| Sizing | Automatic |
| Fineness | 8.5 |

### Mallado del modelo

<p align="center">
  <img src="Recursos/Imágenes/SimScale_Mallado.png" width="800"/>
</p>

<p align="center">
  <em>Figura 7. Mallado generado para el análisis estructural.</em>
</p>

La malla final presentó aproximadamente:

- **3.4 millones de celdas.**
- **5 millones de nodos.**

La generación de la malla permite dividir la geometría en elementos pequeños sobre los cuales SimScale realiza los cálculos mediante el método de elementos finitos.

---

## 12. Ejecución de la simulación

Una vez completada la configuración del modelo se ejecutó:

### Static — Run 1

El proceso de simulación finalizó correctamente.

También se confirmó que el mallado fue generado sin errores.

---

## 13. Resultados obtenidos

El principal resultado evaluado durante esta etapa fue:

### Displacement Z

Este resultado representa el desplazamiento de los componentes en la dirección vertical.

### Resultado de desplazamiento

<p align="center">
  <img src="Recursos/Imágenes/SimScale_Desplazamiento.png" width="800"/>
</p>

<p align="center">
  <em>Figura 8. Resultado del desplazamiento vertical obtenido en SimScale.</em>
</p>

La escala obtenida muestra aproximadamente un desplazamiento mínimo de:

**−2.984 × 10⁻⁴ m**

Al convertir este valor a milímetros:

**−2.984 × 10⁻⁴ × 1000**

se obtiene aproximadamente:

**−0.2984 mm**

Por lo tanto, el desplazamiento vertical máximo hacia abajo observado fue aproximadamente:

## **0.30 mm**

También se observó un desplazamiento positivo máximo cercano a:

**2.006 × 10⁻⁵ m**

equivalente aproximadamente a:

**0.020 mm**

---

## 14. Interpretación de los resultados

Los resultados muestran una variación del desplazamiento a lo largo de las guías inclinadas.

Las zonas más alejadas de los soportes presentan mayores desplazamientos, mientras que las zonas cercanas a la estructura presentan menores movimientos.

El desplazamiento máximo aproximado fue de:

**0.30 mm**

Este valor resulta relativamente pequeño en comparación con las dimensiones generales del módulo.

Por lo tanto, bajo las condiciones utilizadas en esta simulación preliminar, la estructura presenta un comportamiento adecuado para continuar con el desarrollo del prototipo.

Sin embargo, los resultados todavía no representan el funcionamiento completo de Kartoffelmachine.

---

## 15. Simplificaciones realizadas

En esta primera simulación se realizaron diferentes simplificaciones para reducir la complejidad del análisis.

No se incorporaron:

- La papa como cuerpo tridimensional.
- La fricción entre la papa y el rodillo.
- La rotación del rodillo.
- El motor.
- El torque generado por el motor.
- El movimiento de la faja transportadora.
- La tolva.
- La cámara.
- El sistema electrónico.
- La Raspberry Pi.
- El mecanismo de separación.
- El impacto producido por la caída de una papa.

La acción de la papa fue representada mediante fuerzas aplicadas sobre las paredes de la V.

---

## 16. Problemas encontrados y soluciones aplicadas

Durante el proceso de modelado y simulación se presentaron diferentes dificultades.

| Problema | Causa | Solución |
|---|---|---|
| `Sheet bodies detected` | Existía una superficie sin volumen | Se eliminó `Surface 1` |
| Piezas sin interacción | Algunas partes no tenían contactos | Se configuraron contactos |
| Guías sin conexión con la base | El diseño inicial no incluía soportes | Se agregaron soportes en Onshape |
| Simulación no podía ejecutarse | Existían cuerpos estructuralmente aislados | Se modificó la geometría |
| Representación de la papa | No se modeló como cuerpo sólido | Se utilizaron fuerzas equivalentes |
| Diseño inicialmente poco fabricable | Las guías parecían estar suspendidas | Se incorporaron soportes estructurales |

---

## 17. Mejora del diseño mediante simulación

El uso de SimScale permitió identificar problemas que no eran completamente evidentes durante el modelado inicial.

Inicialmente el módulo estaba constituido principalmente por:

- Base.
- Dos guías inclinadas.
- Rodillo.

Durante la configuración del análisis se identificó que las guías no tenían una conexión estructural adecuada hacia la base.

Como consecuencia, se regresó a Onshape y se añadieron soportes.

Por lo tanto, la simulación no solamente permitió obtener resultados numéricos, sino que también contribuyó directamente a mejorar el diseño mecánico.

---

## 18. Integración con Kartoffelmachine

El módulo desarrollado representa una posición individual para una papa.

El diseño general de Kartoffelmachine contempla utilizar múltiples posiciones similares distribuidas a lo largo de una faja transportadora.

Cada papa podrá colocarse dentro de su propio soporte en V.

Durante el funcionamiento futuro:

1. Las papas ingresarán mediante una tolva.
2. Cada papa ocupará una posición individual.
3. La faja realizará el transporte.
4. El rodillo permitirá generar la rotación.
5. Una cámara capturará diferentes vistas.
6. La Raspberry Pi procesará las imágenes.
7. El modelo de visión artificial determinará la calidad de la papa.
8. Un mecanismo automático realizará la separación correspondiente.

---

## 19. Trabajo futuro

Las siguientes etapas del desarrollo consideran:

1. Modelar la faja transportadora completa.
2. Incorporar múltiples módulos en V.
3. Diseñar la tolva de alimentación.
4. Diseñar el soporte de la cámara.
5. Incorporar iluminación.
6. Incorporar el motor del rodillo.
7. Diseñar el sistema de transmisión.
8. Analizar la rotación de la papa.
9. Evaluar la fricción entre papa y rodillo.
10. Diseñar el mecanismo de separación.
11. Integrar todos los componentes en un único ensamblaje.
12. Realizar nuevas simulaciones sobre el sistema completo.

---

## 20. Conclusión

Se desarrolló satisfactoriamente un primer modelo mecánico del módulo de posicionamiento y rotación de papas utilizando **Onshape**.

El módulo está compuesto principalmente por dos superficies inclinadas que forman una geometría en V y un rodillo inferior que permitirá posteriormente generar la rotación de cada papa.

Durante el proceso se identificó la necesidad de incorporar soportes que conectaran las guías inclinadas con la base, obteniendo una estructura más realista y físicamente construible.

Posteriormente el modelo fue importado hacia **SimScale**, donde se configuró un análisis estructural estático.

Se definieron:

- Material PLA.
- Gravedad.
- Fixed Support.
- Fuerzas.
- Contactos.
- Mallado.
- Condiciones de simulación.

El análisis permitió obtener un desplazamiento vertical máximo aproximado de:

## **0.30 mm**

Este resultado constituye una primera evaluación virtual del subsistema mecánico.

A partir de este módulo se continuará desarrollando la estructura completa de **Kartoffelmachine**, incorporando la faja transportadora, múltiples módulos en V, la tolva, el sistema de rotación, la cámara de reconocimiento y el mecanismo de clasificación automática.
