# Diferencia Mínima Clínicamente Importante (MCID) en KPPS

Este módulo evalúa la **relevancia clínica** de los cambios en la escala King's Parkinson’s Disease Pain Scale (KPPS).  
Mientras los análisis previos se centraron en la significancia estadística (p-value), este cuaderno determina si la mejoría observada es lo suficientemente grande como para ser **percibida como beneficiosa por el paciente**, es decir, si alcanza la *Diferencia Mínima Clínicamente Importante (MCID)*.

El análisis se basa en los datos longitudinales depurados y clasificados en severidad provenientes de los módulos anteriores.

---

## Objetivos del Módulo

### 1. Traducir estadística a significado clínico
Convertir un cambio numérico continuo en una métrica binaria de “éxito terapéutico”.

### 2. Identificar respondedores
Determinar qué proporción de la cohorte experimentó una mejoría clínicamente relevante según el umbral MCID.

### 3. Caracterizar predictores de mejoría
Evaluar qué características basales (motoras, demográficas o clínicas) están asociadas con alcanzar el MCID.

---

## Metodología y Flujo de Trabajo

### 1. Cálculo del Cambio Individual (Δ)
Para cada sujeto se cuantifica la diferencia entre la severidad final y la basal:

\[
\Delta_{\text{KPPS}} = \text{KPPS}_{\text{Final}} - \text{KPPS}_{\text{Basal}}
\]

Este valor refleja mejoría (Δ < 0), deterioro (Δ > 0) o estabilidad.

---

### 2. Definición del Umbral Clínico (Threshold)

El módulo utiliza un criterio estricto para definir **respuesta clínica positiva**:

- **MCID Achieved (Yes):**  
  \[
  \Delta \le -3
  \]
- **No Improvement:**  
  \[
  \Delta > -3
  \]

Este umbral refleja una reducción absoluta de ≥ 3 puntos en la escala total KPPS, criterio reportado como clínicamente significativo para estudios de dolor en Parkinson.

El resultado se codifica en una nueva variable categórica:

MCID_Response = Yes / No


---

### 3. Análisis de Factores Predictivos

Se comparan sistemáticamente los perfiles basales de **respondedores** vs **no respondedores**.

#### Variables numéricas (Edad, UPDRS, Levodopa, Duración de enfermedad)
Prueba utilizada:  
- **U de Mann–Whitney**  
  Adecuada para distribuciones no normales e independiente del tamaño muestral.

#### Variables categóricas (Sexo, Fenotipo, Depresión)
Prueba utilizada:  
- **Chi-Cuadrado de Pearson (χ²)**  
  Evalúa la dependencia entre categorías y la probabilidad de alcanzar el MCID.

---

## Resultados Clave

1. **Tasa de éxito clínico**  
   Proporción de pacientes que alcanzaron el MCID.

2. **Comparación de perfiles**  
   Boxplots y estadísticas que muestran diferencias en severidad motora y otros predictores entre respondedores y no respondedores.

3. **Identificación de predictores significativos**  
   Lista de variables con asociación estadísticamente significativa (p < 0.05).

4. **Archivo final procesado:**  

Remepark_kpps_with_groups.xlsx

(enriquecido con la variable MCID_Response).

---

## Resumen del Pipeline Completo Relacionado

1. **Data Cleaning:**  
Unificación y depuración de KPPS + UPDRS + variables demográficas.

2. **Longitudinal Analysis:**  
Evaluación del cambio numérico mediante Wilcoxon y análisis de estabilidad temporal.

3. **Severity Phenotyping:**  
Clasificación clínica en Leve, Moderado, Severo y Muy Severo; análisis de transiciones mediante Bowker.

4. **Clinical Relevance (MCID):**  
Evaluación binaria de la mejoría clínica y análisis de predictores.

---

Este módulo forma parte del sistema de análisis clínico del **Laboratorio Clínico de Enfermedades Neurodegenerativas (LCEN–INNN)** dentro del proyecto ReMePARK.

