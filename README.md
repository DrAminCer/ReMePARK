# ReMePARK
ReMePARK – Mexican Parkinson's Disease Registry.  
Multicenter, longitudinal cohort capturing clinical, motor/non-motor, quality-of-life, and treatment data to advance research and patient care.

---

## 🧠 MDS-UPDRS Validation & Longitudinal Analysis

Este módulo forma parte del pipeline de análisis clínico y de calidad de datos del proyecto **ReMePARK**.  
Incluye procedimientos reproducibles para validar, limpiar y modelar las puntuaciones **MDS-UPDRS (Partes I–IV)**.

📁 **Ubicación:** [`notebooks/mdsupdrs_validation/`](notebooks/mdsupdrs_validation)

### Contenido principal

| Sección | Descripción |
|--------|-------------|
| **1. Validación estructural** | Identificación de columnas por parte (I–IV), control de tipos, valores y rangos válidos (0–4). |
| **2. Prorrateo y reglas de integridad** | Implementación de criterios de Goetz et al., 2015 para manejo de ítems faltantes. |
| **3. Cálculo de puntajes** | Totales por parte, puntaje global y clasificación leve–moderada–grave mediante triangulación de puntos de corte. |
| **4. Métricas longitudinales** | Cálculo de deltas, tiempo en años, pendiente anual y métricas intraindividuales. |
| **5. MCID y progresión clínica** | Detección de cambios clínicamente importantes y eventos de progresión (≥5 puntos en UPDRS III). |
| **6. Modelos mixtos** | Estimación de pendientes individuales mediante modelos lineales mixtos con pendiente aleatoria por paciente. |
| **7. Time-to-event** | Modelo de Cox Proportional Hazards para riesgo de progresión motora. |

---

### 🔬 Tecnologías utilizadas

- `pandas`, `numpy`, `matplotlib`, `seaborn`
- `statsmodels` (modelos mixtos)
- `lifelines` (CoxPH y supervivencia)
- `scikit-learn`

---

## 🩺 EQ-5D Crosswalk & Health Utility Analysis

Este módulo implementa el procesamiento completo del instrumento **EQ-5D-5L**, la conversión mediante **Crosswalk 5L→3L**, el cálculo de **índices de utilidad**, y análisis longitudinal de calidad de vida.

📁 **Ubicación:** [`notebooks/Remepark_EQ5.ipynb`](notebooks/Remepark_EQ5.ipynb)

### Contenido principal

| Sección | Descripción |
|--------|-------------|
| **1. Validación EQ-5D-5L** | Control de rangos permitidos (1–5), consistencia entre dominios y detección de valores faltantes. |
| **2. Crosswalk 5L** | Implementación del algoritmo EuroQol (Mexican Value Set, 2021). |
| **3. Utility Index** | Cálculo del índice de utilidad usando valores poblacionales correspondientes. |
| **4. Descriptivos y visualizaciones** | Distribuciones, boxplots, correlaciones internas y resumen estadístico. |
| **5. Modelado longitudinal** | Pendiente anual del índice EQ-5D, curvas de progresión y modelos mixtos. |
| **6. Integración clínica** | Asociación entre EQ-5D y escalas motoras/no motoras (UPDRS / NMS). |

---

## 🩺 Armonización NMSS → MDS-NMS

Módulo para transformar puntajes **NMSS** en valores comparables con los dominios de la **MDS-NMS**, permitiendo análisis coherentes entre periodos del estudio con diferentes instrumentos.

📁 **Ubicación:** [`notebooks/NMS_to_MDS_NMS.ipynb`](notebooks/NMS_to_MDS_NMS.ipynb)

### Contenido principal

| Sección | Descripción |
|--------|-------------|
| **1. Normalización porcentual** | Escalamiento lineal de puntajes NMSS y MDS-NMS al rango 0–100 %. |
| **2. Estandarización Z-score** | Conversión a desviaciones estándar para comparaciones relativas. |
| **3. Vinculación equipercentil** | Mapeo no paramétrico basado en igualación de percentiles. |
| **4. Mapeo conceptual** | Correspondencia explícita entre los 9 dominios NMSS y las secciones de MDS-NMS. |
| **5. Puntajes armonizados** | Exportación de dominios equivalentes para análisis longitudinal integrado. |

---
## 🩺 KPPS Pain Scale Processing

Este módulo implementa el flujo completo de limpieza, integración y estandarización de la **King’s Parkinson’s Disease Pain Scale (KPPS)** para análisis individuales y longitudinales dentro de ReMePARK. Incluye validación estricta, fusión multidimensional con bases clínicas y generación de un dataset final listo para análisis estadístico.

📁 **Ubicación:** [`notebooks/Preprocesamiento_KPPS.ipynb`](notebooks/Preprocesamiento_KPPS.ipynb)

### Contenido principal

| Sección | Descripción |
|--------|-------------|
| **Carga y limpieza de KPPS** | Importación desde Google Drive, filtrado de datos incompletos mediante listwise deletion. |
| **Identificación de cohorte** | Conteo de sujetos únicos y detección de la subpoblación longitudinal (≥ 2 visitas). |
| **Integración multidimensional** | Fusión con datos sociodemográficos, MDS-UPDRS y PDQ-39 mediante claves primarias combinadas. |
| **Control de calidad** | Outer join para maximizar retención, eliminación de registros fantasma, auditoría de datos faltantes. |
| **Persistencia del dataset final** | Exportación como `Remepark_cleaned_kpss.xlsx` listo para SPSS, R o Python. |

---
## 🩺 KPPS Longitudinal Pain Analysis

Este módulo evalúa la progresión del dolor en personas con Enfermedad de Parkinson utilizando la King’s Parkinson’s Disease Pain Scale (KPPS). A partir del dataset limpio generado por el módulo de procesamiento, se analiza la evolución del dolor entre la visita basal y la última visita disponible, así como la periodicidad del seguimiento clínico.

📁 **Ubicación:** [`notebooks/Delta_KPPS.ipynb`](notebooks/Delta_KPPS.ipynb)

### Contenido principal

| Sección | Descripción |
|--------|-------------|
| **Cohorte longitudinal** | Selección de pacientes con ≥ 2 visitas y consolidación del dataset analítico. |
| **Auditoría temporal** | Cálculo de intervalos entre visitas (TimeDelta) y estadísticas descriptivas del seguimiento. |
| **Análisis Pre–Post** | Comparación entre Baseline y Endpoint, cálculo del cambio absoluto (Δ KPPS). |
| **Pruebas estadísticas** | Shapiro–Wilk para normalidad y Wilcoxon Signed-Rank para evaluar significancia del cambio en dolor. |
| **Caracterización transversal** | Resumen demográfico inicial (Tabla 1), severidad por visita y análisis descriptivo por cohorte. |

---

## 🩺 KPPS Severity Levels & Progression Analysis

Este módulo analiza la severidad del dolor y su progresión longitudinal utilizando la escala King's Parkinson’s Disease Pain Scale (KPPS). Permite cuantificar cambios clínicos, clasificar severidad y evaluar predictores asociados al empeoramiento del dolor.

📁 **Ubicación:** [`notebooks/severidad_KPPS/`](notebooks/Severidad_KPPS.ipynb)


### Contenido principal

| Sección | Descripción |
|--------|-------------|
| **Configuración longitudinal** | Cálculo de intervalos entre visitas (TimeDelta), identificación de Baseline y Endpoint por sujeto. |
| **Análisis Pre–Post** | Cálculo de Δ KPPS, prueba de normalidad (Shapiro–Wilk) y Wilcoxon Signed-Rank para evaluar cambio clínico significativo. |
| **Transición categórica**| Matrices de transición entre niveles de severidad y prueba de simetría de Bowker para evaluar cambios ordinales. |
| **Factores asociados** | Evaluación de predictores demográficos y motores (sexo, edad, UPDRS, LEDD, duración de enfermedad) mediante χ² y Kruskal-Wallis. |
| **Fenotipado de severidad** | Clasificación en grupos Mild, Moderate, Severe, Very Severe mediante cuartiles poblacionales. |
| **Exportación** | Generación del archivo `Remepark_kpps_with_groups.xlsx` con el fenotipo final de severidad. |

---

## 🩺 KPPS MCID (Minimal Clinically Important Difference)

Este módulo evalúa la relevancia clínica del cambio en el dolor utilizando la KPPS. A diferencia de los análisis previos que se centran en la significancia estadística, este módulo determina si la mejoría observada es suficientemente grande como para ser percibida por el paciente (MCID) y analiza los factores que predicen dicha mejoría.

📁 **Ubicación:** [`notebooks/MCID_KPPS/`](notebooks/MCID_KPPS.ipynb)


### Contenido principal

| Sección | Descripción |
|--------|-------------|
| **Cálculo del cambio individual** | Estimación de Δ KPPS (Final – Basal) por sujeto. |
| **Definición del umbral clínico** | MCID definido como reducción ≥ 3 puntos en el total KPPS. Clasificación en Respondedores vs No Respondedores. |
| **Comparación entre grupos** | Mann–Whitney para predictores numéricos y Chi-Cuadrado (χ²) para predictores categóricos. |
| **Identificación de predictores** | Variables demográficas y motoras asociadas con alcanzar el MCID (p < 0.05). |
| **Visualizaciones** | Boxplots y gráficos comparativos entre respondedores y no respondedores. |
| **Exportación** | Archivo enriquecido con la variable MCID_Response (`Yes/No`). |

---

## 🧠 Control de calidad del MoCA

Este módulo revisa la consistencia de los puntajes del **Montreal Cognitive Assessment (MoCA)** en bases de ReMePARK. Valida los ítems, recalcula subtotales y totales, y señala registros que requieren revisión contra el formulario original. El archivo de entrada no se modifica.

📁 **Ubicación:** [`notebooks/Validacion MoCA.ipynb`](notebooks/QC_MoCA_ReMePARK_Colab.ipynb)

### Contenido principal

| Sección                      | Descripción                                                                                                                                                                 |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Validación de ítems**      | Detección de valores faltantes, no enteros o fuera del rango permitido para cada ítem.                                                                                      |
| **Subtotales y total**       | Recálculo de los dominios y del puntaje total directamente a partir de los ítems; comparación con los valores registrados.                                                  |
| **Corrección educativa**     | Verificación del punto adicional registrado en `PT.educ` y del total corregido, con límite de 30 puntos.                                                                    |
| **Clasificación**            | Comparación de las categorías registradas con las esperadas según los puntos de corte de 26 y 24 utilizados en la base.                                                     |
| **Memory Index Score (MIS)** | Verificación de su rango y de su compatibilidad con el recuerdo libre. No se recalcula el MIS exacto porque la base no contiene las respuestas con pistas y reconocimiento. |
| **Reporte de incidencias**   | Exportación de un Excel con resumen por fila, detalle de hallazgos y copia de los datos originales.                                                                         |

### Ejecución

Abre el notebook en **Google Colab**, ejecuta las celdas en orden y sube un archivo Excel con los encabezados esperados y los registros en `Hoja1`. Al finalizar, se descargará `QC_MoCA_ReMePARK.xlsx`.

Las incidencias indican datos que deben cotejarse con la fuente original. Una fila sin incidencias pasó las comprobaciones programadas, pero esto no confirma por sí solo la exactitud de las respuestas registradas ni constituye una clasificación diagnóstica.

---

---
### 🔧 Librerías utilizadas

- Python 3.9+  
- pandas, numpy  
- matplotlib, seaborn  
- statsmodels  
- scikit-learn  
- lifelines  

---


---

## 🔒 Uso

**No subir información identificable o sensible.**  
**Todos los cuadernos están diseñados para ejecutarse con datos anonimizados siguiendo la estructura definida en este repositorio.**

---

## 📜 Licencia

**Código bajo licencia MIT.** 
**Documentos y resultados derivados bajo licencia CC BY-NC 4.0.**

---





