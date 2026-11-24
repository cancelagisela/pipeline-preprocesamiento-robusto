# Construcción de un Pipeline de Preprocesamiento Robusto

Implementación de un pipeline reproducible de preprocesamiento y modelado de regresión con Scikit-Learn sobre datos de compras de clientes (`shopping_trends_updated.csv`).

## Descripción del dataset

- **Archivo:** `shopping_trends_updated.csv` (3.900 registros y 18 columnas con información demográfica, de compra y preferencias de clientes).
- **Variable objetivo (`target`):** `Purchase Amount (USD)` (regresión para estimar el monto de compra).
- **Variables predictoras utilizadas:**
  - **Numéricas:** `Age`, `Previous Purchases`
  - **Categóricas:** `Category`, `Size`, `Season`

## Estructura del pipeline

1. **División Train / Test:** Separación de datos (`train_test_split`) antes de ajustar cualquier transformador para evitar *data leakage*.
2. **Preprocesamiento por tipo de variable (`ColumnTransformer`):**
   - **Numéricas:** `SimpleImputer(strategy="median")` + `StandardScaler()`.
   - **Categóricas:** `SimpleImputer(strategy="most_frequent")` + `OneHotEncoder(handle_unknown="ignore")`.
3. **Modelo y persistencia:** Ensamblaje con `LinearRegression`, evaluación de métricas (`MAE` y `R²`), prueba de `.predict()` sobre datos nuevos y exportación del pipeline entrenado con `joblib`.

## Dependencias
- `pandas`
- `scikit-learn`
- `joblib`

## Ejecución y verificación de la rúbrica
1. Abrir `Construcción_de_un_Pipeline_de_Preprocesamiento_Robusto.ipynb` en Google Colab o Jupyter.
2. Verificar que `shopping_trends_updated.csv` esté en el directorio de trabajo (o subirlo al entorno de Colab).
3. Ejecutar todas las celdas en orden:
   - División **Train / Test** (`train_test_split`) antes del ajuste de transformadores.
   - Preprocesamiento con `ColumnTransformer` y `Pipeline` (imputación y escalado en numéricas; imputación y codificación en categóricas).
   - Entrenamiento del modelo de regresión, cálculo de métricas y prueba del método `.predict()` sobre datos nuevos.
   - Exportación del pipeline entrenado mediante `joblib`.

## Resultados obtenidos
Se construyó un pipeline reproducible de Machine Learning utilizando Scikit-Learn.
El flujo implementado incluye:

-   División de datos en entrenamiento y prueba.
-   Imputación de valores faltantes.
-   Escalado de variables numéricas.
-   Codificación One-Hot de variables categóricas.
-   Entrenamiento de un modelo de regresión.
-   Evaluación mediante métricas de rendimiento.
-   Toda la ejecución y los resultados pueden verificarse en el notebook incluido en este repositorio

## Métricas obtenidas
MAE: 20.72

R²: -0.0057

Además, se validó el pipeline realizando predicciones sobre nuevos datos.

Ejemplo:

[61.49, 57.55]
