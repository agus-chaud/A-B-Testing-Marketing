---
name: ab-test-stats
description: "Diseno de experimentos A/B, power analysis, calculo de significancia estadistica"
version: 1.0.0
author: "Equipo Marketing AB Testing"
---

# ab-test-stats

## Cuando usar

- Disenar tamanos de muestra para experimentos A/B.
- Calcular poder estadistico (power) y MDE (Minimum Detectable Effect).
- Determinar significancia (p-value, intervalos de confianza).
- Elegir test estadistico (z-test, t-test, chi-cuadrado, etc.) segun tipo de metrica.
- Validar supuestos (normalidad, varianzas homogeneas).

## Skills relacionadas

- `ab-test-setup`: usa esta skill para obtener hipotesis, tipo de metrica y MDE objetivo; devuelve calculos precisos (tablas de ab-test-setup son referencias rapidas).
- `ab-test-reporting`: los resultados (n, p-value, IC) alimentan visualizaciones y reportes.

## Checklist

1. Identificar tipo de metrica (binaria, continua, ratio).
2. Definir alpha, power y MDE esperado.
3. Seleccionar test adecuado (proporciones vs medias).
4. Verificar supuestos del modelo.
5. Documentar decision en spec o memoria operativa.

## Salida tipica

- Tamano de muestra recomendado.
- Formula o funcion usada (scipy.stats, statsmodels).
- Interpretacion de resultados (rechazar/no rechazar H0).
- Recomendacion: si hace falta reporte o dashboard, activar `ab-test-reporting`.
