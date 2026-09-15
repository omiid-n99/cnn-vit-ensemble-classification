# AGENTS.md

## Project

This is a university Deep Learning project about image inpainting.

The project compares:

1. U-Net
2. A lightweight Vision Transformer (ViT)
3. A weighted ensemble of U-Net and ViT

The full project specification is in:

PROJECT_DESCRIPTION.md

Read that file before making major implementation decisions.

## Main Rules

Keep the project simple.

This is not a production software project.

The main implementation must stay inside:

notebooks/image_inpainting.ipynb

Do not create unnecessary infrastructure such as:

- src/
- configs/
- tests/
- splits/
- CLI tools
- experiment managers
- YAML configuration systems
- model registries
- deployment code

Do not add new top-level directories unless explicitly requested.

## Dataset

Use the Oxford-IIIT Pet Dataset.

Resize images to 128x128.

Use deterministic train/validation/test splits.

The same splits must be used for U-Net and ViT.

Do not use the test set for model selection or ensemble-weight selection.

## Inpainting Task

Artificial masks will be applied to complete images.

The masked image is the model input.

The original complete image is the target.

Primary mask sizes:

- 24x24
- 32x32
- 48x48

Support:

- central rectangular masks
- randomly positioned rectangular masks

Keep masking simple.

## Models

### U-Net

Use a lightweight U-Net-style encoder-decoder with skip connections.

### ViT

Use a lightweight ViT-based reconstruction model.

A reasonable starting configuration is:

- image size: 128
- patch size: 16
- embedding dimension: 128 or 256
- about 4 attention heads
- about 4 Transformer blocks

Keep it practical for Google Colab.

### Ensemble

Use a simple weighted average:

ensemble = alpha * unet_prediction + (1 - alpha) * vit_prediction

Choose alpha using the validation set, not the test set.

## Evaluation

Required metrics:

- MSE
- PSNR
- SSIM

Also include:

- qualitative reconstruction examples
- comparison of different mask sizes
- failure-case analysis

Useful visual layout:

Original | Masked | U-Net | ViT | Ensemble

Never fabricate results.

## Notebook Structure

The notebook should roughly contain:

1. Introduction
2. Imports and configuration
3. Dataset loading
4. Train/validation/test split
5. Mask generation
6. Mask visualization
7. U-Net
8. U-Net training/evaluation
9. ViT
10. ViT training/evaluation
11. Ensemble
12. Mask-size experiments
13. Quantitative comparison
14. Qualitative comparison
15. Failure analysis
16. Conclusion

## Working Style

Work incrementally.

Do not implement the whole project at once.

Preferred order:

1. Dataset
2. Masks
3. U-Net
4. U-Net training/evaluation
5. ViT
6. ViT training/evaluation
7. Ensemble
8. Additional mask experiments
9. Final comparisons and cleanup

Before making a major change:

1. inspect the current notebook
2. modify only the requested stage
3. avoid unrelated changes
4. keep the code readable
5. explain important decisions

Prefer simple PyTorch code that is easy to understand and explain.