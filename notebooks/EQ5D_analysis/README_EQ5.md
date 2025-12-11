# EQ-5D Health Utility Analysis – ReMePARK
Este cuaderno implementa el procesamiento completo del instrumento **EQ-5D-5L**, la conversión (*crosswalk*) a EQ-5D-3L y el cálculo del **índice de utilidad** para participantes del proyecto **ReMePARK**.  
Incluye análisis descriptivo, validación de estructura, y modelado longitudinal de calidad de vida.

---

## 📌 Objetivos del cuaderno

- Validar la integridad y el rango de los cinco dominios del EQ-5D-5L.
- Aplicar el algoritmo **Crosswalk 5L** de EuroQol (Mexican Value Set, 2021).
- Calcular el **Utility Index** por participante.
- Describir la distribución de calidad de vida en la cohorte.
- Analizar cambios longitudinales (pendiente anual).
- Explorar la relación entre EQ-5D y escalas clínicas (UPDRS, NMS).

---

## 📁 Estructura del cuaderno

1. **Importación de librerías y configuración inicial**  
2. **Carga y validación de datos EQ-5D**  
   - Rango permitido (1–5)  
   - Verificación de celdas no numéricas  
   - Distribución por dominio  
3. **Implementación del algoritmo Crosswalk**  
   - Conversión 5L → 3L  
   - Asignación de valores poblacionales  
   - Generación del índice de utilidad  
4. **Análisis descriptivo**  
   - Histogramas, densidades, boxplots  
   - Correlaciones entre dominios  
5. **Análisis longitudinal**  
   - Cálculo de deltas  
   - Pendiente anual por individuo  
   - Modelos mixtos  
6. **Integración con MDS-UPDRS y NMS**  
   - Correlaciones  
   - Modelos lineales (si aplica)  
7. **Exportación de resultados**

---

## 📦 Dependencias

Para ejecutar el cuaderno, asegurarse de tener instalados:

```bash
pip install pandas numpy matplotlib seaborn statsmodels lifelines openpyxl

