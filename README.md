# Deep Learning for Image Inpainting

University Deep Learning project comparing methods for reconstructing missing
image regions on the **Oxford-IIIT Pet Dataset**, resized to 128 x 128 RGB.

## Methods and evaluation

- Lightweight **U-Net** with encoder–decoder skip connections.
- Lightweight **Vision Transformer**: the initial 16 x 16 patch experiment is
  retained alongside the improved 8 x 8 patch model with a convolutional decoder.
- **Weighted U-Net–ViT ensemble**, using validation-selected alpha 0.75.

Training uses 32 x 32 central masks and masked-region MSE. Final test evaluation
covers 24 x 24, 32 x 32, and 48 x 48 masks at central and deterministic random
positions. Models share the same data splits and masked inputs; visible pixels
remain unchanged.

Metrics include **MSE, PSNR, and SSIM**, plus masked-region MSE and PSNR.
The notebook contains saved validation/test results, reconstruction comparisons,
and failure analysis. Model checkpoints and ensemble alpha were selected using
validation data before final evaluation on the official test split.

## Notebook and Google Colab

The complete implementation is in
[notebooks/image_inpainting.ipynb](notebooks/image_inpainting.ipynb).

1. Open [Google Colab](https://colab.research.google.com/) and upload the notebook.
2. View the saved outputs to inspect the completed experiment without execution.
3. To reproduce the experiment, select a GPU runtime and run cells in order.
   Dataset-loading cells download Oxford-IIIT Pet; training cells train the models.

The notebook uses PyTorch, torchvision, NumPy, Matplotlib, pandas, and scikit-image.
Best weights are held in memory during execution; saved outputs do not include
model weights. Full execution performs training again.
