## Diabetes Classification

Find a classifier that gives me the highest accuracy.

### Preparation

Original: [classifier.ipynb](diabetes/classifier.ipynb)

- Initially uses the DecisionTree classifier.

Convert to template: [classifier.template.ipynb](diabetes/classifier.template.ipynb)

- Import a bunch of scikit-learn classifiers.
- Tag the confusion matrix cell with `confusion`.
- Tag the accuracy cell with `accuracy`.
- Tag the ROC curve with `roc`.

### Run

- Add different classifiers to `experiments`.
- Run Papermill's `execute_notebook` function from Python.
- Use `sklearn_evaluation` to load up all the generated notebooks
- Compare those tagged cells (e.g. `confusion`, `accuracy`, `roc`)
- Each classifier will have a notebook and a model in pickle format.
