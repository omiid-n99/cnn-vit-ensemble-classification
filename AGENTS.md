# Project Instructions

## Project Overview

This is a university deep-learning project focused on image classification.

The project will compare:

1. A conventional CNN baseline.
2. A proposed deep-learning approach.
3. A Vision Transformer (ViT).
4. Ensemble models combining selected trained models.

The final project must include a fair experimental comparison between
the approaches.

The final submission will consist of:
- a well-documented implementation/notebook
- experimental results
- plots and comparison tables
- an approximately 12-page academic report

## Computational Constraints

Experiments must be feasible on Google Colab.

Prefer:
- lightweight models
- transfer learning where appropriate
- reasonable image resolutions
- reasonable batch sizes
- efficient training procedures

Avoid unnecessarily expensive architectures or experiments.

## Framework

Use Python and PyTorch.

Prefer standard, well-maintained libraries such as:
- torch
- torchvision
- timm
- scikit-learn
- numpy
- pandas
- matplotlib

Do not introduce unnecessary dependencies.

## Repository Structure

Use the existing repository structure.

src/
    data.py
    train.py
    evaluate.py
    utils.py
    models/
        baseline.py
        proposed_model.py
        vit.py
        ensemble.py

configs/
notebooks/
results/
tests/

Keep reusable logic inside src/.

The notebook should orchestrate experiments rather than contain large
amounts of duplicated implementation code.

## Experimental Requirements

All model comparisons must be fair.

Use:
- the same train/validation/test splits
- the same held-out test set
- consistent preprocessing where appropriate
- consistent evaluation metrics
- fixed random seeds

The test set must never be used for:
- training
- hyperparameter selection
- model selection

Prevent data leakage.

## Reproducibility

Set random seeds for:
- Python
- NumPy
- PyTorch
- CUDA when available

Experiments should be reproducible as far as reasonably possible.

Important hyperparameters must be configurable rather than hardcoded.

## Evaluation

At minimum, support:

- accuracy
- precision
- recall
- F1-score
- confusion matrix
- training loss curves
- validation loss curves
- training/validation accuracy curves

Where appropriate, include:
- per-class metrics
- parameter count
- training time

Results should be exportable to files under results/.

## Results

Use:

results/metrics/
results/plots/
results/tables/

Save machine-readable metrics as CSV or JSON where appropriate.

Figures should be suitable for inclusion in the final academic report.

## Code Quality

Code should be:
- modular
- readable
- documented
- reasonably typed where useful
- easy to execute from Google Colab

Avoid:
- unnecessary abstractions
- excessive boilerplate
- duplicated code
- hardcoded local paths

Use docstrings for important classes and functions.

## Testing

Add lightweight tests and sanity checks for important components.

Tests should not require full model training.

Useful tests include:
- dataset loading
- expected tensor shapes
- model forward passes
- output dimensions
- ensemble calculations

## Model Development

Do not implement several major components at once unless explicitly asked.

Preferred implementation order:

1. dataset pipeline
2. training/evaluation infrastructure
3. CNN baseline
4. proposed model
5. ViT model
6. ensemble methods
7. experiment notebook
8. final cleanup and review

Before making a major architectural decision, explain the reasoning.

## Academic Integrity

Do not fabricate experimental results.

Any reported performance values must come from actual experiments.

When interpreting results, distinguish clearly between measured results
and hypotheses or explanations.

The implementation should be understandable enough that the student can
explain and defend it during a possible discussion with the professor.