# IO2 TP3: RedBaires

Investigación Operativa 2 (ITBA), 2026, 2.º cuatrimestre. Grupo 02: Yasmin Ady Ohana, Julia Sexe y Santiago Minoyetti.

Simulación de eventos discretos de la propagación de rumores en la red social RedBaires y de las contramedidas disponibles: moderadores, clasificador Centinela, fricción en los reenvíos y degradación del alcance.

## Contenido

| Archivo | Qué es |
|---|---|
| `entregas/26C2-G02-MC-TP3A.pdf` | Parte A entregada: modelo conceptual y modelo de datos. |
| `TP3_modelo_de_datos.ipynb` / `.html` | Notebook del modelo de datos de la parte A: limpieza, ajuste de distribuciones y evaluación a priori. |
| `insumos_redbaires.py` | Lee `TP3_datos.zip`, aplica la limpieza y estima todos los parámetros del simulador (`estimar_insumos`). |
| `simulador_redbaires.py` | Simulador: eventos E1 a E4, lógicas L1 a L4, variables de decisión parametrizadas e informe de variables de referencia. |
| `validacion_redbaires.py` | Prueba de bondad de ajuste por Monte Carlo entre las cascadas simuladas y las observadas. |
| `TP3_simulador_RedBaires.ipynb` / `.html` | Notebook de la parte B, ejecutado: insumos, validación, verificación, cálculo de N, corridas con IC y prueba de estrés. |
| `construir_notebook.py` | Genera el notebook de la parte B (sin ejecutar) a partir de su texto y código. |
| `TP3_datos.zip` | Datos de la cátedra (muestra de cascadas y parámetros de Finanzas). |
| `docs/rubricas_TP3.md` | Transcripción de las rúbricas de las tres partes. |

Para mirar los resultados sin instalar nada, abrir los `.html` en el navegador.

## Cómo correrlo

Requiere Python 3.11 o posterior.

```bash
python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Ejemplo de uso del simulador:

```python
from insumos_redbaires import estimar_insumos
from simulador_redbaires import SimuladorRedBaires, Configuracion, Supuestos, replicar, informe_replicas

I = estimar_insumos('TP3_datos.zip')          # unos 30 s
sim = SimuladorRedBaires(I)
sup = Supuestos(escala=294.606)                # escala recalibrada en la sección 5 del notebook

# una réplica: 1 día de calentamiento + 30 días de medición (unos 2,5 min)
informe, _ = sim.correr(Configuracion(M=2, C=1, U=5, F=0.25, D='mega', delta=0.5), 'conservador', sup, semilla=1)
print(informe.resumen())

# varias réplicas en paralelo y sus intervalos de confianza
tabla = replicar(sim, Configuracion(M=2), 'conservador', sup, n=10, semilla_base=1, procesos=2)
print(informe_replicas(tabla))
```

Con `procesos > 1` las réplicas se reparten en procesos con el método de inicio del sistema (en Windows, spawn). Si el código anterior se corre como script, y no desde el cuaderno, tiene que ir bajo `if __name__ == '__main__':`.

IN, IL y CFP son totales de la ventana de medición. Los costos del informe (CF, `CFP_mes`, CD) están en USD por mes: con un horizonte distinto de 30 días, lo medido se lleva a un mes antes de sumarlo a CF.

Variables de decisión (`Configuracion`):

| VD | Significado | Rango |
|---|---|---|
| `M` | moderadores por turno | 1 a 12 |
| `C` | configuración de Centinela | 0 (medida), 1 (declarada por Finanzas), 2 (máximo del rango) |
| `U` | umbral de fricción (reenvíos acumulados de la pieza) | 1 a 20 |
| `F` | probabilidad de bloquear un reenvío por encima del umbral | 0 a 0,9 |
| `D` | alcance de la degradación | `'ninguna'`, `'mega'`, `'c2'`, `'mega_c2'` |
| `delta` | intensidad de la degradación | 0 a 0,9 |

Escenarios: `'conservador'`, `'intermedio'` y `'pesimista'`. Los supuestos sin datos (PREM, TREV, ESC, NDEG, horizonte, representación del retardo) están en `Supuestos`.

Dos corridas con la misma semilla dan el mismo informe. Dos configuraciones corridas con la misma `semilla_base` comparten números aleatorios.

Para volver a ejecutar el notebook completo y su versión HTML (entre 35 y 60 minutos con 2 núcleos, según la máquina), con el entorno activado:

```bash
python construir_notebook.py
python -m nbconvert --to notebook --execute --ExecutePreprocessor.timeout=-1 TP3_simulador_RedBaires.ipynb --output TP3_simulador_RedBaires.ipynb
python -m nbconvert --to html TP3_simulador_RedBaires.ipynb
```

`python -m nbconvert` asegura que el cuaderno corra con el Python del entorno, aunque haya otro Jupyter instalado en el sistema.

Las corridas largas se guardan en `resultados_corridas/`, en una subcarpeta identificada por el código de los módulos y los datos, y cada archivo lleva además un resumen de los parámetros de su corrida. Si la ejecución se interrumpe, retoma desde lo guardado; si el código o los datos cambian, recalcula todo, y si cambian los parámetros de una corrida, recalcula esa corrida. Esa carpeta no se sube al repositorio.

## Estado

- [x] Parte A: modelo conceptual y modelo de datos (entregada).
- [x] Parte B: simulador, validación, verificación, cálculo de N y corridas en condiciones iniciales.
- [ ] Parte B: informe (máximo 10 páginas).
- [ ] Parte B: confirmar con la cátedra si se acepta el simulador en Python (la rúbrica menciona AnyLogic).
- [ ] Parte B: decidir la calibración de la escala de siembra (ver sección 9 del notebook).
- [ ] Parte C: experimentación y conclusiones.
