## Intro

How do I run a notebook from the terminal?

### Preparation

Original: [sum.ipynb](intro/sum.ipynb)

Change `x` and `y`, run the notebook from the terminal.

```bash
papermill sum.template.ipynb test.ipynb
```

Convert to template: [sum.template.ipynb](intro/sum.template.ipynb)

- Make a copy.
- Rename as `sum.template`.
- Add headings.
- Add a comment: `THESE VALUES SHOULD BE OVERRIDDEN AT THE EXECUTION TIME`
- Add a tag: `parameters` (Jupyter Notebook vs. Jupyter Lab)

### Run

Change `x` and `y`, run the notebook from the terminal.

```bash
papermill sum.template.ipynb sum.results.ipynb \
    -p x 12 \
    -p y 316
```

### `parameters` and `injected-parameters`

The cell tagged with `parameters` is the one that `papermill` looks for.

The cell tagged with `injected-parameters` is the one that `papermill` injects your execution-time parameters into.

Note that `papermill` does not delete the cell tagged with `parameters`, thus you will see sets of parameters, default ones and your injected parameters, but the default parameters will be overriden by your injected parameters.
