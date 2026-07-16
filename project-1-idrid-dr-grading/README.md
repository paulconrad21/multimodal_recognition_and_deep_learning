# Project 1: Diabetic Retinopathy Grading on IDRiD

This repository folder contains the code, result tables, and final report for the first project. The goal of the project was to compare different deep learning approaches for five-class diabetic retinopathy grading on the IDRiD dataset.

The experiments include convolutional neural networks, a Vision Transformer, preprocessing variants, imbalance handling strategies, hyperparameter tuning, and ensemble methods.

## Dataset

The experiments use the IDRiD diabetic retinopathy grading dataset. The dataset itself is not included in this repository because it is provided externally and can be large. The notebooks were mainly executed on Kaggle and expect the dataset to be available through Kaggle input paths.

## Repository Structure

```text
project-1-idrid-dr-grading/
  notebooks/
    cnn/          ResNet and EfficientNet experiments
    vit/          Vision Transformer experiments
    ensembles/    Ensemble and logit-fusion experiments
  results/
    experiment_results/   CSV summaries for individual model runs
    ensembles/            CSV summaries for ensemble experiments
```

## Main Notebooks

- `notebooks/cnn/resnet-eyes-v7-r1-r7-experiment-matrix.ipynb`  
  ResNet-18 experiment matrix.

- `notebooks/cnn/efficientnet-b0-eyes-v2-r1-r7-experiment-matrix.ipynb`  
  EfficientNet-B0 experiment matrix.

- `notebooks/cnn/efficientnet-b2-eyes-v4-b2-1-b2-4-targeted-matrix.ipynb` and `notebooks/cnn/efficientnet-b2-eyes-v5-final-two-cpu-friendly-runs.ipynb`  
  EfficientNet-B2 experiments.

- `notebooks/cnn/efficientnet-b2-partner-preprocessing-screen-confirm-gradcam-ready.ipynb`  
  Additional preprocessing experiments and Grad-CAM export.

- `notebooks/vit/final-experiment-vit.ipynb`  
  Vision Transformer experiments.

- `notebooks/ensembles/ensemble-strong-old-plus-new-preprocessing-v3.ipynb`  
  Main ensemble experiment.

- `notebooks/ensembles/ensemble-logit-fusion-v1.ipynb`  
  Logit-level ensemble experiment.

## Results

The main result tables are stored as CSV files in `results/`. The final report summarizes the most important findings and compares the individual models, preprocessing variants, and ensembles.

The strongest individual CNN model was based on EfficientNet-B2. The best final performance was achieved by an ensemble that combined several complementary CNN models and preprocessing variants.

## Report

The final report is available here:

```text
report/project_1_report_conrad.pdf
```

## Notes

Trained model checkpoints (`.pth` files) are not included because of file size and storage considerations. The notebooks can be rerun on Kaggle if the dataset and required checkpoint outputs are attached.
