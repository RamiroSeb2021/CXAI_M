# CXAI-M — Agent Guidelines

## How to Use This Guide

- Start here for entender el contexto del proyecto antes de tocar cualquier notebook.
- El proyecto es académico: XAI (Explainability in Machine Learning), 10.º semestre.
- El entregable central es una adaptación de `algorithmic_recourse_interpretable_colab_extended.ipynb` con un dataset diferente (UCI Adult Income).

## Available Skills

| Skill | Description | Path |
|-------|-------------|------|
| `skill-creator` | Create new AI agent skills | `skills/skill-creator/SKILL.md` |
| `skill-sync` | Sync and regenerate skill registry | `skills/skill-sync/SKILL.md` |

---

## Project Overview

**CXAI-M** es un curso sobre Explainability in Machine Learning. El repositorio contiene:

| Componente | Ubicación | Descripción |
|------------|-----------|-------------|
| Notebooks | `notebooks/` | Talleres y tutoriales XAI |
| Datos | `data/archive/` | UCI Adult Income dataset |
| Skills | `skills/` | Skills para agentes de IA |

**Stack:** Python 3.12+, scikit-learn, LIME, SHAP, DiCE, Poetry

---

## Notebooks — Mapa de dependencias conceptuales

```
LIME_SHAP_tabular.ipynb
    └── Taller_LIME_SHAP_base_real.ipynb   (aplica LIME+SHAP a datos reales)
        └── Taller_LIME_SHAP_base_real_JJMJP.ipynb  (entrega completada)

algorithmic_recourse_interpretable_colab_extended.ipynb  ← NOTEBOOK CENTRAL
    └── contrafactuales_credito_sesgo_variables_es.ipynb  (extiende con sesgo/equidad)
    └── notebook_xai_robustez_incertidumbre_monitoreo.ipynb  (extiende con robustez)
```

---

## Técnicas XAI — Resumen rápido

| Técnica | Cuándo usarla | Notebook de referencia |
|---------|---------------|----------------------|
| **LIME** | Explicación local de una predicción individual | `LIME_SHAP_tabular` |
| **SHAP** | Explicación local Y global, valores de contribución | `LIME_SHAP_tabular`, `Taller_LIME_SHAP_*` |
| **Algorithmic Recourse** | "¿Qué debería cambiar para obtener otro resultado?" | `algorithmic_recourse_*` |
| **DiCE** | Recourse automático con diversidad de contrafactuales | `algorithmic_recourse_*` |
| **Contrafactuales** | Mínimo cambio para cambiar la decisión | `contrafactuales_credito_*` |
| **Drift de explicaciones** | Monitoreo de estabilidad en producción | `notebook_xai_robustez_*` |

---

## Trabajo grupal — Proyecto principal

**Objetivo:** adaptar `algorithmic_recourse_interpretable_colab_extended.ipynb` al dataset UCI Adult Income (`data/archive/adult.csv`).

**Distribución del equipo (5 personas):**

| Persona | Módulo | Secciones del notebook |
|---------|--------|----------------------|
| Persona 1 | Integración + liderazgo | Introducción, imports, integración total |
| Persona 2 | Datos + modelo interpretable | Secciones 2, 3, 4, 5 |
| Persona 3 | Recourse manual + restricciones | Secciones 6, 7, 8 + reglas de actionability |
| Persona 4 | Alternativas + visualización | Secciones 9, 10, 11 + contribuciones |
| Persona 5 | Robustez + DiCE + evaluación en lote | Secciones 12, 13, 14, 16 + benchmark DiCE |

**Fecha de entrega:** 9 de abril de 2026. Ver `CRONOGRAMA.md` para el plan detallado.

---

## Development

```bash
# Setup
poetry install

# Activar entorno y abrir un notebook
poetry run jupyter notebook notebooks/<nombre>.ipynb

# Instalar DiCE (cuando se necesite, dentro del notebook)
!pip install dice-ml
```

---

## Commit Guidelines

Seguir conventional commits: `<type>[scope]: <description>`

**Types:** `feat`, `fix`, `docs`, `chore`, `refactor`, `analysis`

**Scopes sugeridos:** `recourse`, `lime-shap`, `contrafactuales`, `robustez`, `data`, `notebook`

**Ejemplos:**
```
feat(recourse): implementar búsqueda bruta de recourse para adult dataset
fix(data): corregir codificación de variables categóricas en adult.csv
docs(recourse): agregar explicación de restricciones de actionability
analysis(dice): comparar recourse manual vs contrafactuales DiCE
```

---

## Auto-invoke Actions

Cuando realices estas acciones, seguí las guías correspondientes:

| Acción | Guía |
|--------|------|
| Modificar o crear un notebook | Respetar estructura narrativa existente (celdas markdown + código) |
| Agregar técnica XAI nueva | Verificar que la técnica esté en contexto del curso primero |
| Crear nueva skill | Usar `skills/skill-creator/SKILL.md` |
| Hacer commit | Usar conventional commits con scope del módulo |

---

## Convenciones de código (notebooks)

1. **Celdas markdown antes de cada sección:** explicar el concepto antes del código
2. **Variables en español** cuando reflejan el dominio del problema (ej: `aprobado`, `tasa_interes`)
3. **Variables técnicas/ML en inglés** (ej: `X_train`, `feature_names`, `shap_values`)
4. **Seed fija:** siempre usar `random_state=42` para reproducibilidad
5. **No hardcodear rutas absolutas:** usar rutas relativas desde la raíz del repo
6. **Outputs visibles:** ejecutar el notebook completo antes de commitear

---

## Contexto conceptual clave

### Algorithmic Recourse vs Contrafactuales
- **Contrafactual puro:** el cambio mínimo para cambiar la predicción, sin importar si es posible en la realidad
- **Recourse algorítmico:** el cambio mínimo que ES POSIBLE hacer (accionable), respetando restricciones de plausibilidad

### Actionability constraints
- Variables **inmutables:** no se pueden cambiar (ej: edad, raza, historial)
- Variables **mutables:** se pueden cambiar con esfuerzo (ej: ingresos, educación, ahorro)
- Variables **semi-mutables:** se pueden cambiar pero solo en una dirección (ej: edad solo aumenta)

### Por qué Logistic Regression para recourse
Permite calcular directamente la contribución de cada variable al score mediante los coeficientes, haciendo el recourse interpretable sin técnicas adicionales.
