# Proyecto Agro-Clima: predicción de rendimiento agrícola en Argentina

## Problema de negocio

[Completar: 1-2 párrafos sobre por qué importa predecir el rendimiento
agrícola (kg/ha) por cultivo, departamento y año — quién lo usaría y para
qué decisión.]

## Datos

- **Fuente agrícola:** [completar: Ministerio de Agricultura / SIIA / otra]
- **Fuente climática:** NASA POWER
- **Cobertura:** 1981–2024, ~40 cultivos, 23 provincias, ~111.000 filas
- **Variables:** superficie sembrada/cosechada, producción, rendimiento,
  temperatura, precipitación, radiación, humedad

Los datos crudos no se versionan en este repositorio (ver `.gitignore`).
Para reproducir: [completar instrucciones de descarga/generación de
`df_recortado.csv`].

## Enfoque

1. **Dashboard exploratorio** (`01_dashboard_exploratorio.ipynb`): KPIs,
   evolución temporal, rankings por cultivo, distribución geográfica.
2. **Modelo supervisado** (`02_modelado_supervisado.ipynb`): regresión del
   rendimiento con Regresión Lineal, Ridge, Random Forest, Gradient
   Boosting y LightGBM; validación cruzada, optimización de
   hiperparámetros, interpretabilidad con SHAP.
3. **Modelo no supervisado** (`03_no_supervisado_zonas.ipynb`): PCA +
   clustering (K-Means) sobre variables climáticas para definir zonas
   agroclimáticas.
4. **Red neuronal** (`04_red_neuronal_mlp.ipynb`): MLP como extensión de
   aprendizaje profundo, comparado bajo las mismas reglas que el modelo
   supervisado.

## Resultados

| Modelo | R² test | MAE test (kg/ha) | Tiempo (s) |
|---|---|---|---|
| Regresión Lineal | 0.821 | 1.020 | 0.4 |
| Random Forest | 0.942 | 484 | 105 |
| **LightGBM (optimizado)** | **0.942** | **500** | **7** |
| MLP (red neuronal) | 0.916 | 687 | 128.5 |

[Completar: 1-2 párrafos de impacto / conclusión general.]

## Cómo ejecutar localmente

```bash
git clone https://github.com/SantiagoScozziero7/proyecto-agro-clima.git
cd proyecto-agro-clima

python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate

pip install -r requirements.txt
pre-commit install

jupyter notebook notebooks/
```
