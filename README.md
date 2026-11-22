# Vanilla GAN using PyTorch

## Overview

This project implements a Vanilla Generative Adversarial Network (GAN) from scratch using PyTorch.

The model consists of two neural networks, a Generator and a Discriminator, trained against each other to generate realistic images from random noise.

The implementation explores the fundamental working principles of GANs, including adversarial training, loss functions, and optimization.

## Features

- Vanilla GAN architecture implemented using PyTorch.
- Fully connected Generator and Discriminator networks.
- Image preprocessing using Torchvision.
- Adversarial training using Binary Cross-Entropy loss.
- Adam optimizer for both networks.
- Periodic visualization of generated images.
- Model checkpoint saving and loading.

## Technologies Used

- Python
- PyTorch
- Torchvision
- NumPy
- Matplotlib
- Pillow
- Jupyter Notebook

## Model Architecture

### 1. Generator

The Generator takes a random noise vector of dimension 100 as input and transforms it into a 64×64 RGB image.

Its architecture consists of fully connected layers:

- 100 → 256 neurons
- 256 → 512 neurons
- 512 → 1024 neurons
- 1024 → 12,288 neurons (64 × 64 × 3)

ReLU activation is used in the hidden layers, followed by Tanh in the output layer.

### 2. Discriminator

The Discriminator receives an RGB image of size 64×64 and predicts whether it is real or generated.

Its architecture consists of fully connected layers:

- Input image → 1024 neurons
- 1024 → 512 neurons
- 512 → 256 neurons
- 256 → 1 output

LeakyReLU activation is used in the hidden layers.

## Training Configuration

| Parameter | Value |
|---|---|
| Latent dimension | 100 |
| Image size | 64 × 64 |
| Image channels | 3 (RGB) |
| Batch size | 128 |
| Loss function | BCEWithLogitsLoss |
| Optimizer | Adam |
| Learning rate | 0.0002 |
| Adam betas | (0.5, 0.999) |

## Image Preprocessing

Images are processed using Torchvision transforms:

1. Center cropping to 178×178.
2. Resizing to 64×64.
3. Converting images into tensors.
4. Normalizing pixel values to the range [-1, 1].

The processed images are loaded using PyTorch DataLoader with a batch size of 128.

## Training Process

The GAN is trained through an adversarial process:

1. Random noise is passed to the Generator to create fake images.
2. The Discriminator receives both real and generated images.
3. The Discriminator learns to distinguish real images from fake images.
4. The Generator is trained to produce images that the Discriminator classifies as real.
5. Generated images are periodically visualized during training.

The implementation uses separate Adam optimizers for the Generator and Discriminator.

## Getting Started

### 1. Clone the repository

```bash
git clone <YOUR_REPOSITORY_URL>
cd vanilla-gan-pytorch
```

### 2. Install dependencies

```bash
pip install torch torchvision numpy matplotlib pillow jupyterlab
```

### 3. Prepare the dataset

Place your training images inside a folder named `Images` in the project directory.

The notebook expects this folder to be available locally. The dataset is not included in the repository.

### 4. Launch JupyterLab

```bash
jupyter lab
```

Open `Vanilla_GAN.ipynb` and execute the notebook cells.

**Important:** The notebook contains a checkpoint-loading cell that expects `vanilla_gan_checkpoint.pth`. Since trained checkpoints are not included in this repository, skip that cell when training from scratch. The notebook initializes both networks and optimizers before this step.

A CUDA-compatible GPU is recommended because the notebook currently specifies CUDA as its execution device.

## Checkpoints

Trained model checkpoints are intentionally not included in this repository because of their large file sizes.

The notebook includes code to save the Generator, Discriminator, and optimizer states locally after training.

## Limitations

- Uses fully connected layers rather than convolutional layers.
- Image generation is limited to 64×64 RGB resolution.
- Training requires a local image dataset.
- Training can be computationally expensive.
- Model checkpoints are not included in the repository.

## Future Improvements

- Experiment with different Generator and Discriminator architectures.
- Improve image quality and training stability.
- Experiment with different latent dimensions and hyperparameters.
- Explore convolutional GAN architectures.

## Author

**Udit Agrawal**

B.Tech Artificial Intelligence Student