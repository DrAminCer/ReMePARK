# Procesamiento y Gestión de la Escala de Dolor KPPS (King’s Parkinson’s Disease Pain Scale)

Este módulo implementa el flujo completo de limpieza, integración y estandarización de la **King’s Parkinson’s Disease Pain Scale (KPPS)** dentro del proyecto ReMePARK. El objetivo es generar un dataset armonizado y reproducible, apto para análisis clínicos y longitudinales.

---

## 1. Gestión de la Escala de Dolor (KPPS)

### Carga de Datos  
Importación directa de la KPPS desde el repositorio en la nube (Google Drive).  
Los archivos crudos son leídos en formato `.xlsx` mediante Pandas.

### Limpieza Estricta  
Se aplica una estrategia de **listwise deletion**, eliminando únicamente a los pacientes con datos incompletos en los ítems de dolor.  
El énfasis es garantizar la validez de los puntajes calculados.

### Identificación de Cohorte  
- Conteo de **sujetos únicos** para estimar el tamaño real de la población.  
- Identificación de la **subpoblación longitudinal**, definida como pacientes con ≥ 2 visitas válidas.

---

## 2. Integración Multidimensional (Data Merging)

Los puntajes KPPS se integran con tres fuentes adicionales mediante claves primarias combinadas:

- **Sociodemográficos**: edad, género, duración de la enfermedad.  
- **MDS-UPDRS**: evaluación motora y no motora unificada.  
- **PDQ-39**: calidad de vida.

La unión se realiza empleando combinaciones de `merge` con claves:


