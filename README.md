# Plan de proyecto para replicar y adaptar `algorithmic_recourse_interpretable_colab_extended.ipynb`

## Objetivo del proyecto

Replicar la lógica del notebook `algorithmic_recourse_interpretable_colab_extended.ipynb` con un conjunto de datos diferente, manteniendo el enfoque de **algorithmic recourse interpretable**, documentando cada etapa, validando resultados y dejando una versión final reproducible antes del **9 de abril**.

---

## Supuestos de gestión

* El equipo está compuesto por **5 personas**.
* El entregable final es un **notebook funcional, entendible, documentado y validado**.
* Se requiere no solo adaptar el código, sino también **entender, justificar y presentar** los resultados.
* La ruta crítica del proyecto está en: **dataset → modelo → restricciones/actionability → búsqueda de recourse → comparación con DiCE → validación final**.

---

## Propuesta de distribución del proyecto entre 5 personas

La división se hace por **módulos funcionales** del notebook, intentando minimizar bloqueos y repartir tanto carga técnica como carga de validación/documentación.

### Persona 1 — Líder de integración y estructura base del notebook

**Responsabilidad principal:** ensamblar el flujo completo, controlar consistencia técnica y unir los aportes del equipo.

**Encabezados del notebook a su cargo (responsabilidad directa):**

* 1. Algorithmic Recourse
* 1. Importar librerías

**Encabezados bajo su responsabilidad transversal (integración):**

* Integración de TODAS las secciones del notebook
* Revisión de reproducibilidad (ejecución de inicio a fin)
* Limpieza final (orden, comentarios, narrativa)
* Redacción de introducción global y conclusiones finales

**Entregables:**

* Notebook maestro integrado
* Flujo completo ejecutable
* Versión final lista para entrega

**Perfil ideal:**
persona con visión global, buena capacidad de organización, control de versiones y depuración.

persona con visión global, buena capacidad de organización, control de versiones y depuración.

---

### Persona 2 — Datos y entrenamiento del modelo interpretable

**Responsabilidad principal:** adaptar la parte inicial del pipeline al nuevo dataset y asegurar que el modelo sea interpretable y funcional.

**Encabezados del notebook a su cargo:**

* 2. Crear un dataset sintético (adaptado a dataset real)
* 3. Entrenar un modelo interpretable
* 4. Interpretar el modelo
* 5. Elegir un caso rechazado para hacer recourse

**Entregables:**

* Dataset limpio y documentado
* Modelo interpretable funcional
* Interpretación clara del modelo
* Selección de casos rechazados

**Perfil ideal:**
persona fuerte en preprocesamiento, modelado supervisado e interpretación.

persona fuerte en preprocesamiento, modelado supervisado e interpretación.

---

### Persona 3 — Reglas, restricciones, costo y búsqueda manual de recourse

**Responsabilidad principal:** construir el núcleo metodológico del recourse explicable.

**Encabezados del notebook a su cargo:**

* 6. Definir acción, restricciones y costo
* Definición de reglas de actionability
* 7. Buscar recourse por fuerza bruta explicable
* Funciones de recourse y lectura de los resultados
* 8. Mostrar el recourse de forma interpretable
* Resumen simple del recourse e interpretación de los resultados

**Entregables:**

* Reglas de actionability claras
* Función de costo definida
* Motor de recourse manual funcionando
* Primer resultado interpretable

**Perfil ideal:**
persona metódica, fuerte en lógica de negocio y restricciones.

persona metódica, fuerte en lógica de negocio, optimización sencilla y lectura cuidadosa de restricciones.

---

### Persona 4 — Alternativas, explicación causal/funcional y visualización

**Responsabilidad principal:** enriquecer la salida del recourse para que sea entendible y comunicable.

**Encabezados del notebook a su cargo:**

* 9. Ver varias alternativas, no solo una
* 10. Explicar por qué funciona el cambio
* Explicación de contribuciones al score y lectura de los resultados
* 11. Visualización sencilla del antes y después

**Entregables:**

* Alternativas de recourse ordenadas
* Explicación del impacto de cada cambio
* Visualizaciones claras antes/después

**Perfil ideal:**
persona con buena capacidad analítica y visualización.

persona con buena capacidad analítica, storytelling técnico y visualización de resultados.

---

### Persona 5 — Robustez, plausibilidad, evaluación en lote y benchmark con DiCE

**Responsabilidad principal:** hacer la validación avanzada del proyecto y comparar contra un método externo.

**Encabezados del notebook a su cargo:**

* 12. Extensión temporal: el recourse puede vencerse
* Chequeo temporal del recourse e interpretación de los resultados
* 13. Introducir plausibilidad y acción parcial
* Restricciones de plausibilidad y búsqueda de recourse filtrado
* 14. Evaluación en lote sobre varios casos rechazados
* 16. Robustez temporal en lote
* Instalar y correr DiCE sobre tu caso actual
* Calcular costo de los contrafactuales de DiCE con tu misma métrica
* Comparar el mejor recourse manual vs el mejor contrafactual de DiCE
* Ver exactamente qué cambia en el mejor contrafactual de DiCE

**Entregables:**

* Evaluación en lote
* Análisis de robustez
* Implementación de plausibilidad
* Comparación con DiCE

**Perfil ideal:**
persona fuerte en validación y experimentación.

persona fuerte en validación, experimentación y comparación de métodos.

---

## Organización recomendada del trabajo

## Frente 1: Base técnica

Lo conforman Persona 1 y Persona 2.

Su meta es dejar listo rápidamente:

* dataset
* notebook base
* modelo interpretable
* selección de casos rechazados

## Frente 2: Núcleo de recourse

Lo lidera Persona 3, con apoyo posterior de Persona 4.

Su meta es dejar funcionando:

* restricciones
* costos
* búsqueda de recourse
* lectura e interpretación inicial

## Frente 3: Validación avanzada y comparación

Lo lidera Persona 5.

Su meta es robustecer el proyecto con:

* plausibilidad
* evaluación en lote
* temporalidad
* benchmark con DiCE

---

## Dependencias clave

1. **La Persona 2 debe terminar una primera versión del dataset y modelo** para que las Personas 3, 4 y 5 trabajen sobre el mismo caso base.
2. **La Persona 3 depende del caso rechazado y del modelo** para construir el recourse manual.
3. **La Persona 4 depende de la salida de Persona 3** para explicar y visualizar alternativas.
4. **La Persona 5 depende parcialmente de Persona 3** para comparar recourse manual vs DiCE.
5. **La Persona 1 depende de todos**, pero debe ir integrando desde el inicio, no solo al final.

---

## Cronograma para terminar antes del 9 de abril

**Fecha de inicio sugerida:** 27 de marzo
**Fecha límite interna de cierre técnico:** 7 de abril
**Fecha límite de pulido final:** 8 de abril
**Margen de seguridad:** 9 de abril

---

## Fase 1 — Arranque y definición (27 al 28 de marzo)

### 27 de marzo

**Todo el equipo**

* Revisar el notebook original completo
* Entender el flujo de punta a punta
* Definir dataset alternativo
* Acordar repositorio, ramas, convenciones y entregables

**Resultado esperado:**

* mapa del proyecto
* criterios de éxito
* responsable por sección

### 28 de marzo

**Persona 1**

* Crear notebook maestro y estructura de trabajo

**Persona 2**

* Explorar dataset, variable objetivo, limpieza inicial

**Persona 3**

* Analizar cómo se definirá actionability y costo en el nuevo contexto

**Persona 4**

* Diseñar esquema de visualizaciones y formato de salidas explicativas

**Persona 5**

* Revisar requisitos para plausibilidad, robustez y uso de DiCE

**Resultado esperado:**

* estructura de trabajo lista
* dataset preliminar aceptado
* diseño metodológico inicial

---

## Fase 2 — Desarrollo del caso base (29 de marzo al 1 de abril)

### 29 de marzo

**Persona 2**

* Terminar preparación del dataset
* Entrenar primer modelo interpretable

**Persona 1**

* Integrar imports, configuración y flujo inicial

### 30 de marzo

**Persona 2**

* Interpretar modelo
* Seleccionar casos rechazados viables

**Persona 3**

* Formalizar reglas de actionability, restricciones y función de costo

### 31 de marzo

**Persona 3**

* Implementar búsqueda de recourse por fuerza bruta o equivalente explicable

**Persona 1**

* Probar ejecución parcial de notebook integrado

### 1 de abril

**Persona 3**

* Obtener primer recourse manual funcional

**Persona 4**

* Comenzar explicación del cambio y visualizaciones antes/después

**Hito de fase:**
Ya debe existir un **caso completo de recourse manual funcionando**.

---

## Fase 3 — Enriquecimiento y validación avanzada (2 al 5 de abril)

### 2 de abril

**Persona 4**

* Construir sección de múltiples alternativas
* Explicar contribuciones al score

**Persona 5**

* Implementar plausibilidad y acción parcial

### 3 de abril

**Persona 5**

* Ejecutar evaluación en lote sobre varios casos rechazados
* Diseñar chequeo de robustez temporal

**Persona 1**

* Consolidar avances y detectar incompatibilidades

### 4 de abril

**Persona 5**

* Instalar y correr DiCE en el caso actual
* Calcular costos comparables con la misma métrica

### 5 de abril

**Persona 5**

* Comparar mejor recourse manual vs mejor contrafactual DiCE
* Documentar diferencias exactas

**Hito de fase:**
Debe quedar terminada toda la **validación avanzada** y la **comparación metodológica**.

---

## Fase 4 — Integración, pruebas y cierre (6 al 8 de abril)

### 6 de abril

**Persona 1**

* Integración total del notebook
* Corrección de formato, orden y narrativa

**Todo el equipo**

* Prueba de ejecución completa desde cero
* Revisión de celdas rotas, dependencias y resultados inconsistentes

### 7 de abril

**Todo el equipo**

* Validación final técnica
* Ajustes de interpretación
* Refinamiento de conclusiones

**Fecha interna de cierre técnico**

### 8 de abril

**Persona 1 + apoyo del equipo**

* Pulido final
* Verificación de reproducibilidad
* Preparación de versión para entrega o sustentación

**Resultado esperado:**

* notebook final limpio
* narrativa coherente
* resultados defendibles

---

## 9 de abril — Entrega con margen de seguridad

Este día no debería usarse para desarrollar, sino solo para:

* contingencias
* reejecución final
* exportación
* envío

---

## Matriz resumida de asignación

| Persona   | Enfoque principal                         | Secciones                                  |
| --------- | ----------------------------------------- | ------------------------------------------ |
| Persona 1 | Integración y liderazgo técnico           | Introducción, imports, integración, cierre |
| Persona 2 | Datos y modelo interpretable              | 2, 3, 4, 5                                 |
| Persona 3 | Recourse manual explicable                | 6, reglas, 7, funciones, 8                 |
| Persona 4 | Alternativas, explicación y visualización | 9, 10, contribuciones, 11                  |
| Persona 5 | Plausibilidad, robustez, lote y DiCE      | 12, 13, 14, 16, benchmark DiCE             |

---

## Riesgos del proyecto

### Riesgo 1: escoger un dataset que no se adapte bien al recourse

**Mitigación:** seleccionar desde el inicio un dataset con variables claramente accionables y una variable objetivo binaria.

### Riesgo 2: el modelo no resulta suficientemente interpretable

**Mitigación:** usar desde el principio un modelo simple y transparente, priorizando interpretabilidad sobre desempeño extremo.

### Riesgo 3: la búsqueda de recourse explota combinatoriamente

**Mitigación:** limitar espacios de búsqueda, discretizar cambios y acordar reglas de plausibilidad temprano.

### Riesgo 4: DiCE genera contrafactuales difíciles de comparar

**Mitigación:** definir desde antes una métrica de costo común para evaluar tanto recourse manual como contrafactuales de DiCE.

### Riesgo 5: integración tardía del notebook

**Mitigación:** la Persona 1 debe integrar avances diariamente, no esperar al final.

---

## Recomendaciones de gestión

1. Trabajar con **ramas separadas por módulo**.
2. Hacer una **reunión corta diaria de 15 minutos** para bloqueos.
3. Definir desde el día 1:

   * nombre del dataset
   * variable objetivo
   * variables accionables
   * métrica de costo
4. Congelar el caso base a más tardar el **1 de abril**.
5. No dejar la comparación con **DiCE** para el final del todo; debe empezar máximo el 4 de abril.
6. Tener una versión ejecutable del notebook al menos desde el **6 de abril**.

---

## Ruta crítica del proyecto

La secuencia crítica es:

**Dataset adecuado → modelo interpretable → caso rechazado → reglas y costos → búsqueda de recourse → alternativas → plausibilidad/robustez → comparación con DiCE → integración final**

Si una de estas piezas se retrasa, compromete el cierre completo.

---

## Criterio de éxito final

El proyecto se considera terminado si al 8 de abril existe:

* un notebook que corre de inicio a fin,
* un dataset alternativo correctamente adaptado,
* al menos un recourse manual interpretable,
* evaluación sobre varios casos,
* comparación clara con DiCE,
* visualizaciones y explicaciones defendibles,
* narrativa final lista para entregar.

---

## Propuesta de liderazgo operativo

Se recomienda que la **Persona 1** actúe como coordinador general del proyecto y que cada persona entregue un avance integrable al final de cada día de trabajo.

Una regla simple de operación puede ser:

* **antes de las 2:00 p. m.**: desarrollo principal
* **después de las 2:00 p. m.**: integración, pruebas y reporte de bloqueos

Eso reduce el riesgo de descubrir incompatibilidades demasiado tarde.
