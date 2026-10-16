# Rúbricas del TP3 de IO2

Transcripción de `IO2/TP3/IO2-22C1-TP 3-Contenidos A/B/C.PNG.png` (rúbricas de la cátedra, versión 2022 C1). Plantilla de entrega de la parte A: `IO2/TP3/25C2-GXX-MC-TITULO.docx` (encabezado "IO 2 Grupo xx 2025c2").

Cada sección se evalúa en cuatro dimensiones: Analizar, Modelar, Explorar e Informar.

## Parte A: modelo conceptual y modelo de datos (entrega 29/09/2026, máximo 12 páginas)

### Modelo conceptual (70 %)

Elementos: descripción del problema y objetivo · variables de decisión (VD), de referencia (VR) y de estado (VE) · entidades y recursos · actividades, con diagrama de proceso IDEF0 · eventos, con diagramas lógicos · plan de análisis y de cuadros.

- **Analizar:** entendimiento general del problema, del objetivo, de los procesos y de cómo encarar la resolución. Plan de análisis y cuadros: cómo se va a estructurar la experimentación, cómo se van a visualizar y analizar los resultados y qué criterios se usan para tomar decisiones. Justificar decisiones.
- **Modelar:** correcta aplicación de herramientas. Al menos 2 de cada una: VD, VR y VE. Las VR tienen que ser contrapuestas. Las VE tienen que incluir al menos el % de ocupación de los recursos.
- **Explorar:** identificar situaciones no explícitas en el problema. Usar herramientas o diagramas no cubiertos en clase.

### Modelo de datos y cuantificación (30 %)

Elementos: tabla descriptiva de variables del modelo de datos · variables aleatorias · diagramas de relación o influencia entre variables · evaluación a priori (estimar el resultado esperado).

- **Analizar:** justificar los supuestos sobre parámetros y variables aleatorias. Identificar las fuentes de variabilidad. Relación entre variables: **usar variables de referencia anula el punto por completo.** En la evaluación a priori se busca una estimación con una simplificación del problema y una resolución analítica relativamente sencilla, sin simular.
- **Modelar:** listado completo, ordenado y bien definido de las variables y datos del modelo. Evitar repeticiones innecesarias entre el modelo conceptual y el de datos. En la evaluación a priori, aplicar la teoría vista en clase (filas, stocks u otra según corresponda).
- **Explorar:** alternativas: contrastar con un caso real (paper, artículo u otro). Plantear una situación alternativa en la evaluación a priori o aplicar teoría no cubierta en clase.

### Informar (toda la parte A)

Presentación y formato · ortografía y redacción · índice, numeración y referencias · **máximo 12 páginas**.

## Parte B: simulador en AnyLogic (entrega 13/10/2026, máximo 10 páginas)

### AnyLogic (80 %)

Elementos: entidades · actividades y flujo · recursos · variables de referencia · cálculo y visualización de variables de estado · stress test y debugging · funcionalidades de AnyLogic.

- **Analizar:** VR con cálculo correcto en el simulador. VE con cálculo y gráficos correctos en el simulador; **la actualización tiene que hacerse en los eventos que impactan en esa VE, no de forma cíclica.**
- **Modelar:** entidades: correcta codificación de atributos y llegadas, correcta programación de la aleatoriedad. Actividades y flujo: lógicas de filas, aleatoriedad. Recursos: lógica de asignación, aplicación de aleatoriedad. Codificación completa de todos los procesos. Se valora el uso de funciones para programar las lógicas más complejas.
- **Explorar:** stress test, típicamente variando las VD; se valora la variedad. Documentar el debugging. Usar al menos 2 funcionalidades de AnyLogic no cubiertas en detalle en clase. Se valora la creatividad para resolver dificultades de AnyLogic.
- **Informar:** orden del simulador, formato del código (por ejemplo, tabulado), comentarios en el código, formato de los gráficos.

### Informe (20 %)

Elementos: descripción de las principales lógicas y bloques · dificultades de codificación y cambios respecto de la parte A · cálculo de N y resultado de la simulación en condiciones iniciales.

- **Analizar:** descripción y análisis de los cambios respecto del modelo conceptual. Cálculo de N y resultado en condiciones iniciales: elegir un set inicial de VD, calcular N (cantidad de días a simular) y mostrar los resultados de 1 corrida, con intervalo de confianza.
- **Modelar:** descripción de las principales lógicas y bloques del simulador AnyLogic.
- **Informar:** presentación, formato, ortografía, índice y referencias · **máximo 10 páginas**.

## Parte C: experimentación y conclusiones (entrega 10/11/2026, máximo 10 páginas)

### Proceso de experimentación (50 %)

Elementos: procedimiento de experimentación · VD: justificación de rangos y lógica de variación · condiciones del experimento (duración, warm up) · medición de VR y generación del output de los experimentos · aplicación de Parameter Variation (PV) · automatización.

- **Analizar:** justificación de las decisiones. VD: rango, paso (step) y valores descartados.
- **Modelar:** procedimiento de experimentación: plantear un plan previo, heurística y pasos de cálculo. PV: programación correcta. Exportación de resultados.
- **Explorar:** automatización: completar el total de experimentos, el cálculo de variables de referencia y la exportación de datos con 1 click. Abierto a iniciativas de cada grupo.

### Análisis y conclusiones (50 %)

Elementos: descripción de dificultades, errores y debugging de la experimentación · cambios respecto del modelo conceptual y del simulador de la parte B · obtención de resultados con IC y comparación entre escenarios · conclusión y recomendación final.

- **Analizar:** resultados: cálculo de IC y comparación entre escenarios, con los tests adecuados. Claridad en las conclusiones.
- **Modelar:** representación de la experimentación. Ajustes al modelo conceptual y al simulador respecto de las partes A y B.
- **Explorar:** distintos métodos para comparar alternativas. Abierto a iniciativas de cada grupo.

### Informar (toda la parte C)

AnyLogic: orden del simulador, formato del código (por ejemplo, tabulado), comentarios en el código, formato de los gráficos. Presentación, formato, ortografía, índice y referencias. Gráficos y figuras fáciles de entender. **Máximo 10 páginas.**

## Estructura de la plantilla de la parte A (`25C2-GXX-MC-TITULO.docx`)

1. Objetivo: Definición del problema · Alcance
2. Modelo conceptual: Variables de decisión · Variables de referencia · Plan de cuadros (conceptual) · Plan de experimentación (conceptual) · Diagrama de proceso · Eventos destacados y lógicas · Variables aleatorias, parámetros y relación entre ellos · Elementos del simulador (entidades, atributos, variables, recursos, colas, eventos)
3. Modelo de datos: Tabla diccionario · Análisis y cuantificación de variables (método de recolección, proceso de obtención) · Análisis estadístico (ajuste a distribuciones) · Relación entre variables (modelos de relación)
4. Bibliografía, referencias y anexos: Bibliografía · Referencias · Descripción teórica de los temas desarrollados que exceden los temas tratados en el curso
