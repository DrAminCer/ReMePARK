
# ReMePARK — Análisis MDS‑UPDRS

Cuaderno de Jupyter para análisis longitudinal de **MDS‑UPDRS I–IV** en la cohorte ReMePARK, con generación de métricas de cambio, trayectorias individuales y modelos estadísticos básicos.

## Contenido
- `ReMePARK_mdsupdrs.ipynb`: cuaderno principal.
- `data/`: carpeta para datos locales (excluida por defecto).
- `figures/`: salidas gráficas (excluidas por defecto).
- `requirements.txt`: dependencias.
- `.gitignore`: exclusiones estándar.
- `LICENSE`: plantilla de licencia (edítala según tus necesidades).

## Instalación
```bash
python -m venv .venv && source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Datos esperados
Coloca el archivo CSV en `data/`. Ver `data/README.md` para el esquema.
Recomendación: formato largo (una fila por sujeto‑visita).

## Uso rápido
1. Abre el cuaderno:
   ```bash
   jupyter notebook ReMePARK_mdsupdrs.ipynb
   ```
2. Ejecuta todas las celdas en orden.

## Salidas típicas
- Cálculo de `MDS_UPDRS_Total` si no existe.
- Gráficas de trayectorias por sujeto y promedios por grupo/estado.
- Cambios absolutos y relativos vs línea base.
- Modelos OLS o mixtos simples con `statsmodels` (opcional).

## Notas metodológicas
- Verifica la consistencia de subescalas (rangos válidos por parte).
- Si modelas longitudinalmente, considera efectos aleatorios por `SubjectID` y estructura de correlación (no incluida por defecto).

## Créditos y afiliación
Laboratorio Clínico de Enfermedades Neurodegenerativas (LCEN) — INNN.

## Licencia
Añade/ajusta `LICENSE` (p. ej., MIT).
