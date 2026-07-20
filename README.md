# TP3_DIPLOMATURA_IA_UP
Análisis de Sentimientos en Twitter (TP3 - Diplomatura)

Este repositorio contiene el desarrollo del trabajo práctico enfocado en el procesamiento de lenguaje natural (PLN), análisis exploratorio y modelado predictivo de sentimientos utilizando un dataset masivo de tweets.

📋 Descripción del Proyecto

El objetivo principal es entrenar un modelo de clasificación de texto para determinar el sentimiento de los tweets (Negativo, Neutral, Positivo) implementando técnicas de limpieza, vectorización TF-IDF, lematización y modelos de Machine Learning (Regresión Logística), incorporando un enfoque de umbral de incertidumbre para la detección de la clase neutral en el conjunto de test.

🛠️ Tecnologías y Librerías Utilizadas

Python 3

Pandas / NumPy: Manipulación y análisis numérico de datos.

Scikit-Learn: Vectorización TF-IDF, métricas de evaluación y modelos predictivos (LogisticRegression).

NLTK: Tokenización, eliminación de stopwords y lematización (WordNetLemmatizer).

Seaborn / Matplotlib: Visualización estadística y generación de matrices de confusión.

Google Colab / Google Drive: Entorno de ejecución y almacenamiento de artefactos.

📊 Estructura y Flujo de Trabajo

Análisis Exploratorio y Limpieza (train_limpio.csv, test_limpio.csv):

Validación de nulos (cero valores nulos en ambos datasets).

Verificación del balanceo de clases en entrenamiento (800,000 registros negativos y 799,999 positivos).

Eliminación de columnas constantes o irrelevantes (id, user, query, date) para evitar ruido y sesgos en el aprendizaje.

Limpieza de texto: eliminación de URLs, menciones y caracteres especiales.

Procesamiento Avanzado (train_topicos.csv, test_topicos.csv):

Aplicación de lematización y filtrado de stopwords en inglés mediante NLTK para optimizar el vocabulario.

Modelado y Predicción con Umbral (predicciones_test_final.csv):

Vectorización mediante TfidfVectorizer ajustada estrictamente sobre el conjunto de entrenamiento (fit_transform en train, transform en test).

Entrenamiento de un modelo de Regresión Logística.

Implementación de una función de predicción con umbral de incertidumbre (threshold = 0.6): si la probabilidad máxima del modelo es menor al umbral, se fuerza la asignación de la clase Neutral (2), permitiendo capturar esta categoría ausente en el entrenamiento binario original.  


📈 Resultados y Evaluación

El modelo fue evaluado sobre el dataset de test final (498 muestras con tres clases: Negativo 0, Neutral 2, Positivo 4):  

Accuracy global: 63%  

Reporte de Clasificación:
Clase 0 (Negativo): Precision: 0.78 | Recall: 0.75 | F1-score: 0.76  

Clase 2 (Neutral): Precision: 0.51 | Recall: 0.30 | F1-score: 0.38  

Clase 4 (Positivo): Precision: 0.58 | Recall: 0.77 | F1-score: 0.66  

Conclusión técnica: Aunque el modelo fue entrenado con un dataset de dos clases, la estrategia de umbral de incertidumbre permitió predecir eficazmente los tweets neutros, evidenciando una ligera tendencia a clasificar dichos casos hacia la polaridad positiva.  


📂 Archivos Generados

train_limpio.csv / test_limpio.csv: Datasets depurados sin columnas de ruido.

train_topicos.csv / test_topicos.csv: Datasets con lematización y filtrado avanzado.

tfidf_vectorizer.joblib & lr_model.joblib: Artefactos serializados del vectorizador y modelo entrenado.

predicciones_test_final.csv: Archivo final con las predicciones y distribución de clases en el conjunto de prueba.
