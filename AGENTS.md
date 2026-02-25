# AGENTS.md

Guia de orquestacion de agentes para `Marketing AB Testing`.

## Objetivo del proyecto

Herramientas de analisis de tests A/B para marketing: diseno estadistico, calculo de significancia, power analysis, reportes y visualizaciones con Python (pandas, scipy, streamlit).

## Regla de oro

No cargar contexto masivo por defecto. Activar solo la skill necesaria para la tarea actual.

## Flujo recomendado

1. `mab-orchestrator`: clasifica la tarea y define alcance.
2. `mab-explorer`: inspecciona datos, notebooks, codigo e impacto.
3. `mab-spec-planner`: produce spec corta (objetivo, criterios, riesgos).
4. **Gate humano #1**: aprobar o corregir la spec antes de implementar.
5. `mab-implementer`: implementa cambios minimos y coherentes.
6. `mab-validator`: valida con pruebas/ejecucion/lints.
7. `mab-senior-explainer`: sintetiza y explica con profundidad senior/docente.
8. **Gate humano #2**: aprobar, pedir ajustes o rechazar el cambio.
9. `mab-doc-updater`: actualiza README o docs solo si aplica.

## Registro de skills (router)

- Activar `mab-orchestrator` cuando la tarea sea ambigua o involucre multiples archivos.
- Activar `mab-explorer` cuando la tarea sea "donde esta", "como funciona" o "que impacto tiene".
- Activar `mab-spec-planner` antes de cambios medianos/grandes o con trade-offs.
- Activar `mab-implementer` cuando ya exista spec clara y alcance acotado.
- Activar `mab-validator` al terminar edicion de codigo.
- Activar `mab-senior-explainer` despues de validar y antes del cierre humano final.
- Activar `mab-doc-updater` si hubo cambios de comportamiento, instalacion o uso.
- Activar `ab-test-setup` cuando se planifique o disene un experimento (hipotesis, variantes, metricas, checklist pre-lanzamiento).
- Activar `ab-test-stats` para diseno de experimentos, power, significancia estadistica.
- Activar `ab-test-reporting` para reportes, dashboards y visualizaciones de resultados A/B.

## Flujo de skills para A/B testing

1. `ab-test-setup`: planificacion (hipotesis, variantes, metricas, tipo de test).
2. `ab-test-stats`: calculos (tamano de muestra, power, MDE, test estadistico).
3. `ab-test-setup`: checklist pre-lanzamiento y durante el test.
4. `ab-test-stats`: analisis de resultados (p-value, IC, conclusion).
5. `ab-test-reporting`: reportes, graficos y dashboards.

## Convenciones operativas

- Preferir cambios pequenos e iterativos.
- Mantener estilo PEP 8 y operaciones vectorizadas con pandas/numpy cuando aplique.
- Evitar clases innecesarias; priorizar funciones puras.
- Registrar decisiones relevantes en `docs/ai/memoria-operativa.md`.
- Verificacion contra requisitos: cada spec debe tener criterios de aceptacion verificables.
- TDD: escribir tests antes o junto con la implementacion; usar `tests/` para pruebas unitarias.
