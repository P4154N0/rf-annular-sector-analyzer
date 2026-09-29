# Documentación Matemática: Geodesia y Trigonometría Esférica

El motor de renderizado de **RF Annular Sector Analyzer** prescinde de librerías GIS pesadas al resolver la geometría espacial directamente en el cliente. Para garantizar que la proyección del sector anular mantenga proporciones métricas reales sobre el mapa cartográfico, el sistema asume un modelo de Tierra esférica con un radio medio $R = 6371000\text{ m}$ y utiliza fórmulas clásicas de trigonometría esférica (fórmulas de Haversine adaptadas).

A continuación, se detallan los tres pilares matemáticos implementados en el núcleo del sistema.

## 1. Problema Geodésico Directo (Cálculo de Destino)

Para trazar el polígono (la zona anular de color naranja), el algoritmo necesita calcular múltiples puntos perimetrales a lo largo de los arcos que forman el radio interior y exterior. Esto se logra partiendo de una coordenada central ($P_1$), una distancia métrica ($d$) y un acimut ($\theta$).

La función `destination(latlng, distanceM, bearingDeg)` implementa el cálculo:

**Fórmulas:**
$$\delta = \frac{d}{R}$$
$$\phi_2 = \arcsin\left(\sin \phi_1 \cos \delta + \cos \phi_1 \sin \delta \cos \theta\right)$$
$$\lambda_2 = \lambda_1 + \operatorname{atan2}\left(\sin \theta \sin \delta \cos \phi_1, \; \cos \delta - \sin \phi_1 \sin \phi_2\right)$$

*Donde:*
*   $\phi_1, \lambda_1$: Latitud y longitud del punto de origen (en radianes).
*   $\phi_2, \lambda_2$: Latitud y longitud del punto destino (en radianes).
*   $\delta$: Distancia angular.
*   $\theta$: Acimut o "bearing" (ángulo respecto al Norte verdadero, en radianes).

## 2. Problema Geodésico Inverso (Cálculo de Acimut)

Cuando el usuario arrastra los tiradores naranjas en el mapa, el sistema debe recalcular dinámicamente cuál es el nuevo ángulo de apertura del sector respecto al centro.

La función `bearingDeg(a, b)` resuelve esto calculando el rumbo inicial entre el centro ($a$) y la posición actual del tirador ($b$):

**Fórmulas:**
$$y = \sin(\lambda_2 - \lambda_1) \cos \phi_2$$
$$x = \cos \phi_1 \sin \phi_2 - \sin \phi_1 \cos \phi_2 \cos(\lambda_2 - \lambda_1)$$
$$\theta = \operatorname{atan2}(y, x)$$

*Donde:*
*   El resultado $\theta$ se convierte a grados y se normaliza utilizando una operación de módulo para mantener el valor estrictamente en el rango de $0^\circ$ a $360^\circ$ mediante la operación `(Math.atan2(y, x) * 180 / Math.PI + 360) % 360`.

## 3. Aproximación Cartesiana de Alta Velocidad (Drag Helpers)

Para evitar la sobrecarga matemática durante los eventos de arrastre rápido (`drag`) de los tiradores de ajuste de radios (verde y cian), la función `getPointFromCenter(distanceM, bearingDeg)` utiliza una aproximación euclidiana sobre una grilla plana local. 

Esta función es matemáticamente más económica y solo se utiliza para reposicionar los íconos de los tiradores, mientras que el trazado real del polígono sigue utilizando la trigonometría esférica de precisión.

**Fórmulas de aproximación:**
$$\Delta \text{lat} = \frac{d \cdot \cos \theta}{111320}$$
$$\Delta \text{lng} = \frac{d \cdot \sin \theta}{111320 \cdot \cos \phi_1}$$

*Donde:*
*   $111320\text{ m}$: Es la constante aproximada de metros por grado de latitud en el ecuador terrestre.
*   El término $\cos \phi_1$ compensa la convergencia de los meridianos a medida que nos alejamos del ecuador.