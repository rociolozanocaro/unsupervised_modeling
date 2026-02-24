# Mushroom Classification & Unsupervised Learning

# 1. OBJECTIVE
The goal of this project is using an unsupervised model like PCA and clustering techniques in a Mushroom dataset and comparing the effect the dimensionality reduction has on a supervised model like RandomForest.

# 2. TECHNOLOGIES USED
    - Python
    - Jupyter Notebooks
    - VSCode

# 3. REPOSITORY STRUCTURE

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
# 4. HOW TO RUN

1. Clone the repository:
    ```
    git clone https://github.com/Bootcamp-Data-Analyst/p9-unsupervised-rocio
    ```
2. Install dependencies:
    ```
   pip install -r requirements.txt
   ```
3. Open the notebook:
   jupyter notebook

# 5. DATASET

The dataset was obtained from Kaggle (Mushroom Classification dataset).

It contains categorical variables describing physical characteristics of mushrooms and a target variable:

- The target is **class** → edible or poisonous

All features are categorical.