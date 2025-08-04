Proyecto de Predicción de Churn de Clientes
1. Propósito del Análisis
El objetivo principal de este proyecto es predecir la cancelación (churn) de clientes de la compañía TelecomX utilizando variables relevantes extraídas de datos de uso y facturación. Con ello se busca identificar patrones de comportamiento, anticipar altas tasas de abandono y proponer estrategias de retención.
2. Estructura del Proyecto
Datos originales sin procesar (TelecomX.csv)
Entrenamiento, evaluación e importancia de variables
# Lista de bibliotecas necesarias
3. Preparación de los Datos
1.	Clasificación de Variables
o	Numéricas: tenure, MonthlyCharges, TotalCharges, SeniorCitizen, Cuentas_Diarias
o	Categóricas: gender, Partner, Dependents, PhoneService, MultipleLines, InternetService, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies, Contract, PaperlessBilling, PaymentMethod
2.	Eliminación de Columnas Irrelevantes
o	Se eliminó customerID para evitar ruido en la predicción.
3.	Codificación de Variables
o	Mapear churn a binario: {'No':0, 'Yes':1}.
o	One-hot encoding para todas las variables categóricas con pd.get_dummies.
4.	Normalización/Estandarización
o	Para modelos sensibles a escala (Regresión Logística, KNN, SVM): StandardScaler aplicado sobre variables numéricas.
o	Para modelos basados en árbol (Random Forest): se utilizan los datos sin escalar.
5.	Separación en Conjuntos
o	División train/test con train_test_split (70% entrenamiento / 30% prueba), stratify=y para preservar la proporción de churn.
4. Justificaciones de Modelización
•	Regresión Logística y KNN: requieren escalado para evitar dominancia de variables de mayor rango y facilitar convergencia.
•	Random Forest: no sensible a escala; robusto a outliers y captura relaciones no lineales sin preprocesamiento complejo.
•	Análisis de overfitting/underfitting: comparación de métricas train vs test, ajuste de hiperparámetros (max_depth, n_estimators, regularización).
5. Ejemplos de EDA e Insights
•	Boxplot Tenure vs Churn: muestra que clientes con tenure < 6 meses tienen churn 3× mayor.
•	Scatter TotalCharges vs Tenure: revela patrón en U; gasto muy bajo o muy alto se asocia a mayor abandono.
•	Matriz de Correlación: identifica que Contract=Month-to-month y ausencia de TechSupport son altamente correlados con churn.
6. Instrucciones de Ejecución
1.	Clonar repositorio:
2.	Instalar dependencias:
pip install -r requirements.txt
3.	Cargar datos tratados:
o	Copia TelecomX.csv
4.	Ejecutar notebooks:
o	challengeII.ipynb
