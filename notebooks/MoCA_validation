Control de calidad del MoCA — ReMePARK

Este directorio contiene el cuaderno QC_MoCA_ReMePARK_Colab.ipynb, diseñado para revisar la consistencia interna de los puntajes del Montreal Cognitive Assessment (MoCA) en bases de ReMePARK. Se ejecuta en Google Colab y no modifica el archivo de entrada.

Cómo ejecutarlo

Abre el cuaderno en Google Colab. Puedes descargar el .ipynb desde GitHub y subirlo a Colab.

Ejecuta las celdas en orden.

Cuando aparezca el selector, sube un archivo Excel con la estructura de Remepark_MoCA_2526.xlsx. Los datos deben estar en la hoja Hoja1.

Descarga QC_MoCA_ReMePARK.xlsx al finalizar y revisa las incidencias contra los formularios originales.

El cuaderno necesita las columnas MoCA que se muestran en su sección de configuración. Si faltan encabezados, se detiene e indica cuáles. Los máximos de los ítems y la composición de los subtotales están definidos en MAXIMOS y GRUPOS; revísalos antes de aplicar el cuaderno a otra versión del instrumento.

Comprobaciones

Componente

Control realizado

Ítems

Valores presentes, enteros y dentro del rango permitido.

Subtotales

Comparación de VISUO.TOT, DENOM.TOT, ATTN.TOT y LENG.TOT con la suma de sus ítems.

Total bruto

Recálculo de MoCA.TOTAL directamente desde los ítems, con máximo de 30 puntos.

Escolaridad

Verificación de PT.educ (0 o 1) y de MoCA.TOTALcorre = min(30, total recalculado + PT.educ).

Clasificaciones

Revisión de Dx.MoCA 26 y Dx.MoCA 24 según las categorías de la base de referencia.

MIS

Rango de 0 a 15 y compatibilidad con MoCA.rec.dif.

Las clasificaciones implementadas son: 0–17, «Deterioro moderado a grave»; desde 18 hasta antes del punto de corte, «Deterioro leve»; y desde 26 o 24, según la variable, «Normal». Se reproducen así las reglas observadas en la base de referencia; no equivalen por sí mismas a un diagnóstico clínico.

El Memory Index Score (MIS) no puede recalcularse exactamente porque la base no incluye los resultados por palabra de evocación con pistas y reconocimiento. Si r es el número de palabras recordadas libremente, el control comprueba que 3r ≤ MIS ≤ 10 + r.

Los registros sin ningún dato MoCA se identifican como «Sin evaluación MoCA». En registros parcialmente completados, los faltantes se reportan y no se sustituyen por cero. La base tampoco incluye años de escolaridad, por lo que el cuaderno no puede comprobar si correspondía asignar PT.educ = 1.

Archivos de salida

El cuaderno descarga QC_MoCA_ReMePARK.xlsx con tres hojas:

Hoja

Contenido

Resumen por fila

Resultados recalculados, clasificaciones esperadas, número de incidencias y estado del registro.

Incidencias

Un renglón por hallazgo, con la columna afectada y fila_excel para localizar el dato de origen.

Datos originales

Copia de Hoja1, sin cambios automáticos.

«Sin incidencias» significa que el registro pasó las comprobaciones implementadas; no confirma que las respuestas o la aplicación del instrumento sean correctas. Cualquier corrección debe cotejarse con la fuente primaria.

Dependencias y datos

Google Colab incluye Python, pandas, numpy y openpy
