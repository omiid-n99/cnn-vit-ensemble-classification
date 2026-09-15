# Deep Learning for Image Inpainting

## Project Objective

This project studies deep-learning methods for image inpainting: reconstructing
missing regions of an image from the visible surrounding content.

The project will compare three approaches:

1. A convolutional encoder-decoder model based on U-Net.
2. A lightweight Vision Transformer (ViT)-based reconstruction model.
3. An ensemble combining the predictions of U-Net and ViT.

## Dataset

The project will use the Oxford-IIIT Pet Dataset.

Images will be resized to a manageable resolution, initially 128x128 pixels,
to keep training practical on Google Colab.

## Inpainting Task

Artificial masks or occlusions will be generated on the original images.

The masked image will be given to the model as input, and the original
complete image will be used as the reconstruction target.

Conceptually:

Original Image -> Apply Mask -> Masked Image -> Model -> Reconstructed Image

## Mask Experiments

A small number of mask configurations will be tested.

The experiments should include different mask sizes and, where practical,
different mask shapes or positions.

The goal is to observe how reconstruction quality changes as the missing
region becomes more difficult to reconstruct.

Keep the number of mask experiments small and manageable.

## Models

### U-Net

A reasonably lightweight U-Net-style convolutional encoder-decoder will be
used as the CNN approach.

### Vision Transformer

A lightweight ViT-style model will be implemented for image reconstruction.

The ViT should remain small enough to train practically in Google Colab.

### Ensemble

After training U-Net and ViT independently, their reconstructed images will
be combined using a simple weighted average.

For example:

ensemble = alpha * unet_prediction + (1 - alpha) * vit_prediction

A small number of ensemble weights may be evaluated using the validation set.

## Evaluation

The main quantitative metrics will be:

- Mean Squared Error (MSE)
- Peak Signal-to-Noise Ratio (PSNR)
- Structural Similarity Index (SSIM)

The models will also be compared visually.

Representative examples should show:

Original | Masked | U-Net | ViT | Ensemble

## Failure Analysis

Several difficult or poorly reconstructed examples will be examined.

The discussion should identify situations where the models struggle and
whether U-Net and ViT exhibit different reconstruction behavior.

## Experimental Fairness

U-Net and ViT must use the same:

- training set
- validation set
- test set
- image resolution
- masking procedure for comparison
- evaluation metrics

The test set must not be used to select hyperparameters or ensemble weights.

## Computational Constraints

The project should remain computationally manageable on Google Colab.

Prefer simple and lightweight implementations rather than attempting
state-of-the-art architectures.

## Final Deliverables

The final submission will consist of:

- a well-documented Google Colab notebook
- experimental results and figures
- an approximately twelve-page report

The implementation should be simple enough that all important components
can be understood and explained during a possible discussion with the
professor.