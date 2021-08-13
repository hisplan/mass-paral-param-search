# Tracking Experiments using Jupyter Notebook

## Set Up

```bash
pip install -r requirements.txt
```

```bash
cd single-cell/inputs
gunzip 2_DT_2_CD45plus_dense.h5ad.gz
```

## Intro

Q> How do I run a notebook from the terminal?

Original: [sum.ipynb](intro/sum.ipynb)

Convert to template: [sum.template.ipynb](intro/sum.template.ipynb)

- Add headings.
- Add a comment: `THESE VALUES SHOULD BE OVERRIDDEN`
- Add a tag: `parameters'

Change `x` and `y`, run the notebook from the terminal.

```bash
papermill sum.template.ipynb sum.results.ipynb \
    -p x 2 \
    -p y 5
```

## Diabetes

Q> Find a classifier that gives me the highest accuracy.

Original: [classifier.ipynb](diabetes/classifier.ipynb)

- Initially uses the DecisionTree classifier.

Convert to template: [classifier.template.ipynb](diabetes/classifier.template.ipynb)

- Import a bunch of scikit-learn classifiers.
- Tag the accuracy cell with `accuracy`.
- Tag the ROC curve with `roc`.

Runner

- Add different classifiers to `experiments`.
- Run Papermill's `execute_notebook` function from Python.
- Use `sklearn_evaluation` to load up all the generated notebooks
- Compare those tagged cells (e.g. `accuracy`, `roc`)

## Single-Cell

Q> How to run several combinations of HVGs, PCs, hyperparameters, etc. in parallel?

Original: [analysis.ipynb](single-cell/analysis.ipynb)

Convert to template: [analysis.template.ipynb](single-cell/analysis.template.ipynb)

- Parameterize
    - `experiment_id = 0`
    - `hvg_n_top_genes = 5000`
    - `pca_n_comps = 50`
    - `n_neighbors = 30`
- Remove hardcoded numbers
- If you already have an algorithm that figures an optimal parameter, use it (e.g. `KOptimzer`)

Run

- Run one at a time: [run-serial.ipynb](single-cell/run-serial.ipynb)
- Run in parallel using Ray: [run-parallel-grid.ipynb](single-cell/run-parallel-grid.ipynb)

Benefits

- The resulting notebook is end-user friendly
    - No giant for-loop
    - No tracking code
    - No parallelism code
- Took 3-5 min. to run on a MacBook pro
- Each experiment generates a notebook and h5ad file.

## References

- Papermill
- `sklearn_evaluation`: https://sklearn-evaluation.readthedocs.io/en/stable/user_guide/NotebookCollection.html
- Ray
