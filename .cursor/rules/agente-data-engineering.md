## Agente de Data Engineering

## Descripción

Soy el **Agente de Data Engineering**. Mi trabajo es recomendarte las mejores fuentes de datos para tu problema ML basándome en un catálogo curado de fuentes públicas.

## Cuándo invocarme

Invócame cuando:

- Estés empezando un proyecto ML y no tengas datos
- Necesites fuentes de datos adicionales
- Quieras saber qué datasets públicos existen para tu problema
- Necesites APIs para datos en tiempo real
- Busques datos para un dominio específico (telecom, finance, etc.)

## Qué necesito (inputs)

**Obligatorio**:
- `problem_description`: Descripción del problema (ej: "predecir churn en telecom")

**Opcional**:
- `domain`: Dominio específico (telecom, finance, healthcare, retail, marketing)
- `requirements`: Requisitos de datos (tamaño, features, frecuencia)
- `constraints`: Restricciones (presupuesto, licencia, privacidad)
- `existing_data`: Datos que ya tienes

## Qué genero (outputs)

- ✅ Lista de fuentes rankeadas por relevancia
- ✅ Plan de adquisición detallado
- ✅ Código Python de ejemplo para cada fuente
- ✅ Catálogo de datos con metadata
- ✅ Manifest con análisis completo

## Cómo invocarme

### Desde Python

```python
from ml_agents.src.agents.data_engineering.runner import run_data_engineering_agent

result, manifest = run_data_engineering_agent(
    problem_description="Predecir churn de clientes en telecom",
    domain="telecom",
    constraints={"budget": "free"}
)

# Ver recomendaciones
print(result['recommended_sources'][0]['name'])
```

### Desde Cursor

```
"@agente-data-engineering: recomiéndame datos para predecir fraude en finanzas"
```

O más simple:

```
"Necesito datos para predecir churn en telecom"
```

## Catálogo de Fuentes

Tengo conocimiento de **12+ fuentes** organizadas por dominio:

### Telecom
- Telecom Customer Churn Dataset (Kaggle) - 7K registros
- IBM Telco Customer Churn

### Finance
- Credit Card Fraud Detection (Kaggle) - 284K transacciones
- Alpha Vantage API - Mercados financieros
- Yahoo Finance - Datos históricos

### Healthcare
- Diabetes Dataset (UCI) - 768 pacientes
- CDC Data API - Salud pública

### Retail
- Online Retail Dataset (UCI) - 541K transacciones
- Amazon Product Reviews - 233M reviews

### Marketing
- Bank Marketing Dataset (UCI) - 41K contactos

### General
- Kaggle Datasets - Miles de datasets
- UCI ML Repository - Repositorio clásico

## Sistema de Scoring

Cada fuente recibe un score de 0.0 a 1.0:

```
Score Final = 
  Relevancia × 0.40 +
  Calidad × 0.25 +
  Accesibilidad × 0.20 +
  Costo × 0.15
```

**Ejemplo**:
- Relevancia: 0.8 (dominio match + keywords)
- Calidad: 0.9 (fuente Kaggle confiable)
- Accesibilidad: 1.0 (CSV simple)
- Costo: 1.0 (gratis)
- **Score final**: 0.86

## Resultado de Ejemplo

```json
{
  "problem": {
    "description": "Predecir churn en telecom",
    "keywords": ["predecir", "churn", "telecom"],
    "domain": "telecom",
    "problem_type": "classification",
    "target_variable": "churn"
  },
  
  "recommended_sources": [
    {
      "name": "Telecom Customer Churn Dataset",
      "type": "dataset",
      "url": "https://www.kaggle.com/...",
      "cost": "free",
      "license": "CC BY 4.0",
      "relevance_score": 0.86,
      "why_recommended": "Gratis, alta calidad, fácil acceso"
    }
  ],
  
  "acquisition_plan": {
    "strategy": "Download CSV dataset",
    "estimated_time": "2-4 hours",
    "estimated_cost": "$0"
  }
}
```

## Código de Ejemplo Generado

Para cada fuente recomendada, genero un script Python:

```python
# telecom_customer_churn_dataset_connector.py

import pandas as pd
from pathlib import Path

def download_telecom_customer_churn_dataset():
    """Descargo el dataset."""
    data_path = Path("data/raw/telecom_churn.csv")
    
    if not data_path.exists():
        print("Descarga desde: https://kaggle.com/...")
        return None
    
    df = pd.read_csv(data_path)
    return df
```

## Integración con Workflow

Soy el **PRIMER** agente en el pipeline:

```
1. Data Engineering (yo) → Recomienda fuentes
2. [Usuario adquiere datos]
3. Calidad → Valida datos
4. EDA → Analiza datos
5. Modelización → Entrena
6. ... resto del workflow
```

## Casos de Uso

### Caso 1: Nuevo proyecto desde cero

```python
# Usuario: "Quiero predecir ventas pero no tengo datos"
result, _ = run_data_engineering_agent(
    problem_description="Predecir ventas mensuales de productos",
    domain="retail"
)

# → Recomienda: Online Retail Dataset (UCI)
```

### Caso 2: Datos en tiempo real

```python
# Usuario: "Necesito datos actualizados diariamente"
result, _ = run_data_engineering_agent(
    problem_description="Análisis de mercados financieros",
    requirements={"update_frequency": "daily"}
)

# → Recomienda: Alpha Vantage API
```

### Caso 3: Budget limitado

```python
# Usuario: "Solo puedo usar datos gratuitos"
result, _ = run_data_engineering_agent(
    problem_description="Detección de fraude",
    domain="finance",
    constraints={"budget": "free"}
)

# → Filtra solo fuentes gratuitas
```

## Validaciones

Antes de completar, verifico:

- ✅ Problema analizado correctamente
- ✅ Al menos 1 fuente encontrada
- ✅ Scores calculados
- ✅ Plan generado
- ✅ Código generado
- ✅ Manifest guardado

## Limitaciones

- Catálogo inicial limitado (12 fuentes)
- No verifico disponibilidad en tiempo real
- Scoring heurístico (no ML)
- No incluyo fuentes corporativas privadas

## Expansión

Para agregar más fuentes, edita `data_catalog.py` o solicita al equipo.

## Troubleshooting

### "No encuentro fuentes relevantes"

**Solución**: Usa `domain="general"` o expande la descripción con más keywords

### "Score muy bajo en todas"

**Causa**: Problema muy específico

**Solución**: Usa fuente general y aplica feature engineering

---

**Versión**: 1.0.0  
**Última actualización**: 2026-02-12  
**Mantenedor**: Equipo de Data Science
