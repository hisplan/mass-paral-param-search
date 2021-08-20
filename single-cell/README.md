## Single-Cell

How to run several combinations of HVGs, PCs, hyperparameters, etc. in parallel?

### Preparation

Original: [analysis.ipynb](single-cell/analysis.ipynb)

Convert to template: [analysis.template.ipynb](single-cell/analysis.template.ipynb)

- Parameterize
    - `experiment_id = 000`
    - `hvg_n_top_genes = 5000`
    - `pca_n_comps = 50`
    - `n_neighbors = 30`
- Remove hardcoded numbers
- If you already have an algorithm that figures an optimal parameter, use it (e.g. `KOptimzer`)

### Run

- Run one at a time: [run-serial.ipynb](single-cell/run-serial.ipynb)
- Run in parallel using Ray: [run-parallel-grid.ipynb](single-cell/run-parallel-grid.ipynb)

### Benefits

- The resulting notebook is end-user friendly
    - No giant for-loop
    - No tracking code
    - No parallelism code
- Took 3-5 min. to run on a MacBook pro
- Each experiment generates a notebook and h5ad file.
