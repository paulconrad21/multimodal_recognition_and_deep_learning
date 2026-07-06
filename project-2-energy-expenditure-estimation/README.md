# Project 2: Energy Expenditure Estimation from Wearable Sensors

This repository folder contains the notebooks, result tables, and result figures for the second project. The goal of the project was to estimate energy expenditure from wearable biosignal time series and to compare single-signal models with multi-signal fusion strategies.

The experiments use a residual temporal convolutional network as the main deep learning model. Additional model candidates, such as FCN, residual CNN, Inception-style CNN, and GRU models, were used during model selection.

## Dataset

The experiments use a wearable sensor dataset for energy expenditure estimation. The dataset can be found here:
https://figshare.com/articles/dataset/Predicting_energy_cost_from_wearable_sensors/7473191

Most notebooks were executed on Kaggle and expect the dataset to be available through Kaggle input paths. These paths may need to be adjusted before rerunning the notebooks.

## Repository Structure

```text
project-2-energy-expenditure-estimation/
  notebooks/
    01-data-analysis.ipynb
    02-model-selection.ipynb
    03-optuna-tuning-best-models.ipynb
    04-single-signal-experiments.ipynb
    05-fusion-strategies.ipynb
    06-fusion-results-visualization.ipynb
  results/
    best_strategy_per_group.csv
    fold_results_summary.csv
    group_strategy_ranking.csv
    graphs/
```

## Main Notebooks

- `notebooks/01-data-analysis.ipynb`  
  Exploratory data analysis, signal inspection, missing value checks, segment construction, and windowing decisions.

- `notebooks/02-model-selection.ipynb`  
  Comparison of several time-series model architectures under Leave-One-Subject-Out cross-validation.

- `notebooks/03-optuna-tuning-best-models.ipynb`  
  Hyperparameter tuning for the strongest candidate models using Optuna.

- `notebooks/04-single-signal-experiments.ipynb`  
  Single-signal experiments for all allowed input signals using the selected model architecture.

- `notebooks/05-fusion-strategies.ipynb`  
  Multi-signal fusion experiments for signal groups G1 to G6 using early, intermediate, and late fusion.

- `notebooks/06-fusion-results-visualization.ipynb`  
  Visualization of the final fusion results and generation of poster-ready plots.

## Method Summary

The time series were split into 30-second windows with a step size of 10 seconds. Models were evaluated using Leave-One-Subject-Out cross-validation to test generalization to unseen subjects.

The final experiments compare three fusion strategies:

- Early fusion: signals are stacked as input channels and processed by one shared model.
- Intermediate fusion: each signal is encoded by its own residual TCN branch, and the learned embeddings are combined.
- Late fusion: each signal is modeled separately, and the individual predictions are combined by a learned linear layer.

## Results

The main result tables are stored in `results/`. Poster-ready figures are stored in `results/graphs/`.

Overall, Minute Ventilation was the strongest individual signal. Fusion was most useful for signal groups without the dominant ventilation signal, while adding more sensors did not automatically improve generalization.

## Notes

Raw data files and trained model checkpoints are not included. The notebooks can be rerun on Kaggle if the dataset is attached and the input paths are adjusted.
