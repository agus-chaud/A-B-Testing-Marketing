# Análisis marketing_AB.csv

Documento técnico del análisis realizado sobre el dataset del experimento ads vs psa.

## Dataset

| Campo | Tipo | Descripción |
|-------|------|-------------|
| user id | int | Identificador único de usuario |
| test group | object | "ad" (tratamiento) o "psa" (control) |
| converted | bool | True si convirtió |
| total ads | int | Total de anuncios mostrados |
| most ads day | object | Día con más anuncios (Monday-Sunday) |
| most ads hour | int | Hora con más anuncios (0-23) |

- **Filas:** ~588k
- **Balance:** 96% ad, 4% psa (intencionalmente no corregido)

## Hipótesis del test A/B

- **H0:** p_ad ≤ p_psa
- **H1:** p_ad > p_psa (lift relativo ≥ 10%)
- **α:** 0.05
- **Tipo:** one-sided

## Validaciones previas (QA)

| Check | Resultado |
|-------|-----------|
| Nulos | 0 en todas las columnas |
| user id duplicados | 0 |
| Usuarios en ambos grupos | 0 (sin contaminación) |
| Balance ad/psa | 96% / 4% |

## Resultados: ads vs psa

| Grupo | n | Conversiones | Tasa |
|-------|---|--------------|------|
| ad | 564,577 | 14,423 | 2.55% |
| psa | 23,524 | 420 | 1.79% |

- **Lift absoluto:** 0.77 pp
- **Lift relativo:** 43.09%
- **Z:** 7.37
- **p-value (one-sided):** ≈ 0
- **Conclusión:** Rechazar H0. Implementar ads.

## Resultados: most ads day vs converted

### Chi-cuadrado omnibus

- **χ²:** 410.05
- **p-value:** < 0.05
- **Conclusión:** Hay asociación entre día y conversión.

### Tasas por día

| Día | Tasa | n |
|-----|------|---|
| Monday | 3.28% | 87,073 |
| Tuesday | 2.98% | 77,479 |
| Wednesday | 2.49% | 80,908 |
| Thursday | 2.16% | 82,982 |
| Friday | 2.22% | 92,608 |
| Saturday | 2.11% | 81,660 |
| Sunday | 2.45% | 85,391 |

### Post-hoc: Monday vs Saturday

- **Mejor:** Monday (3.28%)
- **Peor:** Saturday (2.11%)
- **Lift relativo:** 55.9%
- **Z:** 14.86, **p-value:** ≈ 0
- **Conclusión:** Monday convierte significativamente más que Saturday.

## Fuentes

- Notebook: `marketing_ab_analysis.ipynb`
- Dataset: `marketing_AB.csv`
- Skills: ab-test-setup, ab-test-stats
