# Telco Customer Churn Prediction

This project builds a beginner-friendly machine learning model to predict customer churn using the Telco Customer Churn dataset.

The goal is not only to train a model, but to understand the full classification workflow: data cleaning, feature selection, model comparison, threshold tuning, and evaluation.

## Learning Goals

By the end of this project, you should understand:

- How to load and inspect a real dataset
- How to clean messy columns like `TotalCharges`
- How to split data into train, validation, and test sets
- How to compare classification models
- Why accuracy is not enough for churn prediction
- How precision, recall, F1, false positives, and false negatives work
- Why changing the prediction threshold changes model behavior

## Dataset

The project uses the Telco Customer Churn dataset.

Each row represents a customer. The target column is `Churn`:

- `Yes` means the customer churned
- `No` means the customer stayed

## Models Compared

The notebook compares:

- Logistic Regression
- Balanced Logistic Regression
- Random Forest

The workflow selects both the best model and the best decision threshold using validation data before evaluating on the test set.

## Current Result

The selected model was:

```text
Random Forest
Threshold: 0.40
```

Final test performance:

```text
Accuracy:   0.787
Precision:  0.592
Recall:     0.639
F1 Score:   0.614
ROC-AUC:    0.844
PR-AUC:     0.654
```

## How To Run

If you use `mise`, install the configured tools first:

```sh
mise install
```

Install dependencies:

```sh
uv sync
```

Start Jupyter:

```sh
uv run jupyter notebook
```

Then open:

```text
notebooks/01_telco_churn_baseline.ipynb
```

## Key Lesson

A churn model does not only produce a prediction. It usually produces a probability.

The threshold turns that probability into a business decision:

```text
Predict churn if churn probability >= threshold
```

A lower threshold catches more churners but creates more false positives. A higher threshold creates fewer false positives but misses more churners.

That tradeoff is why churn prediction is not just a modeling problem. It is also a business decision.

## Note

This is a learning project, not a production churn system.
