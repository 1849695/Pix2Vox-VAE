# Pix2Vox++ VAE: 3D Object Reconstruction with Variational Autoencoder

This project is a reimplementation and modification of the paper "Pix2Vox++: Multi-scale Context-aware 3D Object Reconstruction from Single and Multiple Images" with a significant change to the encoder-decoder architecture, transforming it into a Variational Autoencoder (VAE).

## Overview

The original Pix2Vox++ is a state-of-the-art method for 3D object reconstruction from single or multiple images. This implementation maintains the multi-scale context-aware approach while introducing a VAE architecture for the encoder-decoder, potentially allowing for more robust and generative 3D reconstructions.

## Key Features

- VAE-based encoder-decoder architecture for 3D object reconstruction
- Multi-scale context-aware approach from the original Pix2Vox++
- Support for both single and multiple image inputs
- [Add any additional features specific to your implementation]

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/pix2vox-vae.git
cd pix2vox-vae

# Install dependencies
pip install -r requirements.txt
```

### Usage



## Model Architecture

This implementation differs from the original Pix2Vox++ in the following ways:

1. Encoder: It is based on a modified version of VGG16 with batch normalization (VGG16_bn). It processes multi-view 2D images as input and extracts features through a series of convolutional layers. The encoder architecture is composed of the following key components:
   1. **Input**: Multi-view images of 3D objects
   - Shape: [batch_size, n_views, channels, height, width]

   2. **Feature Extraction**:
   - Base: Pre-trained VGG16 with batch normalization (first 27 layers)
   - Additional layers:
     - Conv2D → BatchNorm → ELU
     - Conv2D → BatchNorm → ELU → MaxPool
     - Conv2D (1x1) → BatchNorm → ELU

   3. **Multi-view Processing**:
   - Each view processed independently
   - Features aggregated by mean across views

   4. **Latent Space Projection**:
   - Two fully connected layers:
     - fc_mu: Produces mean (μ)
     - fc_log_sigma: Produces log standard deviation (log σ)

   5. **Reparameterization**:
   - Samples latent vector z using μ and σ

Outputs are the following:
- μ (mean of latent distribution)
- log σ (log standard deviation of latent distribution)
- z (sampled latent vector)

2. Decoder: [Describe your VAE decoder architecture]
3. Latent Space: [Explain how the latent space is structured and used]


## Results

[Provide some example results, comparisons with the original Pix2Vox++, or any metrics you've used to evaluate your model]

## Citation


```
@inproceedings{xie2020pix2vox++,
  title={Pix2Vox++: Multi-scale Context-aware 3D Object Reconstruction from Single and Multiple Images},
  author={Xie, Haozhe and Yao, Hongxun and Sun, Xiaoshuai and Zhou, Shangchen and Zhang, Shengping},
  booktitle={International Journal of Computer Vision},
  year={2020}
}
```
