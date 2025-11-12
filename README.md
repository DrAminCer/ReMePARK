# ReMePARK
ReMePARK – Mexican Parkinson's Disease Registry. Multicenter, longitudinal cohort capturing clinical, motor/non-motor, and treatment data to advance research and care. 
---

## 🧠 MDS-UPDRS Validation & Longitudinal Analysis

Este módulo forma parte del pipeline de análisis clínico y de calidad de datos del proyecto **ReMePARK**.  
Contiene procedimientos reproducibles para validar, limpiar y analizar las puntuaciones **MDS-UPDRS (Partes I–IV)** de los participantes de la cohorte.

📁 **Ubicación:** [`notebooks/mdsupdrs_validation/`](notebooks/mdsupdrs_validation)

### Contenido principal

| Sección | Descripción |
|:--------|:-------------|
| **1. Validación estructural** | Identificación y verificación de columnas UPDRS I–IV; control de valores válidos (0–4). |
| **2. Prorrateo y reglas de integridad** | Aplicación de criterios de Goetz et al. 2015 para manejo de ítems faltantes por parte. |
| **3. Cálculo de puntajes** | Totales por parte y puntaje global MDS-UPDRS; clasificación de severidad leve–moderada–grave. |
| **4. Métricas longitudinales** | Deltas, pendientes anuales y modelado mixto de progresión motora (Parte III). |
| **5. MCID y progresión clínica** | Detección de cambios clínicamente importantes (MCID) y eventos de progresión ≥ 5 pts. |
| **6. Time-to-event** | Implementación de modelos de supervivencia (Cox PH) para análisis de riesgo de progresión. |

---

### 🔬 Tecnologías y librerías principales

- `pandas`, `numpy`, `matplotlib`, `seaborn`  
- `statsmodels` (modelos lineales mixtos)  
- `lifelines` (análisis de supervivencia)  
- `scikit-learn` (métricas complementarias y regresiones auxiliares)

---

### 🧩 Estructura recomendada



## Usage
Do not upload PHI or raw data.
Scripts in scripts/; notebooks in notebooks/.

## License
Code: MIT. Documents/data: CC BY-NC 4.0.
