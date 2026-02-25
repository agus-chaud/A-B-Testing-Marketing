---
name: mab-implementer
description: "Implementa cambios en Marketing AB Testing siguiendo spec, PEP 8 y foco en legibilidad"
version: 1.0.0
author: "Equipo Marketing AB Testing"
---

# mab-implementer

## Cuando usar

- Cuando existe spec clara y alcance definido.

## Principios de implementacion

- Preferir funciones puras y nombres descriptivos.
- Priorizar operaciones vectorizadas con pandas/numpy.
- Mantener compatibilidad con flujos existentes (notebooks, scripts, dashboards).
- Cambiar lo minimo necesario para cumplir criterios.

## Checklist antes de cerrar

1. El codigo cumple el objetivo sin side effects innecesarios.
2. No rompe pipelines de datos ni formatos de salida esperados.
3. Mantiene consistencia con README y documentacion existente.
