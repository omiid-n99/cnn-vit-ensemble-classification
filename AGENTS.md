# Project Instructions

## Project

This is a university deep-learning project about image inpainting.

The project compares:

1. U-Net
2. A lightweight Vision Transformer reconstruction model
3. A weighted ensemble of U-Net and ViT

The dataset is Oxford-IIIT Pets.

Images will be resized to 128x128 pixels.

Artificial masks will be used to create missing image regions.

Main mask sizes:

- 24x24
- 32x32
- 48x48

The project will evaluate:

- MSE
- PSNR
- SSIM
- qualitative reconstruction quality
- failure cases

The final deliverables are a well-documented Google Colab notebook and
an approximately 12-page academic report.

## Important Simplicity Requirement

Keep this project simple.

This is a university experimental project, not a production software
engineering project.

DO NOT create additional architecture or infrastructure unless explicitly
requested.

In particular, do not create:

- src/ packages
- configuration systems
- YAML experiment files
- formal test suites
- persistent split files
- command-line applications
- unnecessary abstractions
- complex training frameworks

The main implementation should remain inside:

notebooks/image_inpainting.ipynb

Use ordinary Python functions and PyTorch classes inside the notebook to
keep the code readable and understandable.

## Repository Structure

Keep the repository approximately as follows:

AGENTS.md
README.md
requirements.txt
notebooks/
    image_inpainting.ipynb
results/
    plots/
    reconstructions/

Do not add new top-level directories without explicit permission.

## Notebook Organization

The notebook should eventually contain approximately these sections:

1. Introduction
2. Setup and imports
3. Experiment configuration
4. Dataset loading
5. Dataset splitting
6. Image preprocessing
7. Mask generation
8. Mask visualization
9. U-Net
10. U-Net training
11. Lightweight ViT
12. ViT training
13. Evaluation
14. Ensemble
15. Mask-size experiments
16. Quantitative comparison
17. Qualitative comparison
18. Failure analysis
19. Conclusion

## Implementation Style

Prefer simple functions and classes.

Examples:

- create_mask(...)
- train_model(...)
- evaluate_model(...)
- compute_metrics(...)
- UNet
- InpaintingViT

Do not move these into separate modules unless explicitly requested.

Use clear Markdown cells to explain important steps.

Keep important experiment settings visible in one notebook cell.

For example:

SEED
IMAGE_SIZE
BATCH_SIZE
LEARNING_RATE
NUM_EPOCHS
MASK_SIZES
DEVICE

## Reproducibility

Use fixed random seeds for:

- Python
- NumPy
- PyTorch

Create one deterministic train/validation/test split.

The same split must be used for U-Net and ViT.

The test set must not be used for model selection or hyperparameter tuning.

## Computational Constraints

The project must be practical to run on Google Colab.

Prefer lightweight architectures and reasonable training times.

Avoid unnecessary experiments or very large models.

## Academic Requirements

Do not fabricate results.

All numerical results must come from actual experiments.

Keep the implementation simple enough that every important component can
be understood and explained during a possible discussion with the professor.

Do not implement multiple major stages at once unless explicitly requested.

Work incrementally.
