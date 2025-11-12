
# Datos

Este repositorio **no** incluye datos sensibles. Coloca aquí tu archivo, por ejemplo `rempark_mdsupdrs_long.csv`.
No subas datos con identificadores personales.

## Esquema esperado (columnas mínimas)
- `SubjectID` (string/int): identificador del paciente.
- `Visit` o `Time` (string/num): etiqueta o tiempo en días/meses desde línea base.
- `VisitDate` (opcional, ISO-8601): fecha de visita.
- `MDS_UPDRS_I`, `MDS_UPDRS_II`, `MDS_UPDRS_III`, `MDS_UPDRS_IV` (numéricos).
- `MDS_UPDRS_Total` (numérico, opcional si se calcula en el cuaderno).
- `State` (opcional): ON/OFF meds.
- `LEDD` (opcional): dosis equivalente de levodopa.
- `Group` (opcional): etiqueta de cohorte (p.ej., intervención/control).

### Reglas
- Si hay varias mediciones por día, define una estrategia (promedio, última, etc.).
- Las subescalas deben ser numéricas y no negativas.
