# Iris Classical Machine Learning Study

This repository contains an end-to-end classical machine learning workflow for the Iris dataset, including:

- baseline model benchmarking
- stability checks across multiple random seeds
- hyperparameter tuning
- final model selection and evaluation
- experiment logging and saved model artifacts

## Project Structure

- `data/iris.csv`: Iris dataset used for training and evaluation
- `notebooks/Baseline.ipynb`: baseline EDA and classifier comparison
- `notebooks/pipeline.ipynb`: full pipeline with stability checks, tuning, and final selection
- `notebooks/repeated.ipynb`: repeated validation and confidence-focused reporting
- `artifacts/`: generated outputs (trained model, logs, summaries)
- `conference_paper_draft.md`: paper draft based on the experiment results

## Models Covered

- Logistic Regression
- K-Nearest Neighbors (KNN)
- Decision Tree
- Support Vector Machine (RBF)
- Random Forest
- Gaussian Naive Bayes

## Key Results (Current)

From the pipeline and repeated-validation workflow:

- Best tuned models on held-out test split include SVM (RBF) and KNN with very high accuracy
- Repeated validation confirms stable performance across stratified splits
- Final comparisons include baseline vs tuned accuracy and improvement per model

See notebooks for exact run outputs and tables.

## How To Run

1. Open the project in VS Code.
2. Open and run notebooks in this order:
   1. `notebooks/Baseline.ipynb`
   2. `notebooks/pipeline.ipynb`
   3. `notebooks/repeated.ipynb`
3. Review outputs and generated files in `artifacts/`.

## Reproducibility Notes

- Most workflows use `random_state=42` for consistent splits/search where applicable.
- Hyperparameter tuning is done with `RandomizedSearchCV`.
- Final model and encoder artifacts are persisted to the `artifacts/` folder.

## GitHub Push Checklist

- Ensure notebook outputs are in the state you want to publish.
- Keep large generated binaries minimal (or use Git LFS if needed).
- Add a `.gitignore` for temporary files and caches if not already present.

---

If you use this repository for reports or publication drafts, cite your notebook version/date to keep results traceable.
