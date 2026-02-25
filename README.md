# Marketing AB Testing

Herramientas de análisis de tests A/B para marketing: diseño estadístico, significancia, power analysis, reportes y visualizaciones 

---

## Contexto del negocio

### Problema y objetivo

**Problema:** Se necesita evaluar si exponer usuarios a anuncios promocionales (ads) en lugar de Public Service Announcements (psa) aumenta la tasa de conversión, con evidencia estadística suficiente para tomar decisiones de negocio.

**Objetivo:** Diseñar, ejecutar y documentar un test A/B que responda a la pregunta: *¿Los usuarios expuestos a ads tienen una tasa de conversión al menos 10% mayor que los expuestos a psa?* Con nivel de significancia α = 0.05 y criterio one-sided (H1: p_ad > p_psa).

---

## Enfoque y decisiones técnicas

### Metodología

- **Framework de planificación:** Analisis de hipótesis, variantes, métricas, checklist.
- **Test estadístico:** Z-test de dos proporciones (one-sided) para la comparación ads vs psa.
- **Implementación:** scipy para garantizar que se ejecute sin depender de statsmodels.
- **Validaciones previas:** completitud, unicidad de user id, ausencia de contaminación entre grupos.
- **Análisis complementarios:** Chi-cuadrado de independencia para estacionalidad (most ads day y most ads hour vs converted) con post-hoc mejor vs peor categoría.

### Pipeline

1. **Carga y exploración** → `marketing_AB.csv` (~588k filas, columnas: user id, test group, converted, total ads, most ads day, most ads hour).
2. **QA de datos** → nulos, duplicados, contaminación usuario (mismo user en ambos grupos).
3. **Balance de grupos** → distribución ad vs psa.
4. **Estacionalidad** → tasas por día y hora.
5. **Test A/B** → z-test one-sided, cálculo de lift, conclusión.
6. **Análisis día vs conversión** → Chi² omnibus + post-hoc Monday vs Saturday.
7. **Análisis hora vs conversión** → Chi² omnibus + post-hoc mejor vs peor hora (16h vs 2h).

Pipeline ejecutable en `marketing_ab_analysis.ipynb`.

---

## Resultado e Impacto

### Test A/B: ads vs psa

| Grupo | n | Conversiones | Tasa |
|-------|---|--------------|------|
| ads | 564,577 | 14,423 | 2.55% |
| psa | 23,524 | 420 | 1.79% |

- **Lift relativo:** 43.09% (ads es ~143% de psa).
- **Z = 7.37**, **p-value ≈ 0** (one-sided).
- **Conclusión:** Rechazamos H0. La tasa de conversión de ads es significativamente mayor que psa (p < 0.05) y supera el MDE objetivo (≥10%).

**Recomendación de negocio:** Implementar ads.

### Estacionalidad: most ads day vs converted

- **Chi²:** χ² = 410.05, p < 0.05 → hay asociación entre día y conversión.
- **Mejor día:** Monday (3.28%).
- **Peor día:** Saturday (2.11%).
- **Post-hoc:** Monday convierte significativamente más que Saturday (lift relativo 55.9%, p < 0.05).

**Recomendación:** Priorizar campañas entre semana, reducir intensidad los sábados.

### Estacionalidad: most ads hour vs converted

- **Chi²:** χ² = 430.77, p < 0.05 → hay asociación entre hora y conversión.
- **Mejor hora:** 16h (3.08%).
- **Peor hora:** 2h (0.73%).
- **Post-hoc:** La hora 16h convierte significativamente más que 2h (lift relativo 320.8%, p < 0.05).

**Recomendación:** Programar campañas preferentemente entre 14h y 20h; evitar o reducir intensidad en madrugada (0h–5h).

### Resumen de recomendaciones

| Análisis | Recomendación |
|----------|---------------|
| A/B ads vs psa | Implementar ads |
| most ads day | Priorizar entre semana, reducir sábados |
| most ads hour | Programar campañas 14h–20h, evitar madrugada |

---

## Principales desafíos y cómo se solucionaron

| Desafío | Solución |
|---------|----------|
| **Dependencia de statsmodels** | Implementación manual del z-test con scipy (proporción agrupada, SE, p-value one-sided) para evitar módulos externos. |
| **Múltiples grupos (día/hora)** | Chi-cuadrado omnibus para detectar asociación global; post-hoc one-sided (mejor vs peor categoría) para interpretación accionable. |

---

## Futuras mejoras

- [x] Análisis **most ads hour** vs converted (Chi² + post-hoc).
- [ ] Reporte formal con `ab-test-reporting` (visualizaciones, HTML/PDF).
- [ ] Dashboard interactivo (Streamlit) para exploración de resultados.
- [ ] Considerar corrección por desbalance (ponderation o re-muestreo) si se requiere análisis más conservador.
- [ ] Tests unitarios para funciones de estadística (tests/).
- [ ] Documentar product-marketing-context si se adopta la dependencia de marketingskills.

---

## Uso rápido

```bash
# Requisitos
pip install pandas numpy matplotlib seaborn scipy

# Ejecutar análisis
jupyter notebook marketing_ab_analysis.ipynb
```

Ver `AGENTS.md` para flujo de trabajo con agentes y skills.
