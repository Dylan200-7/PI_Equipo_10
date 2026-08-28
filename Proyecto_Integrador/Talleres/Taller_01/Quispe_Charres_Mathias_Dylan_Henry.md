# Modelado y análisis estructural del módulo en V

## Diseño de la pieza

El módulo fue diseñado en **Onshape** como parte del sistema mecánico de **Kartoffelmachine**. Su función es mantener cada papa posicionada individualmente durante su recorrido por la faja transportadora y permitir posteriormente su rotación mediante un rodillo ubicado en la zona inferior.

La geometría está compuesta principalmente por una base, dos guías inclinadas que forman una **V**, soportes estructurales y un rodillo inferior.

La forma en V permite centrar la papa y reducir su desplazamiento lateral durante el proceso de inspección.

**Modelo CAD:**  
[Ver modelo en Onshape](https://cad.onshape.com/documents/ae63f36f4342b7ddb9845e0c/w/7c21d35c96e35642a47e9d04/e/2c1a282385f188e1420c34c3)

<p align="center">
  <img src="Recursos/Imágenes/Onshape_Modulo_V.png" width="800"/>
</p>

<p align="center">
  <em>Figura 1. Modelo CAD del módulo en V desarrollado en Onshape.</em>
</p>

---

## Modificaciones realizadas durante el modelado

Durante el desarrollo inicial se identificó que las dos guías inclinadas no se encontraban conectadas directamente con la base.

Esta configuración ocasionaba que las paredes quedaran estructuralmente aisladas durante la simulación.

Para solucionar este problema se incorporaron soportes entre las guías y la base, permitiendo una correcta transmisión de las cargas hacia la estructura inferior.

También se identificó una geometría creada como superficie denominada `Surface 1`. Debido a que esta superficie no poseía volumen y no era necesaria para el análisis estructural, fue eliminada antes de realizar la simulación definitiva.

---

# Análisis estructural

El modelo fue evaluado en **SimScale** mediante un análisis estructural estático.

Para la simulación se utilizó **PLA** como material y se configuraron condiciones de gravedad, fuerzas, contactos y fijación.

**Simulación:**  
[Ver simulación en SimScale](https://www.simscale.com/workbench/?pid=8224550795592368556&rru=945c7aac-8471-4882-861e-cce932f1d648&ci=cf2ece35-8068-443a-adc2-56ed3a30edc5&mt=SIMULATION_RESULT&ct=SOLUTION_FIELD)

---

## Material utilizado

Para el análisis se utilizó **PLA**, considerando que el prototipo podrá fabricar algunos de sus componentes mediante impresión 3D.

Las principales propiedades utilizadas fueron:

| Propiedad | Valor |
| ---------------------- | --------------------: |
| Material | PLA |
| Módulo de Young | 3.5 × 10⁹ Pa |
| Coeficiente de Poisson | 0.36 |
| Densidad | 1250 kg/m³ |
| Modelo del material | Elástico lineal |
| Comportamiento | Isotrópico |

<p align="center">
  <img src="Recursos/Imágenes/SimScale_PLA.png" width="800"/>
</p>

<p align="center">
  <em>Figura 2. Asignación del material PLA en SimScale.</em>
</p>

---

## Configuración de gravedad

Dentro del análisis se incorporó la gravedad con una magnitud de:

**9.81 m/s²**

orientada hacia la dirección vertical negativa del modelo.

Esta condición permite considerar el peso propio de los componentes del módulo durante la simulación.

<p align="center">
  <img src="Recursos/Imágenes/SimScale_Gravedad.png" width="800"/>
</p>

<p align="center">
  <em>Figura 3. Configuración de la gravedad utilizada en la simulación.</em>
</p>

---

## Condición de fijación

Para representar la unión del módulo con la estructura principal de Kartoffelmachine se configuró una condición de:

**Fixed Support**

Esta condición restringe el desplazamiento de las superficies seleccionadas en la base del módulo.

<p align="center">
  <img src="Recursos/Imágenes/SimScale_Fixed_Support.png" width="800"/>
</p>

<p align="center">
  <em>Figura 4. Condición Fixed Support aplicada sobre la estructura.</em>
</p>

---

## Aplicación de fuerzas

Para representar de manera simplificada la carga ejercida por una papa sobre las dos paredes de la V se utilizaron dos fuerzas.

### Force 2

En una de las guías se configuraron los siguientes componentes:

| Componente | Valor |
| ---------------------- | --------------------: |
| Fx | 0 N |
| Fy | 5 N |
| Fz | -5 N |

<p align="center">
  <img src="Recursos/Imágenes/SimScale_Force_2.png" width="800"/>
</p>

<p align="center">
  <em>Figura 5. Force 2 aplicada sobre una de las guías del módulo.</em>
</p>

### Force 3

En la guía opuesta se aplicó una fuerza en sentido lateral contrario:

| Componente | Valor |
| ---------------------- | --------------------: |
| Fx | 0 N |
| Fy | -5 N |
| Fz | -5 N |

<p align="center">
  <img src="Recursos/Imágenes/SimScale_Force_3.png" width="800"/>
</p>

<p align="center">
  <em>Figura 6. Force 3 aplicada sobre la segunda guía del módulo.</em>
</p>

Las componentes laterales opuestas permiten representar de manera aproximada la presión ejercida por una papa al encontrarse apoyada entre ambas superficies inclinadas.

---

## Contactos entre componentes

Durante las primeras pruebas se identificaron componentes sin una conexión estructural adecuada.

Esto provocaba que SimScale detectara algunas piezas como elementos independientes y no pudiera transmitir correctamente las cargas hacia la base.

Luego de modificar el diseño en Onshape y agregar los soportes correspondientes, se actualizaron los contactos entre los diferentes cuerpos.

Finalmente se trabajó con:

**Contacts (3)**

permitiendo transmitir correctamente las cargas entre los componentes durante la simulación.

---

## Generación de la malla

Para realizar los cálculos mediante elementos finitos se generó una malla sobre todo el modelo.

La configuración utilizada fue:

| Parámetro | Configuración |
| ---------------------- | --------------------: |
| Algoritmo | Standard |
| Sizing | Automatic |
| Fineness | 8.5 |
| Celdas aproximadas | 3.4 millones |
| Nodos aproximados | 5 millones |

<p align="center">
  <img src="Recursos/Imágenes/SimScale_Mallado.png" width="800"/>
</p>

<p align="center">
  <em>Figura 7. Mallado del módulo generado en SimScale.</em>
</p>

---

# Resultado de la simulación

El principal resultado evaluado fue el desplazamiento vertical:

## Displacement Z

<p align="center">
  <img src="Recursos/Imágenes/SimScale_Desplazamiento.png" width="800"/>
</p>

<p align="center">
  <em>Figura 8. Distribución del desplazamiento vertical del módulo.</em>
</p>

De acuerdo con la escala mostrada en SimScale, el desplazamiento mínimo obtenido fue aproximadamente:

**−2.984 × 10⁻⁴ m**

Al convertir este valor a milímetros:

**−2.984 × 10⁻⁴ m × 1000 = −0.2984 mm**

Por lo tanto, el desplazamiento vertical máximo hacia abajo obtenido en la simulación fue aproximadamente:

## **0.30 mm**

También se obtuvo un desplazamiento positivo máximo cercano a:

**2.006 × 10⁻⁵ m ≈ 0.020 mm**

---

## Resumen de resultados

| Parámetro | Resultado |
| ---------------------- | --------------------: |
| Material | PLA |
| Tipo de análisis | Estructural estático |
| Resultado evaluado | Displacement Z |
| Desplazamiento máximo aprox. | **0.30 mm** |
| Gravedad | 9.81 m/s² |
| Fuerza lateral guía 1 | 5 N |
| Fuerza vertical guía 1 | -5 N |
| Fuerza lateral guía 2 | -5 N |
| Fuerza vertical guía 2 | -5 N |
| Mallado | Standard |
| Fineness | 8.5 |

---

## Interpretación del resultado

La simulación permite observar cómo las cargas aplicadas sobre las paredes inclinadas producen una pequeña deformación en la estructura.

Las regiones más alejadas de los soportes presentan un mayor desplazamiento, mientras que las zonas próximas a la base permanecen con menores desplazamientos debido a la condición de fijación aplicada.

El valor máximo obtenido fue aproximadamente:

**0.30 mm**

Este desplazamiento es reducido en comparación con las dimensiones generales del módulo, por lo que el comportamiento estructural obtenido en esta primera simulación resulta adecuado para continuar con el desarrollo del prototipo.

Sin embargo, esta simulación representa únicamente una evaluación preliminar y simplificada del funcionamiento real.

---

## Simplificaciones del análisis

Para esta primera simulación no se incorporaron algunos elementos del funcionamiento real de Kartoffelmachine.

Entre las simplificaciones realizadas se encuentran:

- La papa no fue modelada como un sólido tridimensional.
- La carga de la papa fue representada mediante fuerzas equivalentes.
- No se simuló la rotación del rodillo.
- No se incorporó fricción entre la papa y el rodillo.
- No se modeló el motor.
- No se aplicó torque al rodillo.
- No se simuló el movimiento de la faja transportadora.
- No se consideró todavía la caída de las papas desde la tolva.
- No se incorporó la cámara ni los componentes electrónicos.

Estas simplificaciones permitieron realizar inicialmente un análisis estructural del soporte sin aumentar innecesariamente la complejidad de la simulación.

---

## Mejoras realizadas a partir de la simulación

El proceso de simulación permitió detectar problemas en el diseño inicial que no eran evidentes únicamente mediante el modelado CAD.

Los principales problemas detectados fueron:

| Problema | Solución |
| ---------------------- | -------------------- |
| Existencia de `Surface 1` sin volumen | Eliminación de la superficie |
| Guías estructuralmente aisladas | Incorporación de soportes |
| Falta de transmisión de cargas | Configuración de contactos |
| Diseño inicial poco fabricable | Modificación de la estructura |
| Necesidad de representar la papa | Aplicación de fuerzas equivalentes |

De esta manera, SimScale fue utilizado no solamente para obtener resultados numéricos, sino también como una herramienta para mejorar el diseño desarrollado inicialmente en Onshape.

---

# Integración con Kartoffelmachine

El modelo desarrollado corresponde a **un módulo individual para una papa**.

En el diseño completo de Kartoffelmachine se plantea utilizar varios módulos similares distribuidos sobre una faja transportadora.

Cada papa ocupará su propia posición en V.

Posteriormente se integrarán:

- Faja transportadora.
- Múltiples módulos en V.
- Tolva de alimentación.
- Rodillos de rotación.
- Sistema de accionamiento.
- Cámara.
- Iluminación.
- Raspberry Pi.
- Sistema de visión artificial.
- Mecanismo de separación de papas buenas y malas.

El rodillo ubicado en la zona inferior permitirá hacer girar la papa durante la inspección, permitiendo que la cámara capture diferentes zonas de su superficie.

---

## Conclusión

Se desarrolló en **Onshape** un primer modelo del módulo mecánico de posicionamiento y rotación de papas para el proyecto **Kartoffelmachine**.

El diseño utiliza dos guías inclinadas en forma de V para mantener la papa centrada y un rodillo inferior destinado a generar posteriormente su rotación.

Durante el proceso de análisis se identificó la necesidad de incorporar soportes adicionales entre las guías y la base, permitiendo obtener una estructura más realista y físicamente construible.

El modelo fue posteriormente evaluado mediante **SimScale** utilizando un análisis estructural estático y PLA como material.

El desplazamiento vertical máximo obtenido fue aproximadamente:

## **0.30 mm**

Este resultado permite realizar una primera evaluación del comportamiento estructural del módulo y sirve como referencia para continuar con el diseño de los demás componentes de Kartoffelmachine.

---

# Enlaces del proyecto

### Modelo CAD

[**Abrir modelo en Onshape**](https://cad.onshape.com/documents/ae63f36f4342b7ddb9845e0c/w/7c21d35c96e35642a47e9d04/e/2c1a282385f188e1420c34c3)

### Simulación estructural

[**Abrir simulación en SimScale**](https://www.simscale.com/workbench/?pid=8224550795592368556&rru=945c7aac-8471-4882-861e-cce932f1d648&ci=cf2ece35-8068-443a-adc2-56ed3a30edc5&mt=SIMULATION_RESULT&ct=SOLUTION_FIELD)