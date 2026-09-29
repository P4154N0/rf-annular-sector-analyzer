# Informe Técnico: Diagnóstico y Mitigación de Interferencia Electromagnética en Enlaces Críticos VHF

## I. Situación Técnica y Diagnóstico de la Problemática
Tras diversas evaluaciones técnicas de campo y el análisis sistemático de la operatividad del sistema de radiocomunicaciones, se detectaron anomalías críticas de interferencia electromagnética que afectaron directamente la operatividad de la red primaria de Emergencias Policiales. 

El fenómeno reportado consistió en una pérdida total de enlace bidireccional entre la estación central y las unidades operativas, tanto fijas como móviles. Dicha afectación se manifestó de forma intermitente, presentándose en ocasiones como un nivel elevado de ruido de banda ancha (fritura) o, en la mayoría de los casos, mediante un silencio absoluto, simulando la acción de un inhibidor de frecuencia o una superposición de armónicas de alta potencia. Las primeras trazas temporales indicaron un patrón de inicio recurrente en la franja horaria nocturna comprendida entre las 21:00 y las 22:00 horas.

## II. Geometría y Sectorización de la Interferencia
Geográficamente, el área afectada no abarcó la totalidad de la cobertura radial de los 360 grados, sino que se delimitó estrictamente a un sector anular (corona circular parcial). Las mediciones finales determinaron los siguientes límites espaciales del lóbulo de interferencia:

*   **Centro de Referencia (Emisor/Receptor Base):** Lat -37.456802, Lng -61.938778
*   **Radio Interior de Afectación:** 2196 metros
*   **Radio Exterior de Afectación:** 13495 metros
*   **Apertura Azimutal:** Cuña direccional comprendida entre los 94.9° y los 204.6°

Este vector de propagación comprometió específicamente el corredor geográfico orientado hacia el sur y sureste de la estación central, abarcando las jurisdicciones de Santa Trinidad, San José y Santa María.

## III. Impacto en Hardware y Saturación
Se constató un efecto colateral de saturación y bloqueo físico (*latch-up*) en las unidades de estación base de la central, equipos que operan con antenas emplazadas entre 5 y 40 metros de altura. Ante la incidencia de este campo electromagnético hostil, dichos equipos sufrieron un bloqueo de microcontrolador que impidió su apagado convencional mediante la tecla de encendido, requiriendo la desconexión física del suministro eléctrico, la retirada de los elementos radiantes y el cambio preventivo de canal para lograr su reseteo y restablecimiento operativo.

Tras un exhaustivo relevamiento técnico de toda la infraestructura propia (comprendiendo cables, líneas de transmisión, antenas y equipamiento base), se descartó categóricamente que la anomalía fuera producto de fallas internas o deficiencias físicas. Esta certeza técnica se fundamentó en que, una vez finalizado el periodo de incidencia de la interferencia, el círculo completo de cobertura recuperaba plenamente su comunicación habitual sin registrar alteraciones mecánicas ni de sintonía en el hardware.

## IV. Medidas de Mitigación y Protocolo de Acción Operativa
Ante la imposibilidad de garantizar la cobertura continua en la frecuencia principal bajo las condiciones descritas, se ejecutó el siguiente protocolo de contingencia para no interrumpir el servicio esencial:

1. **Monitoreo Dirigido:** Se mantuvo la operación en la red primaria de manera prioritaria durante el mayor tiempo posible, a los efectos de constatar los patrones de irrupción de la interferencia y su trazabilidad horaria.
2. **Protocolo de Desvío de Tráfico:** Ante el colapso de las comunicaciones o la ausencia de modulación en el sector delimitado, se procedió a realizar de inmediato el corrimiento y migración de los equipos fijos y móviles afectados hacia una red de contingencia y respaldo, garantizando la continuidad del despacho sin interrupciones.
3. **Registro y Centralización de Novedades:** Se estableció que cualquier corte, anomalía o indicio de saturación en las estaciones dejara de comunicarse de forma aislada, debiendo ser reportado de manera directa y centralizada detallando hora exacta, unidades involucradas y estado de los equipos base.