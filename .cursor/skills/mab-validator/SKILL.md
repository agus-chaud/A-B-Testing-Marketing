---
name: mab-validator
description: "Valida cambios con foco en regresiones funcionales y calidad minima (Marketing AB Testing)"
version: 1.0.0
author: "Equipo Marketing AB Testing"
---

# mab-validator

## Cuando usar

- Siempre despues de modificar codigo Python o notebooks.

## Validaciones minimas

1. Ejecutar flujo principal:
   - Scripts de analisis o `streamlit run` si hay dashboard.
2. Verificar que no hay errores obvios de import/sintaxis.
3. Revisar lints/diagnosticos de archivos editados.
4. Ejecutar tests si existen (`pytest tests/` o `python -m unittest`).
5. Confirmar que calculos estadisticos y reportes siguen operativos.

## Salida obligatoria

- Resultado de validacion (ok/fail).
- Riesgos residuales.
- Accion recomendada siguiente.
