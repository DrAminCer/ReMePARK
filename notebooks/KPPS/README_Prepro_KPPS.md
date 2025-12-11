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

Esto permite construir un dataset completo para análisis multivariados.

---

## 3. Control de Calidad y Auditoría

### Estrategia Outer Join  
Se utiliza un enfoque **outer join** para maximizar la retención de datos durante la integración.  
Esto evita pérdidas innecesarias de información cuando alguna base no contiene cierto paciente o visita.

### Depuración Final  
Una vez completada la fusión, se eliminan los **registros fantasma** que no cuentan con información válida de dolor.

### Análisis de Missing Values  
Se realiza una cuantificación automática de valores faltantes en variables críticas como:

- UPDRS  
- PDQ-39  
- Sociodemografía  

Esto permite evaluar la integridad del dataset final previo al análisis estadístico.

---

## 4. Persistencia de Datos

El conjunto final es exportado como:
Remepark_cleaned_kpss.xlsx

un archivo limpio, documentado y listo para uso en SPSS, R, Python o Stata.

---

## Tecnologías Utilizadas

- **Python 3.x**  
- **Pandas** — Manipulación y fusión de DataFrames  
- **NumPy** — Manejo numérico y tratamiento de NaN  
- **Seaborn / Matplotlib** — Visualización exploratoria  
- **Google Colab / Drive API** — Acceso y gestión de almacenamiento en la nube  

---

## Estructura del Flujo de Datos (ETL)

El proceso sigue una lógica **ETL**:

### Extract  
- Conexión a Google Drive  
- Lectura de archivos `.xlsx` crudos  

### Transform  
- Selección dinámica de columnas con `filter(like='KPSS')`  
- Validación de integridad por paciente  
- Fusión de tablas (merge tipo left y outer)  
- Auditoría final de calidad  

### Load  
- Exportación del archivo maestro  
- Generación de métricas de calidad  

---

## Cómo Utilizar Este Módulo

1. Verifica acceso a la carpeta compartida de Google Drive donde se encuentran los archivos *Unified ReMePARK 2024*.  
2. Monta tu unidad de Drive al inicio del notebook.  
3. Ejecuta las celdas en orden para replicar el flujo completo de limpieza e integración.  
4. El archivo final será generado automáticamente como:
Remepark_cleaned_kpss.xlsx
y almacenado en la ruta especificada dentro del notebook.

---

Este módulo forma parte del pipeline analítico y de calidad de datos del **Laboratorio Clínico de Enfermedades Neurodegenerativas (LCEN–INNN)** para el proyecto ReMePARK.


