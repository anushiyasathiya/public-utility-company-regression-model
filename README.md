# public-utility-company-regression-model

# Week 9 Quiz: Revenue Forecasting with Simple Linear Regression

This notebook builds and compares two simple linear regression models that forecast monthly revenue using degree-day weather variables (`coolDD` and `heatDD`), then evaluates which one generalizes better on held-out data.

## Data

- **Source file:** `AICPA_regressionAnalysisData.csv`
- **Columns used:** `date`, `revenue`, `production`, `coolDD`, `heatDD`, `type`
- The `type` column splits rows into `dt4training` and `dt4testing` subsets.

## Workflow

1. **Load & prep** — Import `pandas`, `numpy`, `matplotlib`, and `statsmodels`; load the CSV and convert `date` to a proper datetime type.
2. **Explore** — Plot monthly revenue over time and compute a correlation matrix across `revenue`, `production`, `coolDD`, and `heatDD` to get an early read on which variable might predict revenue best.
3. **Split** — Separate the data into training (`dt4training`) and testing (`dt4testing`) sets.
4. **Model 1** — OLS regression of `revenue` on `coolDD` (training data only).
5. **Model 2** — OLS regression of `revenue` on `heatDD` (training data only).
6. **Forecast** — Use both fitted models to predict revenue on the testing set.
7. **Evaluate** — Compute each model's Mean Absolute Percentage Error (MAPE) on the test set.
8. **Visualize** — Plot actual vs. predicted revenue for both models over the test period.

## Results

Per the notebook output:

| Model | Predictor | Test MAPE |
|---|---|---|
| Model 1 | `coolDD` | ~29.6% |
| Model 2 | `heatDD` | ~21.6% |

**Conclusion (from the notebook's memo):** Model 2 (`heatDD`) outperforms Model 1 (`coolDD`) on the test set, consistent with `heatDD` showing a stronger raw correlation with revenue than `coolDD`. If a single model must be chosen, `heatDD` is the better predictor.

I pulled these figures directly from the notebook's printed output — you may want to re-run the notebook yourself to confirm before citing them elsewhere.

## Requirements

```
pandas
numpy
matplotlib
statsmodels
```

## Usage

1. Place `AICPA_regressionAnalysisData.csv` in the same directory as the notebook.
2. Open `Week 9 Quiz.ipynb` in Jupyter or Google Colab.
3. Run all cells in order.

## Notes

- This README was generated from a PDF export of the Colab notebook, so it reflects the code and outputs visible in that export rather than the live `.ipynb` file. If you've changed the notebook since exporting, some details here may be out of date.
