# Análisis Longitudinal y Severidad del Dolor (KPPS)

Este módulo realiza el análisis clínico-estadístico de la progresión del dolor en personas con Enfermedad de Parkinson utilizando la **King’s Parkinson’s Disease Pain Scale (KPPS)**.  
A diferencia del módulo de limpieza y unificación de datos, este cuaderno se enfoca en la **evolución temporal del dolor** y en la **evaluación de cambios clínicamente relevantes** dentro de la cohorte ReMePARK.

El análisis se basa en el dataset maestro limpio:
Remepark_cleaned_kpss.xlsx

obtenido del módulo de procesamiento previo.

---

## 1. Descripción General del Módulo

Este flujo de trabajo evalúa dos dimensiones fundamentales:

### Análisis temporal
Validación detallada de los intervalos de seguimiento (días entre visitas) para garantizar la consistencia del diseño longitudinal.

### Progresión clínica
Medición del cambio de severidad del dolor entre la visita basal (Baseline) y la última visita registrada (Endpoint), utilizando pruebas estadísticas apropiadas para datos pareados y no normales.

---

## 2. Pipeline Analítico

El notebook implementa los siguientes pasos secuenciales:

### 2.1 Carga y Filtrado de Cohorte
- Importación del archivo **Remepark_cleaned_kpss.xlsx**.  
- Identificación de la cohorte con seguimiento longitudinal:  
  selección de pacientes con más de una visita (`accum.visits > 1`).

### 2.2 Auditoría Temporal (Time-Delta)
- Conversión estandarizada de fechas a formato `datetime`.  
- Cálculo del tiempo transcurrido entre visitas consecutivas (`groupby → diff`).  
- Obtención de estadísticas descriptivas para los intervalos de seguimiento:  
  media, mínimo y máximo en días.

### 2.3 Análisis Pre–Post (Baseline vs Endpoint)
- Detección automática de la **primera** y **última** visita de cada sujeto.  
- Cálculo del cambio absoluto en puntaje total:

\[
\Delta \text{KPSS} = \text{KPSS}_{\text{endpoint}} - \text{KPSS}_{\text{baseline}}
\]

- Evaluación de la distribución del cambio mediante **Shapiro–Wilk**.  
- Ejecución de la prueba no paramétrica **Wilcoxon Signed-Rank**, adecuada para datos pareados sin normalidad.

### 2.4 Caracterización transversal y demográfica
- Comparación descriptiva entre Visita 1 y Visita 2.  
- Construcción de la **Tabla 1** demográfica:  
  edad y sexo al inicio del seguimiento para la cohorte longitudinal.

---

## 3. Objetivos del Notebook

- Determinar la periodicidad real de las evaluaciones clínicas en la cohorte de dolor.  
- Estimar si existe un cambio estadística y clínicamente significativo en la severidad del dolor (KPSS total) entre Baseline y Endpoint.

---

## 4. Metodología Estadística

- **Manejo de fechas:**  
  Cálculo de `TimeDelta` a nivel individual mediante `groupby` y `diff`.

- **Normalidad:**  
  Verificación mediante **Shapiro–Wilk**, adecuada para muestras pequeñas o moderadas.

- **Prueba de hipótesis:**  
  **Wilcoxon Signed-Rank Test**, ideal para cambios longitudinales en escalas clínicas.

---

## 5. Outputs del Módulo

1. Estadísticas descriptivas del intervalo real entre visitas.  
2. Distribución y magnitud del cambio longitudinal de KPSS.  
3. Resultados de Wilcoxon:  
   - Estadístico W  
   - P-value  
4. Tablas transversales de severidad por visita.  
5. Tabla demográfica inicial (Edad, Sexo).

---

## 6. Uso del Código

1. Montar Google Drive o configurar la ruta local donde se encuentra `Remepark_cleaned_kpss.xlsx`.  
2. Ejecutar el notebook de forma secuencial.  
3. Verificar que las fechas estén correctamente formateadas antes del análisis.  
4. Interpretar los valores del test de Wilcoxon para determinar la significancia del cambio.

---

Este módulo forma parte del sistema analítico de seguimiento longitudinal del **Laboratorio Clínico de Enfermedades Neurodegenerativas (LCEN–INNN)** dentro del proyecto ReMePARK.



