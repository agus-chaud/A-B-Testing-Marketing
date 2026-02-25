---
name: mab-orchestrator
description: "Orquesta tareas en Marketing AB Testing con minimo contexto y maximo foco"
version: 1.0.0
author: "Equipo Marketing AB Testing"
---

# mab-orchestrator

## Cuando usar

- Pedido ambiguo o amplio.
- Cambio que toca multiples modulos, notebooks o datos.
- Necesidad de dividir en subagentes/pasos.

## Objetivo

Transformar un pedido en un plan ejecutable de bajo riesgo para este repo.

## Salida obligatoria

1. Objetivo (1-2 lineas).
2. Alcance (archivos/modulos/datos probables).
3. Secuencia de skills a activar.
4. Riesgos principales.
5. Criterios de cierre.

## Reglas

- No implementar codigo aqui.
- Reducir alcance antes de delegar.
- Si el cambio es pequeno, evitar sobre-orquestar y delegar directo a implementacion.
