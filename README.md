### Project Title
Diabetes Risk Classification with KNN

**Author**
Gajendra Babu Thokala

#### Executive summary
Predict diabetes risk using the CDC BRFSS survey indicators and KNN classifiers (with and without PCA). The notebook runs EDA and benchmarks baseline models using ROC-AUC, accuracy, recall, precision, and F1.

#### Rationale
Diabetes is often underdiagnosed; early prediction enables preventative care and lower costs. Large-scale self-reported indicators from BRFSS offer broad coverage and interpretability.

#### Research Question
Can we classify whether an individual has diabetes using k-nearest neighbors on lifestyle/demographic survey features (BRFSS), and how does PCA affect performance?

#### Data Sources
- CDC BRFSS 2015: https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset/data
- Target column: `Diabetes_binary`; CSVs under `data/brfss/` are referenced in the notebook.

#### Methodology
- Follow CRISP-DM: understand data (shapes, missingness, class balance), prepare by standardizing column names, dropping duplicates, and handling nulls.
- Preprocess with `ColumnTransformer`: median impute + scale numeric fields; mode impute + one-hot encode categoricals.
- EDA: class imbalance plots and correlation heatmap across numeric features.
- Modeling: stratified train/test split; KNN pipeline with grid search over `k`; evaluation via accuracy, precision, recall, F1, ROC-AUC plus confusion matrix and ROC curve.
- Dimensionality reduction: optional PCA (95% variance) before KNN; compare against non-PCA baseline.

#### Results
- Ran BRFSS baseline. Best KNN (`k=15`, distance weights): ROC-AUC ~0.77, accuracy ~0.857, precision ~0.458, recall ~0.161, F1 ~0.238. KNN+PCA (95% variance) performed similarly (ROC-AUC ~0.77).
- Notebook produces ROC curves, confusion matrices, and comparison tables.

#### Next steps
- Broaden hyperparameter search (distance metrics, weighting), calibrate probabilities, and add permutation importance for interpretability.
- Mitigate class imbalance on the BRFSS binary dataset (weights or resampling).
- Add models: Decision Trees, Random Forests, KNN Regressor; benchmark against baseline KNN.
- Optional: package an inference API (FastAPI) and a lightweight Streamlit UI for interactive exploration.

#### Outline of project

- [EDA + baseline KNN notebook](notebooks/eda_knn_baseline.ipynb)

##### Contact and Further Information
Questions or feedback: Email to gajendra2k2@gmail.com
