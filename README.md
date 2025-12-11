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
| **2. Crosswalk 5L→3L** | Implementación del algoritmo EuroQol (van Hout et al., 2012). |
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





