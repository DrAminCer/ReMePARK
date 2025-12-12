# Análisis de Severidad y Progresión del Dolor (KPPS)

Este módulo evalúa la carga de dolor y su evolución longitudinal en personas con Enfermedad de Parkinson, utilizando la **King’s Parkinson’s Disease Pain Scale (KPPS)** dentro del proyecto ReMePARK.  
El análisis se basa en la cohorte depurada y estandarizada proveniente del módulo de limpieza y fusión del KPPS.

---

## Objetivos del Módulo

### 1. Evaluar la progresión del dolor
Determinar si el dolor empeora, mejora o permanece estable entre la visita basal (Baseline) y la última visita disponible (Endpoint).

### 2. Fenotipado clínico de severidad
Clasificar a los pacientes en grupos de severidad (Leve, Moderado, Severo, Muy Severo) utilizando cuartiles poblacionales para obtener una categorización reproducible.

### 3. Identificar predictores de empeoramiento
Explorar qué factores motores, demográficos o farmacológicos se asocian con cambios en la severidad del dolor.

---

## Flujo de Trabajo (Pipeline)

El análisis se estructura en cuatro etapas principales.

---

### 1. Configuración Longitudinal

- **Cálculo de intervalos de seguimiento:**  
  Determinación de días transcurridos entre visitas consecutivas mediante `TimeDelta`.

- **Definición de cohortes longitudinales:**  
  Identificación automática de:
  - **Baseline:** primera visita con datos válidos.  
  - **Endpoint:** última visita disponible por sujeto.

Esto permite construir pares *pre–post* adecuados para análisis longitudinales.

---

### 2. Análisis de Cambio (Pre–Post)

El módulo evalúa la evolución del dolor desde dos perspectivas:

#### a) Perspectiva Numérica
- Cálculo del cambio absoluto:
  
\[
\Delta = \text{KPSS}_{\text{final}} - \text{KPSS}_{\text{inicial}}
\]

- Prueba de normalidad (Shapiro–Wilk).
- Prueba de hipótesis pareada no paramétrica:
  - **Wilcoxon Signed-Rank Test**  
    Determina si la variación del dolor total es estadísticamente significativa.

#### b) Perspectiva Categórica
- Generación de matrices de transición entre niveles de severidad (ej. Leve → Moderado).
- Aplicación del **Test de Simetría de Bowker**, generalización de McNemar para variables ordinales.
- Visualización mediante tablas de transición y heatmaps.

---

### 3. Análisis de Factores Asociados

Se evalúan posibles predictores de empeoramiento del dolor, incluyendo:

- Edad  
- Sexo  
- MDS-UPDRS III (motor)  
- Dosis de levodopa (LEDD)  
- Tiempo desde el diagnóstico  

#### Pruebas utilizadas:
- **Chi-Cuadrado (χ²):** para predictores categóricos.  
- **Kruskal–Wallis:** para predictores numéricos no paramétricos.  

#### Visualizaciones:
- Boxplots comparativos.  
- Gráficos de barras agrupadas.  

---

### 4. Clasificación de Severidad (Fenotipado)

Se genera una nueva variable:

KPSS_Severity_Group


basada en cuartiles poblacionales:

| Grupo | Definición |
|-------|------------|
| Mild | Q1 |
| Moderate | Q2 |
| Severe | Q3 |
| Very Severe | Q4 |

Este fenotipado permite:

- análisis estratificado,  
- comparación entre visitas,  
- integración con otros módulos clínicos.

---

## Resultados Principales

El módulo produce:

1. Tablas descriptivas de severidad basal y final.  
2. P-values y estadísticos para Wilcoxon y Bowker.  
3. Boxplots relacionando dolor con severidad motora o demográfica.  
4. Matrices de transición entre categorías.  
5. Archivo final procesado:

Remepark_kpps_with_groups.xlsx


---

Este módulo forma parte del sistema de análisis longitudinal del proyecto **ReMePARK**, desarrollado por el **Laboratorio Clínico de Enfermedades Neurodegenerativas (LCEN–INNN)**.


