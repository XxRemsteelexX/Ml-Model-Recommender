# ml-model-recommender

Automated ML model selection for tabular data. Analyzes datasets, compares preprocessing strategies, trains baselines, and provides actionable recommendations.

## features
- deep eda with visualizations (missingness, distributions, correlations)
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
CSV_PATH = '/absolute/path/to/your/data.csv'  # excel/json/parquet also supported
TARGET_COLUMN = None  # let it auto-detect or set explicitly
PROBLEM_TYPE = None   # let it auto-infer or set 'classification'/'regression'
```

4) run cells top to bottom to generate analysis, model baselines, and reports

## repository layout
- ML_Model_Selector_Notebook.ipynb  # main notebook
- ML_Model_Chooser_README.md        # extended documentation
- environment.yml                   # conda environment
- requirements.txt                  # pip requirements (optional)
- .gitignore                        # excludes data and generated outputs

## notes
- keep raw datasets out of version control (use the data/ folder or external paths)
- for excel files, set `CSV_PATH` to something like `/path/file.xlsx`; the loader will use `read_excel`
- generated figures go to `figs/` and reports to `reports/` (both ignored by git)

## license
choose a license (e.g., mit) before publishing widely.

