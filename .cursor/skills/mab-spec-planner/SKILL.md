---
name: mab-spec-planner
description: "Define especificaciones breves y verificables antes de implementar (Marketing AB Testing)"
version: 1.0.0
author: "Equipo Marketing AB Testing"
---

# mab-spec-planner

## Cuando usar

- Cambios medianos/grandes.
- Ajustes de logica de negocio, calculos estadisticos o criterios de analisis A/B.

## Plantilla de spec (obligatoria)

1. **Contexto:** que problema se resuelve.
2. **Objetivo:** resultado esperado.
3. **No-objetivos:** que no se tocara.
4. **Criterios de aceptacion:** verificables.
5. **Riesgos:** posibles regresiones.
6. **Plan minimo de pruebas:** ejecuciones/manual checks.

## Reglas

- Evitar especificaciones vagas.
- Si no hay criterio de aceptacion, no pasar a implementacion.
- Documentar asunciones estadisticas (alpha, power, MDE) si aplican.
