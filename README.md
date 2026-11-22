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

## Ejecución

1. Abrir `Construcción_de_un_Pipeline_de_Preprocesamiento_Robusto.ipynb` en Google Colab o Jupyter.
2. Asegurar que `shopping_trends_updated.csv` esté disponible en el entorno de ejecución.
3. Ejecutar las celdas en orden para entrenar el modelo, evaluar métricas, probar predicciones y generar el archivo exportado con `joblib`.
