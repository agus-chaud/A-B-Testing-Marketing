---
name: mab-explorer
description: "Explora arquitectura de datos, notebooks y codigo de Marketing AB Testing; estima impacto"
version: 1.0.0
author: "Equipo Marketing AB Testing"
---

# mab-explorer

## Cuando usar

- Preguntas de descubrimiento: "donde esta", "como funciona", "que depende de".
- Antes de modificar analisis estadisticos, pipelines de datos o reportes.

## Checklist de exploracion

1. Identificar archivos objetivo en `data/`, `notebooks/`, `src/`, `config/`.
2. Trazar flujo: datos crudos -> transformacion -> analisis -> visualizacion/reporte.
3. Detectar efectos secundarios (formato de salida, dependencias entre notebooks).
4. Listar riesgos de regresion.

## Salida obligatoria

- Mapa breve de archivos relevantes.
- Hipotesis de impacto (bajo/medio/alto).
- Recomendacion de siguientes skills.
