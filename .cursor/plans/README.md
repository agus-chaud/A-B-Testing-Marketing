# Plans (Spec-Driven)

Aqui se almacenan los planes de implementacion en formato spec-driven.

## Formato de plan

Cada plan es un archivo `.plan.md` con frontmatter YAML y secciones:

```yaml
---
name: Nombre del plan
overview: Descripcion breve
todos: []
isProject: false
---
```

- **Contexto actual**: estado del proyecto antes del cambio.
- **Objetivo**: resultado esperado.
- **Decisiones de diseño**: opciones tomadas y razones.
- **Arquitectura**: diagramas Mermaid si aplica.
- **Tareas de implementacion**: pasos concretos.
- **Orden sugerido**: secuencia de ejecucion.
- **Riesgos y mitigaciones**.
- **Archivos a tocar**: tabla de impacto.

## Flujo

1. `mab-spec-planner` produce la spec.
2. Gate humano aprueba.
3. `mab-implementer` ejecuta siguiendo el plan.
4. `mab-validator` verifica contra criterios.
5. Registrar decision en `docs/ai/memoria-operativa.md`.
