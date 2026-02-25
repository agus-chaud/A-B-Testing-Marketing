# Memoria Operativa de IA

Este archivo guarda decisiones de alto valor para no perder contexto entre sesiones/agentes.

## Como usarlo

- Agregar una entrada cuando se tome una decision tecnica relevante.
- Registrar solo senales utiles (no logs extensos).
- Revisar y depurar entradas obsoletas cada cierto tiempo.

## Plantilla de entrada

```md
## [YYYY-MM-DD] Titulo corto de decision

- Contexto:
- Decision:
- Motivo:
- Impacto (archivos/modulos):
- Riesgo:
- Seguimiento:
```

## Entradas

## [2026-02-25] Setup de orquestacion y patron dash-financiero

- Contexto: se solicito replicar en Marketing AB Testing el patron usado en dash-financiero (orquestador liviano, subagentes por rol, skills por dominio, verificacion contra requisitos, memoria persistente, enfoque spec-driven + TDD con IA).
- Decision: se creo `AGENTS.md` como router, skills modulares en `.cursor/skills/` (mab-orchestrator, mab-explorer, mab-spec-planner, mab-implementer, mab-validator, mab-senior-explainer, mab-doc-updater, ab-test-stats, ab-test-reporting), `docs/ai/memoria-operativa.md`, `docs/ai/acta-aprobacion-humana.md`, `.cursor/plans/` y estructura `tests/`.
- Motivo: estandarizar flujo de trabajo con gates humanos, specs verificables y memoria entre sesiones.
- Impacto (archivos/modulos): configuracion de agentes, documentacion operativa, estructura de proyecto.
- Riesgo: adopcion incompleta si no se respeta el flujo sugerido; rules existentes en `.cursor/rules/` pueden coexistir o migrarse a skills progresivamente.
- Seguimiento: validar en las proximas tareas si las rules actuales deben integrarse o migrarse al flujo AGENTS.md.

## [2026-02-25] Integracion ab-test-setup con skills locales

- Contexto: se incorpora ab-test-setup (marketingskills) para complementar ab-test-stats y ab-test-reporting.
- Decision: ab-test-setup cubre planificacion y checklist; ab-test-stats, calculos estadisticos; ab-test-reporting, comunicacion. Se agregan referencias cruzadas en las skills y flujo en AGENTS.md. Instalacion en `.cursor/skills/ab-test-setup/` (solo Cursor, solo este proyecto).
- Motivo: evitar solapamiento y habilitar handoffs claros entre skills.
- Impacto: AGENTS.md, ab-test-stats/SKILL.md, ab-test-reporting/SKILL.md, .cursor/skills/ab-test-setup/ (SKILL.md + references/).
- Riesgo: ab-test-setup adaptada localmente; cambios upstream en marketingskills no se propagan automaticamente.
- Seguimiento: revisar si product-marketing-context (dependencia de marketingskills) aporta valor al proyecto.

## [2026-02-25] Analisis inicial marketing_AB.csv

- Contexto: analisis de calidad de datos, planificacion del test A/B, ejecucion ads vs psa y analisis estacionalidad (most ads day).
- Decision: notebook `marketing_ab_analysis.ipynb` con carga, QA (nulos, duplicados, contaminacion usuario), balance de grupos, estacionalidad (dia/hora), test A/B one-sided (ads > psa), Chi² most_ads_day vs converted con post-hoc. Documentacion en README.md y docs/analisis-marketing-ab.md.
- Motivo: validar datos, aplicar framework ab-test-setup/ab-test-stats y obtener conclusion accionable.
- Impacto: marketing_ab_analysis.ipynb, README.md, docs/analisis-marketing-ab.md.
- Riesgo: dataset desbalanceado (96% ad, 4% psa) ignorado por decision explicita.
- Seguimiento: analisis most_ads_hour; reporte con ab-test-reporting; dashboard Streamlit.
