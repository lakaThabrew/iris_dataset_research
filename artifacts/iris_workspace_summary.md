# Iris Workspace Summary

This document collects the main facts, results, and visualizations from the Iris workspace notebooks, CSV files, and related text files.

## Project Snapshot

- Dataset: Iris classification with 150 samples and 4 numeric features: sepal_length, sepal_width, petal_length, and petal_width.
- Target classes: Iris-setosa, Iris-versicolor, and Iris-virginica.
- Class balance: 50 samples per class.
- Main workflow: baseline model comparison, tuning, repeated validation, confidence inspection, and model persistence.
- Final selected model: tuned SVM with RBF kernel.

## Core Facts From The Data

- The CSV file [data/iris.csv](../data/iris.csv) contains 150 rows and 5 columns.
- The feature columns are all float64 and the species column is categorical text.
- The dataset is balanced, which makes accuracy and cross-validation easier to interpret.
- The training and test split used in the workflow is 120 training samples and 30 test samples.

## Notebook Summaries

### Baseline Notebook

File: [notebooks/Baseline.ipynb](../notebooks/Baseline.ipynb)

- The notebook loads the Iris dataset, inspects unique values and distributions, and compares baseline classical machine learning models.
- The imported baseline models include K-Nearest Neighbors, Decision Tree, SVM, Random Forest, and Gaussian Naive Bayes.
- The best baseline model reported in the notebook is Gaussian NB.
- The reported test accuracy for that best baseline model is 0.9667.

Visualizations in this notebook:

- Histogram grid for the dataset features using `df.hist(figsize=(10, 8))`.
- Scatter plot of sepal_length vs sepal_width colored by species.
- Scatter plot of petal_length vs petal_width colored by species.
- Confusion matrix heatmap for the best baseline model.

### Pipeline Notebook

File: [notebooks/pipeline.ipynb](../notebooks/pipeline.ipynb)

- This notebook builds the complete classical ML pipeline.
- It includes baseline model comparison, stability checks across random seeds, hyperparameter tuning, diagnostics, model saving, and a small inference example.
- The baseline best model again is Gaussian NB.
- The notebook selects tuned SVM (RBF) as the final model.
- The final model uses approximately C = 26.8269579528 and gamma = 0.0138949549.
- The final model reports a single-split test accuracy of 1.0000.
- The notebook records the repeated validation summary: mean accuracy 0.9717, standard deviation 0.0320, and 95% confidence interval [0.9628, 0.9805].
- The classification report for the final held-out test split shows macro F1-score 1.0000 and weighted F1-score 1.0000.
- The model artifact is saved to [artifacts/iris_best_pipeline.joblib](iris_best_pipeline.joblib).
- The experiment log is written to [artifacts/experiment_log.csv](experiment_log.csv).

Visualizations in this notebook:

- Box plot of test accuracy across random seeds to show model stability.
- Confusion matrix heatmap for the final tuned model.
- Heatmap of class-wise feature means.
- Pair plot of Iris features colored by class.
- Interactive scatter widget for exploring feature pairs with class coloring.

### Repeated Validation Notebook

File: [notebooks/repeated.ipynb](../notebooks/repeated.ipynb)

- This notebook continues from the tuned SVM (RBF) model.
- It performs repeated stratified 5-fold cross-validation with 10 repeats.
- It inspects prediction confidence using probability outputs.
- It logs the final experiment results to CSV.
- The repeated CV results are: mean accuracy 0.9717, standard deviation 0.0320, and 95% CI [0.9628, 0.9805].
- The confidence summary shows the model is most confident on Iris-setosa and somewhat less confident on the other two classes.
- The notebook reports a confidence summary by predicted class with mean confidence values of about 0.9715 for Iris-setosa, 0.8811 for Iris-versicolor, and 0.8504 for Iris-virginica.

Visualizations in this notebook:

- Histogram of repeated cross-validation accuracy scores with a density curve.
- Box plot of prediction confidence by predicted class.
- Confusion matrix heatmap for the final predictions.

## Results Table

- Best baseline model: Gaussian NB.
- Best baseline test accuracy: 0.9667.
- Final tuned model: SVM (RBF).
- Final tuned model parameters: C ≈ 26.8269579528 and gamma ≈ 0.0138949549.
- Final held-out test accuracy: 1.0000.
- Repeated CV mean accuracy: 0.9717.
- Repeated CV standard deviation: 0.0320.
- Repeated CV 95% CI: [0.9628, 0.9805].
- Macro F1-score: 1.0000.
- Weighted F1-score: 1.0000.

## Related Files And Notes

- The paper draft in [conference_paper_draft.md](../conference_paper_draft.md) already matches the main final metrics and describes the workflow at a higher level.
- The assignment text in [Individual Research Task\_ Classical Machine Learning Study.txt](../Individual%20Research%20Task_%20Classical%20Machine%20Learning%20Study.txt) requires a classical ML project, baseline reproduction, and justified improvements.
- The extracted paper in [jdaip_2021083016105875_extracted.txt](../jdaip_2021083016105875_extracted.txt) is a separate reference text about dimension reduction methods and is not part of the Iris experiment results.

## Practical Takeaway

- The workspace is centered on a clean classical ML comparison for Iris classification.
- Gaussian NB is the strongest baseline.
- The tuned SVM (RBF) is the final model because it combines perfect held-out accuracy with stable repeated-validation results.
- The notebooks include both static plots and one interactive widget for exploratory analysis.
