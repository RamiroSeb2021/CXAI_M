# CXAI-M — Explainability in Machine Learning

**Curso:** Explicabilidad en Inteligencia Artificial (XAI)  
**Semestre:** 10.º  
**Entrega principal:** 9 de abril de 2026

Colección de notebooks y talleres que cubren técnicas de interpretabilidad de modelos ML: LIME, SHAP, algorithmic recourse, análisis de sesgo y robustez de explicaciones.

---

## 📚 Notebooks

### 1. LIME_SHAP_tabular.ipynb
**Tema:** Tutorial introductorio a LIME y SHAP en datos tabulares  
**Tipo:** Pedagógico + implementación  
**Nivel:** Principiante

**Dataset:** Sintético — educativo con 6 variables (horas de estudio, ausencias, tareas, participación, promedio previo, uso de plataforma)

**Modelos:** Random Forest (regresión para notas finales, clasificación para aprobación)

**Secciones principales:**
1. Importar librerías y crear datos sintéticos
2. Parte 1: Modelo de **regresión** (predicción de notas finales)
   - Entrenamiento de Random Forest
   - Predicciones y residuales
3. Parte 2: Modelo de **clasificación** (predicción de aprobación/reprobación)
   - Entrenamiento
   - Matriz de confusión
4. **LIME local:** explicar por qué el modelo predice una nota/resultado específico para un estudiante
   - Feature contributions lineales locales
   - Comparación de casos correctos vs incorrectos
5. **SHAP local y global:**
   - Waterfall plots (contribución de cada variable)
   - Summary plots (importancia global)
   - Dependence plots
6. **Comparación LIME vs SHAP:** ventajas y desventajas de cada técnica
7. **Permutation importance:** validación alternativa de importancia de features

**Conceptos clave:**
- Explicaciones **locales** (para una predicción específica)
- Explicaciones **globales** (importancia general del modelo)
- Cómo leer un waterfall plot de SHAP
- Diferencia entre LIME (aproximación local lineal) y SHAP (valores Shapley)

**Tiempo estimado:** 2-3 horas

---

### 2. Taller_LIME_SHAP_base_real.ipynb
**Tema:** Taller completo de analítica educativa e interpretabilidad  
**Tipo:** Taller (plantilla) + análisis  
**Nivel:** Intermedio

**Dataset:** Real — educativo de 2.393 estudiantes con 35 tipos de pruebas y 22 grados de escolaridad (Google Sheets)

**Modelos:** Random Forest (clasificación y regresión), Logistic Regression

**Secciones principales:**
1. **Lectura de datos:** desde Google Sheets
2. **Diagnóstico de la base de datos:**
   - Unidad de observación
   - Validación de integridad
   - Valores faltantes
3. **Exploración de datos (EDA):**
   - Distribución de notas finales
   - Proporción de aprobados/reprobados
   - Desempeño por grado escolar
   - Desempeño por tipo de prueba
   - Diferencias por grupo demográfico
   - Visualizaciones comparativas
4. **Modelado clasificación:**
   - Entrenamiento de Random Forest y Logistic Regression
   - Evaluación (accuracy, precision, recall, F1)
5. **Modelado regresión:**
   - Predicción de notas finales
   - Errores y residuales
6. **Interpretabilidad con LIME:**
   - Explicación de decisiones de clasificación
   - Predicciones individuales
7. **Interpretabilidad con SHAP:**
   - Explicaciones locales
   - Summary plots y dependence plots
8. **Comparación de técnicas:**
   - Cuándo usar LIME vs SHAP
   - Limitaciones en datos reales
9. **Discusión:**
   - Data leakage (variables que revelan el target)
   - Sesgos en el dataset
   - Utilidad real de las explicaciones
   - Próximos pasos en auditoría de modelos

**Conceptos clave:**
- **Data leakage:** variables que codifican información del target (ej: calificación en una prueba que predice la calificación final)
- Diferencia entre interpretabilidad de modelo e interpretabilidad de predicción
- Cómo explicar decisiones a stakeholders no técnicos
- Limitaciones de LIME/SHAP en datos con colinealidad

**Tiempo estimado:** 4-5 horas

---

### 3. Taller_LIME_SHAP_base_real_JJMJP.ipynb
**Tema:** Taller completado (entrega de estudiante)  
**Tipo:** Entrega  
**Nivel:** Intermedio

**Estructura:** Idéntica al notebook anterior (Taller_LIME_SHAP_base_real.ipynb)

**Estado:** Análisis completado con resultados, conclusiones y reflexiones sobre las técnicas de interpretabilidad aplicadas a datos educativos reales.

---

### 4. algorithmic_recourse_interpretable_colab_extended.ipynb ⭐
**Tema:** Algorithmic Recourse — explicaciones accionables  
**Tipo:** Tutorial + implementación  
**Nivel:** Avanzado  
**Importancia:** **NOTEBOOK CENTRAL DEL PROYECTO GRUPAL**

**Dataset:** Sintético — decisiones de aprobación de crédito con 3 variables: `education_years`, `income_k`, `savings_k`

**Modelo:** Logistic Regression (elegido por interpretabilidad)

**Secciones principales (16 secciones):**

#### Parte A: Fundamentos (secciones 1-5)
1. **Introducción a Algorithmic Recourse:** qué es y por qué importa
2. **Importar librerías**
3. **Crear dataset sintético:** casos de aprobación/rechazo de crédito
4. **Entrenar modelo interpretable:** Logistic Regression, explicar por qué elegir este modelo
5. **Interpretar el modelo:** lectura directa de coeficientes como regla de decisión

#### Parte B: Recourse manual (secciones 6-8)
6. **Definir acción, restricciones y costo:**
   - Qué es una acción (cambio en variables)
   - Qué restricciones existen (actionability)
   - Función de costo (minimizar cambios)
7. **Buscar recourse por fuerza bruta explicable:**
   - Espacio de búsqueda discreto
   - Exploración exhaustiva (educativo)
   - Encontrar el cambio mínimo para revertir rechazo
8. **Mostrar recourse interpretable:**
   - "Para ser aprobado, necesitás aumentar ingresos en X y educación en Y"
   - Explicación de contribuciones al score

#### Parte C: Enriquecimiento (secciones 9-11)
9. **Ver varias alternativas:** Pareto frontier de recourse (no solo una solución)
10. **Explicar por qué funciona:** descomposición de contribuciones al score
11. **Visualización antes/después:** gráficos claros del cambio

#### Parte D: Extensión temporal (secciones 12-13)
12. **Extensión temporal:** el recourse puede expirar si el modelo cambia
    - Simulación de reentrenamiento del modelo
    - ¿Sigue siendo válido el recourse?
13. **Evaluación temporal:** chequeo de robustez a lo largo del tiempo

#### Parte E: Evaluación en lote (secciones 14, 16)
14. **Evaluación en lote:** aplicar recourse a múltiples casos rechazados
    - Estadísticas de costo
    - Cobertura (qué porcentaje logra ser aprobado)
16. **Robustez temporal en lote:** ¿el recourse es robusto para todos los casos?

#### Parte F: Benchmark con DiCE (secciones sin número explícito)
- **Instalar DiCE:** framework automático de contrafactuales
- **Generar contrafactuales con DiCE:** dejar que un algoritmo busque recourse
- **Calcular costo:** evaluar con la misma métrica que el recourse manual
- **Comparar:** mejor recourse manual vs mejor contrafactual DiCE
- **Análisis detallado:** qué exactamente cambia en el mejor contrafactual

**Conceptos clave:**
- **Actionability:** no todas las variables pueden cambiar (ej: edad histórica)
  - Inmutable: no se puede cambiar (edad, historial)
  - Mutable: se puede cambiar (ingresos, educación)
  - Gradual: solo aumenta/disminuye (edad siempre crece)
- **Plausibilidad:** los cambios deben ser realistas
- **Costo:** minimizar la magnitud del cambio (L1, L∞, custom)
- **Diversidad:** múltiples soluciones en lugar de una sola
- **Robustez:** ¿el recourse sigue siendo válido si el modelo cambia?
- **Temporalidad:** las decisiones no son eternas

**Tiempo estimado:** 6-8 horas de lectura activa

---

### 5. contrafactuales_credito_sesgo_variables_es.ipynb
**Tema:** Contrafactuales y sesgo en sistemas de crédito  
**Tipo:** Análisis crítico + implementación  
**Nivel:** Avanzado

**Dataset:** Sintético — decisiones de crédito con variable protegida explícita (`es_negro`)

**Modelos:** Random Forest, Logistic Regression, Ridge Regression

**Secciones principales:**

#### Parte A: Clasificación (aprobación de crédito)
1. **Setup:** librerías y funciones auxiliares
2. **Crear dataset con sesgo intencional:** 
   - Variable objetivo: `aprobado` (sí/no)
   - Variable protegida: `es_negro` (0/1)
   - Correlación artificial de sesgo en el dataset
3. **Analizar tasas de aprobación por grupo:**
   - % aprobado para grupo 0
   - % aprobado para grupo 1
   - Identificar disparidad
4. **Entrenar modelo de clasificación**
5. **Auditar decisiones con 3 técnicas de importancia:**
   - **Coeficientes estandarizados:** influencia directa de cada variable
   - **Permutation importance:** degradación de desempeño al permutar
   - **Feature contributions:** impacto en la predicción individual
6. **Auditar caso individual:**
   - Tomar un caso y cambiar solo la variable protegida
   - ¿Cambia la decisión?
   - Conclusión: la variable está codificada aunque el modelo no la usa explícitamente
7. **Generar contrafactuales:**
   - Contrafactuales permitiendo cambiar TODAS las variables
   - Contrafactuales EXCLUYENDO la variable protegida
   - Comparación: ¿qué tan diferentes son?

#### Parte B: Regresión (tasa de interés)
8. **Analizar tasas de interés por grupo**
9. **Entrenar modelo de regresión**
10. **Auditar con las mismas técnicas**
11. **Auditar caso individual**
12. **Generar contrafactuales para mejorar tasa**

**Conceptos clave:**
- **Sesgo directo:** el modelo usa explícitamente una variable protegida
- **Sesgo indirecto (codificado):** el modelo no usa explícitamente la variable, pero está correlacionada con otros features
- **Proxy variables:** variables que correlacionan fuertemente con la protegida
- **Equidad vs accuracy:** trade-off entre desempeño y equidad
- **Auditoría de modelos:** cómo investigar si un modelo es discriminatorio

**Tiempo estimado:** 4-5 horas

---

### 6. notebook_xai_robustez_incertidumbre_monitoreo.ipynb
**Tema:** Robustez, incertidumbre y monitoreo de explicaciones XAI  
**Tipo:** Laboratorio + framework  
**Nivel:** Avanzado

**Dataset:** Breast Cancer (scikit-learn `load_breast_cancer()`) — 30 features de imágenes digitalizadas

**Modelo:** Random Forest Classifier

**Secciones principales:**

1. **Motivación:** 
   - Tema: no es suficiente generar explicaciones, hay que validar su calidad
   - Preguntas: ¿son las explicaciones estables? ¿reproducibles?
2. **Cargar datos y entrenar modelo**
3. **Explicaciones base (SHAP):**
   - Summary plots globales
   - Explicaciones locales por caso
4. **Robustez local (perturbación):**
   - Método: cambiar inputs ligeramente
   - Pregunta: ¿cambian las explicaciones?
   - Interpretación: si SHAP es inestable con pequeños cambios, cuidado
5. **Robustez por reentrenamiento:**
   - Método: re-entrenar el modelo múltiples veces
   - Pregunta: ¿la narrativa de SHAP sigue siendo la misma?
   - Caso: variable A es importante en run 1, pero no en run 2?
6. **Incertidumbre en explicaciones:**
   - Cuantificar confianza en las contribuciones
   - Distribuciones de SHAP values
7. **Monitoreo en producción:**
   - **Data drift:** cambio en la distribución de inputs
   - **Explanation drift:** cambio en las explicaciones generadas
   - Distinción crítica: performance del modelo ≠ estabilidad de explicaciones
8. **Framework para reportar:**
   - Cómo comunicar explicaciones con responsabilidad
   - Incluir disclaimers sobre incertidumbre

**Conceptos clave:**
- **Robustez local:** ¿qué tan sensibles son las explicaciones a cambios pequeños en inputs?
- **Robustez global:** ¿son las explicaciones estables a través de entrenamientos diferentes?
- **Incertidumbre en explicaciones:** no todas las explicaciones tienen la misma confianza
- **Drift vs drift de explicaciones:** cambio en datos ≠ cambio en explicaciones
- **Responsabilidad en XAI:** no presentar explicaciones como más confiables de lo que realmente son

**Tiempo estimado:** 3-4 horas

---

## 🔗 Dependencias conceptuales

```
LIME_SHAP_tabular.ipynb  (aprende LIME + SHAP básico)
        ↓
Taller_LIME_SHAP_base_real.ipynb  (aplica a datos reales)
        ↓
Taller_LIME_SHAP_base_real_JJMJP.ipynb  (entrega)

algorithmic_recourse_interpretable_colab_extended.ipynb  ⭐ CENTRAL
        ├→ contrafactuales_credito_sesgo_variables_es.ipynb
        │   (extiende: agregando auditoría de sesgo)
        │
        └→ notebook_xai_robustez_incertidumbre_monitoreo.ipynb
            (extiende: agregando validación de explicaciones)
```

---

## 🎯 Técnicas XAI — Mapa rápido

| Técnica | Pregunta que responde | Notebook |
|---------|----------------------|----------|
| **LIME** | "¿Por qué el modelo predijo X para este caso?" | LIME_SHAP_tabular, Taller_LIME_SHAP_* |
| **SHAP** | "¿Cuánto contribuyó cada variable a esta predicción?" | LIME_SHAP_tabular, Taller_LIME_SHAP_*, robustez |
| **Algorithmic Recourse** | "¿Qué debería cambiar para obtener otro resultado?" | algorithmic_recourse_* |
| **Contrafactuales** | "¿Cuál es el cambio mínimo para cambiar la predicción?" | algorithmic_recourse_*, contrafactuales_* |
| **Importancia de features** | "¿Cuáles variables son más importantes globalmente?" | LIME_SHAP_tabular, contrafactuales_* |
| **Auditoría de sesgo** | "¿El modelo discrimina contra grupos específicos?" | contrafactuales_credito_sesgo |
| **Robustez de XAI** | "¿Las explicaciones son estables y confiables?" | notebook_xai_robustez |

---

## 📊 Datasets

| Dataset | Fuente | Tipo | Uso | Problemas incluidos |
|---------|--------|------|-----|-------------------|
| Educativo sintético | `numpy` + educación | Sintético | LIME_SHAP_tabular | Ninguno (pedagogía pura) |
| Educativo real | Google Sheets (2.393 estudiantes) | Real | Taller_LIME_SHAP_* | Data leakage, sesgos reales |
| Crédito sintético | `numpy` | Sintético | algorithmic_recourse_* | Actionability, plausibilidad |
| Crédito con sesgo | `numpy` | Sintético | contrafactuales_credito_sesgo | Sesgo intencional en datos |
| Breast Cancer | `sklearn.datasets` | Real | notebook_xai_robustez | Drift, incertidumbre |
| UCI Adult Income | `data/archive/adult.csv` | Real | *Proyecto grupal* | Desbalance, categorías múltiples |

---

## 🚀 Setup y ejecución

### Requisitos
- Python 3.12+
- Poetry (gestor de dependencias)

### Instalación
```bash
# Clonar/descargar el repo
cd CXAI_M

# Instalar dependencias
poetry install

# Activar entorno
poetry shell

# O directamente (sin activar):
poetry run jupyter notebook notebooks/<nombre>.ipynb
```

### Dependencias principales
```toml
scikit-learn >= 1.8        # Modelos e interpretabilidad
lime >= 0.2               # LIME local explanations
shap >= 0.51              # SHAP values
ipykernel >= 7.2          # Jupyter support
```

### Instalar DiCE (cuando se use)
Algunos notebooks necesitan DiCE para contrafactuales automáticos:
```bash
# Dentro del notebook:
!pip install dice-ml
```

---

## 📅 Proyecto grupal (Entrega 9 de abril)

**Objetivo:** Adaptar `algorithmic_recourse_interpretable_colab_extended.ipynb` al dataset UCI Adult Income.

**Distribución de trabajo (5 personas):**

| Persona | Módulo | Responsabilidad |
|---------|--------|-----------------|
| **P1** | Integración | Liderazgo técnico, imports, integración total, narrativa |
| **P2** | Datos + modelo | Dataset, preprocesamiento, modelo interpretable, selección de casos |
| **P3** | Recourse manual | Restricciones, costo, búsqueda bruta, interpretación |
| **P4** | Visualización | Alternativas, explicación de cambios, visualizaciones |
| **P5** | Validación | Plausibilidad, lote, temporalidad, benchmark con DiCE |

**Timeline:** Ver `CRONOGRAMA.md`

---

## 📝 Convenciones

### Notebooks
- Variables de dominio en **español** (ej: `aprobado`, `tasa_interes`)
- Variables técnicas en **inglés** (ej: `X_train`, `feature_names`, `predictions`)
- Celdas markdown explicando cada sección ANTES del código
- Seed fija: `random_state=42`
- Rutas relativas (no hardcodeadas)

### Commits
Conventional commits con scope del módulo:
```
feat(recourse): implementar búsqueda bruta en adult dataset
fix(data): corregir codificación de variables categóricas
docs(lime-shap): agregar ejemplo de waterfall plot
analysis(sesgo): comparar tasas de aprobación por grupo
```

---

## 🎓 Referencias conceptuales

### Por qué Logistic Regression para recourse
Permite calcular directamente contribución de cada variable mediante coeficientes:
```
score = β₀ + β₁·education + β₂·income + β₃·savings
```
Cada cambio en variable tiene efecto predecible. Con Random Forest es más opaco.

### Actionability — Concepto crítico
- **Inmutable:** edad, raza, historial (no cambiar aunque fuera posible)
- **Mutable:** ingresos, educación, ahorro (sí pueden cambiar)
- **Gradual:** edad solo crece, sin regresión

Sin restricciones de actionability, el recourse no es útil en la realidad.

### Por qué monitorear explicaciones
Una explicación que cambia cada semana no es confiable. Hay que validar que las explicaciones sean estables.

---

## 📚 Para más contexto

- `AGENT.md` — Guía para agentes de IA
- `CRONOGRAMA.md` — Plan de proyecto, fases, dependencias

---

**Creado:** 5 de abril de 2026  
**Última actualización:** 5 de abril de 2026  
**Estado del proyecto:** En desarrollo (entrega 9 de abril)
