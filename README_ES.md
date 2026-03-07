# Clasificación de Setas & Aprendizaje No Supervisado

[English](README.md) | [Español](README_ES.md)

# 1. OBJETIVO
El objetivo de este proyecto es aplicar un modelo no supervisado mediante PCA y técnicas de clustering a un dataset de setas, y comparar el efecto que tiene la reducción de dimensionalidad sobre un modelo supervisado como RandomForest.

# 2. TECNOLOGÍAS UTILIZADAS
    - Análisis de datos: Pandas, Numpy, Missingno.
    - Visualización: Matplotlib, Seaborn, Plotly.
    - Machine Learning: Scikit-learn (PCA, RandomForestClassifier, KMeans).
    - Jupyter Notebooks.
    - VSCode.
    - Git.

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Jupyter](https://img.shields.io/badge/Jupyter-%23F37626.svg?style=for-the-badge&logo=jupyter&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-%233F4F75.svg?style=for-the-badge&logo=plotly&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

# 3. ESTRUCTURA DEL REPOSITORIO

``` text
──  notebooks/
│   └── p9_unsupervised_rocio.ipynb
├── data/
│   └── data_processed
        └── mushrooms_clean.csv
        └── mushrooms_clean.parquet
    └── data_raw
        └── mushrooms.csv
└── README.md
└── requirements.txt
```

# 4. CÓMO EJECUTAR EL PROYECTO

1. Clonar el repositorio
```text 
git clone https://github.com/rociolozanocaro/Unsupervised_Modeling
```

2. Crear y activar el entorno virtual
```text 
python -m venv .venv
```

```text 
# Windows
.venv/Scripts/activate

# Mac/Linux
source .venv/bin/activate
```

3. Instalar dependencias
```text 
pip install -r requirements.txt
```

# 5. DATASET

El dataset fue obtenido de Kaggle: [Mushroom Dataset](https://www.kaggle.com/uciml/mushroom-classification).

Contiene únicamente variables categóricas que describen características físicas de setas y una variable objetivo: 'class', que indica si la seta es 'edible' (comestible) o 'poisonous' (venenosa).

# 6. LIMPIEZA DE DATOS

Los pasos de preprocesamiento incluyeron:

- Conversión de todas las columnas a tipo categórico.
- Comprobación de valores nulos.
- Tratamiento de la categoría '?' en 'stalk-root' mediante imputación KNN.
- Eliminación de la columna 'veil-type' (solo tenía una categoría).
- Comprobación de filas duplicadas. No se encontró ninguna.

# 7. ANÁLISIS EXPLORATORIO DE DATOS

## 7.1. Análisis Univariante
Se usaron gráficos de barras para analizar la distribución de cada variable categórica.

![Barplot image](images/barplot_class_univariable.png)

La variable objetivo tiene una distribución equilibrada.

## 7.2. Análisis Bivariante
Se analizó la relación entre la variable objetivo (class) y cada característica.

![Stackedbar image](images/stackedbar_class_odor_bivariable.png)

Algunas categorías separan perfectamente las setas comestibles de las venenosas.

![Crosstab](images/crosstab_class_odor_bivariable.png)

La variable 'odor' (olor) es especialmente útil para predecir si una seta es comestible o venenosa. Solo la categoría 'n' (ninguno) presenta cierta mezcla entre ambas clases.

## 7.3. Análisis Multivariante
Se utilizó la V de Cramér para medir las asociaciones entre variables categóricas.

![Cramer Matrix](images/cramermatrix_multivariable.png)

Se confirma lo observado anteriormente: 'odor' y 'class' están muy correlacionadas.

# 8. MODELOS
## 8.1. PCA (Reducción de Dimensionalidad)

Se aplicó Análisis de Componentes Principales para reducir la dimensionalidad.

- Se usaron 2 y 3 componentes para visualización (2D, 3D) por clase y por clusters.

![PCA 2D class](images/PCA_2D_class.png)

![PCA 2D clusters](images/PCA_2D_clusters.png)

![PCA 3D clusters](images/PCA_3D_clusters.png)

- Entre 8 y 12 componentes preservan la mayor parte del poder predictivo, explicando más del 64% de la varianza acumulada.

![Accuracy vs number of PCA](images/accuracy_components.png)

## 8.2. Random Forest Classifier

Se entrenó un clasificador Random Forest para predecir la clase de la seta con y sin reducción de dimensionalidad.

| Modelo | Características/Componentes | Varianza explicada | Accuracy |
| :--- | :--- | :--- | :--- |
| Codificado | 115 características | 100% | 1.0 |
| PCA | 10 componentes | 64% | 0.9993 |

La reducción de dimensionalidad no redujo significativamente el rendimiento del modelo.

## 8.3. K-Means Clustering

Se utilizó el método del codo para determinar el número óptimo de clusters sobre los componentes de PCA.

![Elbow Method](images/elbow_method.png)

Los resultados indican que entre 4 y 6 clusters es una elección adecuada.

Se generaron visualizaciones de los clusters que mostraron una separación parcial entre setas comestibles y venenosas. Solo un cluster presenta mezcla entre ambas clases.

![clusters](images/clusters_class.png)

# 9. CONCLUSIONES

- El dataset es altamente separable.
- Random Forest alcanzó una precisión perfecta.
- PCA redujo la dimensionalidad manteniendo el rendimiento.
- Algunas características categóricas determinan fuertemente la toxicidad de las setas.
- El clustering no supervisado refleja parcialmente la separación entre clases.

# 10. AUTORA
| Nombre | Contacto |
| :--- | :--- |
| **Rocío Lozano Caro** | [![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/rociolozanocaro/) [![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/rociolozanocaro) |
