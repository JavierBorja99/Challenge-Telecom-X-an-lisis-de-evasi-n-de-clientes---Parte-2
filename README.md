Telecom X - Predicción de Churn (Parte 2) 📊
1. Propósito del Análisis
El objetivo principal de este proyecto es desarrollar un modelo de machine learning capaz de predecir la probabilidad de que un cliente cancele su servicio (churn) con la empresa de telecomunicaciones Telecom X. Al identificar los factores más influyentes y los perfiles de clientes con mayor riesgo, la empresa puede diseñar estrategias de retención proactivas y personalizadas, optimizando recursos y minimizando la pérdida de ingresos.

2. Estructura del Proyecto
El repositorio está organizado de la siguiente manera para facilitar la navegación y reproducibilidad del análisis:

telecom-churn-prediction/
│
├── data/
│   └── telecom_data_tratado.csv    # Dataset limpio y preprocesado
│
├── notebooks/
│   └── 01_analisis_churn.ipynb     # Cuaderno principal con todo el análisis
│
├── visualizations/
│   └── churn_por_contrato.png      # Ejemplo de visualización guardada
│   └── importancia_variables.png   # Ejemplo de visualización guardada
│
└── README.md                       # Este archivo
/data: Contiene el dataset tratado y listo para ser cargado por el notebook.

/notebooks: Alberga el cuaderno de Jupyter (.ipynb) con todo el código del análisis, desde la carga de datos hasta la evaluación de modelos.

/visualizations: Carpeta opcional para guardar los gráficos más relevantes generados durante el análisis.

3. Proceso de Preparación de Datos
La preparación de los datos fue una etapa crucial para asegurar el rendimiento y la validez de los modelos.

Clasificación de Variables:

Numéricas: tenure, MonthlyCharges, TotalCharges.

Categóricas: gender, SeniorCitizen, Partner, Dependents, Contract, PaymentMethod, InternetService, entre otras.

Codificación y Normalización:

One-Hot Encoding: Se aplicó a todas las variables categóricas para convertirlas en un formato numérico que los modelos puedan procesar, evitando la creación de un orden jerárquico artificial.

Normalización (StandardScaler): Se escalaron las variables numéricas para modelos sensibles a la escala, como la Regresión Logística. Esto asegura que ninguna variable domine a otra solo por tener una magnitud mayor.

Separación de Datos:

El conjunto de datos se dividió en 80% para entrenamiento y 20% para prueba. Se utilizó una división estratificada por la variable objetivo (Churn) para mantener la proporción de clases en ambos conjuntos.

Justificación de Decisiones:

Se eligió la Regresión Logística por su alta interpretabilidad, permitiendo entender el impacto de cada variable en la probabilidad de churn.

Se seleccionó Random Forest como un modelo más complejo y robusto, que no requiere normalización de datos y es capaz de capturar relaciones no lineales.

Se aplicó la técnica SMOTE en el conjunto de entrenamiento para corregir el desbalance de clases, lo que ayuda a que el modelo no se incline a predecir únicamente la clase mayoritaria (no churn).

4. Análisis Exploratorio de Datos (EDA) - Insights
Durante el EDA, se generaron varias visualizaciones para entender la relación entre las variables y la cancelación.

Insight 1: El tipo de contrato es el factor más decisivo.

Los clientes con contratos mes a mes tienen una tasa de cancelación drásticamente mayor en comparación con aquellos con contratos anuales. Esto sugiere una falta de lealtad y un alto riesgo.

(Ejemplo de gráfico a incluir: churn_por_contrato.png)

Insight 2: Los clientes nuevos son los más propensos a cancelar.

La tasa de churn es muy alta durante los primeros meses de servicio y disminuye a medida que aumenta la antigüedad (tenure) del cliente. La retención debe enfocarse en las etapas tempranas del ciclo de vida del cliente.

(Ejemplo de gráfico a incluir: un histograma de tenure separado por Churn)

5. Instrucciones para Ejecutar el Cuaderno
Para replicar este análisis, sigue los siguientes pasos:

Clona o descarga este repositorio.

Asegúrate de tener Python 3 instalado. Luego, instala las bibliotecas necesarias ejecutando el siguiente comando en tu terminal:

Bash

pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn jupyter
Inicia Jupyter Notebook:

Bash

jupyter notebook
Abre el cuaderno ubicado en la carpeta notebooks/01_analisis_churn.ipynb.

Carga los datos tratados. El cuaderno está configurado para cargar el archivo telecom_data_tratado.csv desde la carpeta /data. Asegúrate de que la ruta sea correcta:

Python

# Ejemplo de código dentro del notebook para cargar los datos
import pandas as pd
df = pd.read_csv('../data/telecom_data_tratado.csv')
Ejecuta las celdas en orden para reproducir todo el análisis. 
