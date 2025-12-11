# Armonización de Escalas Clínicas: NMSS → MDS-NMS

La transición de instrumentos clínicos en estudios longitudinales representa un desafío para la comparabilidad y continuidad de los datos. En el proyecto ReMePARK, los síntomas no motores fueron evaluados inicialmente mediante la **Non-Motor Symptoms Scale (NMSS)**; sin embargo, la adopción reciente de la **MDS-Non-Motor Rating Scale (MDS-NMS)** requiere un proceso de armonización que permita integrar ambas fuentes dentro de un mismo marco analítico.

Este módulo documenta y ejecuta la conversión operativa de dominios y puntajes NMSS hacia su estructura equivalente en MDS-NMS, utilizando técnicas de mapeo psicométrico y aproximaciones estadísticas robustas.

---

## Objetivo del Mapeo

Transformar los puntajes derivados de NMSS para que sean comparables a los dominios y subdominios de la MDS-NMS.  
Dado que ambas escalas difieren en número de ítems, estructura jerárquica y pesos implícitos, la conversión no puede realizarse mediante reglas lineales simples. Por ello se implementa un abordaje triangulado que combina técnicas de normalización, estandarización y vinculación equipercentil.

---

## Estrategia Metodológica

### 1. Normalización Porcentual (Linear Scaling)
- **Enfoque:** Los puntajes se transforman al porcentaje del puntaje máximo posible.  
- **Uso:** Permite comparar la saturación de síntomas independientemente del tamaño del dominio.  
- **Interpretación:** Equivale a estimar qué proporción del constructo no motor está afectado.

### 2. Estandarización Z-Score (Distributional Scaling)
- **Enfoque:** Convierte los puntajes en desviaciones estándar respecto a la media de la cohorte.  
- **Uso:** Neutraliza efectos de dificultad o rango entre escalas.  
- **Interpretación:** Ubica al paciente dentro de la distribución poblacional, permitiendo comparaciones relativas entre NMSS y MDS-NMS.

### 3. Vinculación Equipercentil (Equipercentile Linking)
- **Enfoque:** Método no paramétrico que mapea puntajes buscando igualar percentiles entre escalas.  
- **Uso:** Es el estándar psicométrico más sólido para traducción de puntuaciones entre instrumentos con distribuciones no lineales.  
- **Interpretación:** Un puntaje NMSS se vincula con el puntaje MDS-NMS equivalente en posición dentro de la cohorte.

---

## Tabla de Correspondencia entre Dominios

La siguiente tabla resume la lógica de alineación conceptual entre los nueve dominios NMSS y sus secciones equivalentes en la MDS-NMS. La correspondencia se basa en la similitud semántica y clínica de los constructos evaluados.

| Dominio NMSS | Contenido Evaluado | Dominio Correspondiente en MDS-NMS |
|--------------|--------------------|------------------------------------|
| **D1: Cardiovascular** | Síntomas autonómicos (p. ej., hipotensión ortostática) | **G. Hipotensión Ortostática** |
| **D2: Sueño / Fatiga** | Insomnio, trastorno de vigilia, fatiga física/mental | **K. Sueño y Vigilia**, **M. Otros (fatiga)** |
| **D3: Ánimo / Apatía** | Depresión, ansiedad, apatía | **A. Depresión**, **B. Ansiedad**, **C. Apatía** |
| **D4: Percepción** | Alucinaciones, delirios | **D. Psicosis** |
| **D5: Atención / Memoria** | Déficits de concentración y memoria | **F. Cognición** |
| **D6: Gastrointestinal** | Disfagia, estreñimiento, salivación | **J. Gastrointestinal** |
| **D7: Urinario** | Urgencia, frecuencia, nicturia | **H. Urinario** |
| **D8: Función Sexual** | Disfunción sexual masculina/femenina | **I. Sexual** |
| **D9: Miscelánea** | Dolor, anosmia, cambios de peso, sudoración | **L. Dolor**, **M. Otros (olfato, peso, sudoración)** |

---

## Contenido del Módulo

- Preprocesamiento y validación de dominios NMSS.  
- Conversión a rangos equivalentes MDS-NMS mediante los tres métodos descritos.  
- Generación de puntajes armonizados por dominio.  
- Análisis exploratorio para confirmar estabilidad de la conversión.  
- Exportación estandarizada para integración con el pipeline longitudinal ReMePARK.

---

## Consideraciones

- Este procedimiento no sustituye la aplicación directa de la MDS-NMS, sino que permite comparar retrospectivamente datos históricos evaluados con NMSS.  
- Las transformaciones deben reproducirse con las mismas distribuciones poblacionales o recalibrarse si cambia la cohorte.  
- Todas las operaciones se realizan únicamente sobre datos anonimizados conforme a las normas de manejo de información clínica.

---

## Mantenimiento

Este módulo es parte del conjunto de herramientas analíticas del **Laboratorio Clínico de Enfermedades Neurodegenerativas (LCEN–INNN)** para el proyecto ReMePARK.


