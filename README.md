# ml-model-recommender

Automated ML model selection for tabular data. Analyzes datasets, compares preprocessing strategies, trains baselines, and provides actionable recommendations.

## features

- deep EDA with visualizations (missingness, distributions, correlations)
- problem type inference (classification vs regression)
- smart preprocessing (imputation, scaling, one-hot vs ordinal)
- high-cardinality detection and guidance
- class imbalance detection and handling suggestions
- model zoo baselines with cross-validation
- diagnostics (confusion matrix / regression plots, feature importance)
- exportable markdown + html reports

## quick start

1) create and activate the conda environment

```bash
conda env create -f environment.yml
conda activate ML_selection_ENV
```

2) launch the notebook

```bash
jupyter notebook ML_Model_Selector_Notebook.ipynb
```

3) configuration (first cell in the notebook)

```python
CSV_PATH = 'path/to/your/data.csv'  # excel/json/parquet also supported
TARGET_COLUMN = None  # let it auto-detect or set explicitly
PROBLEM_TYPE = None   # let it auto-infer or set 'classification'/'regression'
```

4) run cells top to bottom to generate analysis, model baselines, and reports

## how it works

1. **data loading** - reads csv, excel, json, or parquet files
2. **target detection** - auto-detects target column and infers classification vs regression
3. **data quality analysis** - checks for missing data, outliers, class imbalance, and potential leakage
4. **feature analysis** - classifies features as numeric, categorical, high-cardinality, text-like, or constant
5. **preprocessing comparison** - builds and compares one-hot vs ordinal encoding pipelines
6. **model zoo** - trains dummy baseline, logistic/linear regression, random forest, and histogram gradient boosting with cross-validation
7. **best model selection** - picks the best model/encoding combination with recommendations
8. **report generation** - exports markdown and html reports with all visualizations

## model zoo

**classification:** dummy classifier, logistic regression, random forest, histogram gradient boosting

**regression:** dummy regressor, linear regression, ridge regression, random forest, histogram gradient boosting

All models are evaluated with stratified k-fold cross-validation and appropriate metrics (ROC AUC for binary, F1 macro for multiclass, RMSE for regression).

## output files

```
figs/                              # all visualizations
  missing_data_analysis.png
  target_distribution.png
  correlation_matrix.png
  numeric_distributions.png
  model_comparison.png
  confusion_matrix.png             # classification
  regression_diagnostics.png       # regression
reports/
  Model_Selection_Report.md        # github-ready markdown
  Model_Selection_Report.html      # styled html report
best_model.pkl                     # serialized final pipeline
```

## repository layout

```
ML_Model_Selector_Notebook.ipynb   # main notebook
environment.yml                    # conda environment
requirements.txt                   # pip requirements (optional)
.gitignore                         # excludes data and generated outputs
```

## notes

- keep raw datasets out of version control (use the data/ folder or external paths)
- for excel files, set `CSV_PATH` to something like `path/to/file.xlsx`; the loader will use `read_excel`
- generated figures go to `figs/` and reports to `reports/` (both gitignored)
- set `MAX_SAMPLES_FOR_QUICK_RUN` to limit rows for faster iteration on large datasets
