# Smart ML Model Chooser

Comprehensive machine learning model selection and baseline evaluation for tabular data with professional reporting.

## What This Does

**Automated Analysis:**
- loads your dataset (csv/excel/json/parquet)
- performs deep exploratory data analysis with visualizations
- detects data quality issues (missing values, outliers, class imbalance, potential leakage)
- infers problem type (classification vs regression)
- analyzes feature types (numeric, categorical, high-cardinality, text-like, datetime)

**Smart Preprocessing:**
- builds optimized preprocessing pipelines
- compares one-hot vs ordinal encoding strategies
- handles class imbalance with appropriate techniques
- provides intelligent scaling and imputation

**Model Training & Evaluation:**
- trains multiple baseline models with cross-validation
- evaluates performance with appropriate metrics
- generates comprehensive model diagnostics
- selects best performing model with statistical confidence

**Professional Reporting:**
- creates detailed markdown and html reports
- saves all visualizations as high-quality figures
- provides actionable recommendations for improvement
- exports publication-ready analysis

## Quick Start

### 1. Setup Environment
```bash
conda env create -f environment.yml
conda activate ML_selection_ENV
```

### 2. Configure Analysis
```python
# in the configuration cell
CSV_PATH = 'path/to/your/data.csv'
TARGET_COLUMN = None  # auto-detects if None
PROBLEM_TYPE = None   # auto-infers if None
```

### 3. Run Analysis
Execute all cells in order. The notebook will:
- automatically detect your target column and problem type
- perform comprehensive data quality analysis
- generate visualizations and model comparisons
- export professional reports

## Output Files

```
├── figs/                           # all visualizations
│   ├── missing_data_analysis.png
│   ├── target_distribution.png
│   ├── correlation_matrix.png
│   ├── model_comparison.png
│   └── confusion_matrix.png (or regression_diagnostics.png)
├── reports/
│   ├── Model_Selection_Report.md   # github-ready markdown
│   └── Model_Selection_Report.html # styled html report
└── best_model.pkl                  # serialized final pipeline
```

## Features

### Data Quality Analysis
- missing data patterns and recommendations
- outlier detection using IQR method
- class imbalance detection with mitigation strategies
- potential data leakage warnings
- feature type classification (numeric, categorical, text-like, etc.)

### Intelligent Preprocessing
- conditional scaling (only when beneficial)
- smart categorical encoding (one-hot vs ordinal)
- high-cardinality categorical handling
- missing value imputation strategies
- feature type-specific transformations

### Model Zoo
**Classification:**
- dummy classifier (baseline)
- logistic regression with class balancing
- random forest with balanced sampling
- histogram gradient boosting

**Regression:**
- dummy regressor (baseline)
- linear regression
- ridge regression
- random forest regressor
- histogram gradient boosting regressor

### Advanced Analysis
- cross-validation with appropriate strategies
- learning curves and validation analysis
- feature importance visualization
- model diagnostic plots
- statistical significance testing

## Extending the Analysis

### Add More Models
```python
# in the model zoo section, add:
from xgboost import XGBClassifier
from catboost import CatBoostClassifier

models['xgboost'] = XGBClassifier(random_state=RANDOM_STATE)
models['catboost'] = CatBoostClassifier(random_state=RANDOM_STATE, verbose=False)
```

### Hyperparameter Tuning
```python
# add optuna optimization
import optuna
from sklearn.model_selection import RandomizedSearchCV

# example hyperparameter tuning cell included in notebook
```

### Text Data Processing
```python
# for text columns detected
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.pipeline import make_union

# text processing pipeline example included
```

## Dependencies

**Core Requirements:**
- python >= 3.11
- pandas >= 2.0
- scikit-learn >= 1.3
- matplotlib >= 3.7
- numpy >= 1.24

**Optional Enhancements:**
- xgboost, lightgbm, catboost (advanced models)
- optuna (hyperparameter tuning)
- shap (model interpretability)
- plotly (interactive visualizations)

See `requirements.txt` and `environment.yml` for complete dependency lists.

## Best Practices

1. **Start with clean data**: remove obviously incorrect records before analysis
2. **Validate target column**: ensure the auto-detected target makes business sense
3. **Review feature types**: check that high-cardinality categoricals are handled appropriately
4. **Examine class imbalance**: consider domain-specific implications of rebalancing
5. **Interpret model diagnostics**: look beyond just accuracy/rmse scores
6. **Follow recommendations**: the notebook provides specific next steps for improvement

## Troubleshooting

**Memory Issues:**
- set `MAX_SAMPLES_FOR_QUICK_RUN = 10000` for initial exploration
- consider feature selection for very wide datasets

**Performance:**
- reduce `N_SPLITS` for faster cross-validation
- use fewer models in the model zoo for speed

**Categorical Encoding:**
- for high-cardinality features, consider catboost or target encoding
- ordinal encoding often works better with tree models

## Contributing

Contributions welcome! Areas for enhancement:
- time series analysis capabilities
- automated feature engineering
- more sophisticated model selection strategies
- integration with mlflow/weights&biases
- automated model deployment options
