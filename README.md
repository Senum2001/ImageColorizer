# Image Colorizer Model

This repository contains an image colorizer model designed to convert grayscale images to color images using deep learning techniques. The model employs a Convolutional Neural Network (CNN) architecture with distinct encoder and decoder sections.

## Model Architecture

### Encoder

The encoder extracts features from the input grayscale image through a series of convolutional layers:

1. **First Convolutional Layer**: Applies 64 filters of size 3x3, with ReLU activation, padding to preserve spatial dimensions, and a stride of 2 to reduce the spatial resolution by half.
2. **Second Convolutional Layer**: Applies 128 filters of size 3x3, with ReLU activation and padding.
3. **Third Convolutional Layer**: Another 128 filters of size 3x3, with ReLU activation, padding, and a stride of 2 for further spatial downsampling.
4. **Fourth Convolutional Layer**: Uses 256 filters of size 3x3, with ReLU activation and padding.
5. **Fifth Convolutional Layer**: Another 256 filters of size 3x3, with ReLU activation, padding, and a stride of 2.
6. **Sixth and Seventh Convolutional Layers**: Both use 512 filters of size 3x3, with ReLU activation and padding, for deep feature extraction.
7. **Eighth Convolutional Layer**: Uses 256 filters of size 3x3, with ReLU activation and padding.

### Decoder

The decoder reconstructs the colorized image from the encoded features:

1. **Ninth Convolutional Layer**: Applies 128 filters of size 3x3, with ReLU activation and padding.
2. **First Upsampling Layer**: Upsamples the feature map by a factor of 2 to increase the spatial resolution.
3. **Tenth Convolutional Layer**: Uses 64 filters of size 3x3, with ReLU activation and padding.
4. **Second Upsampling Layer**: Further upsamples the feature map by a factor of 2.
5. **Eleventh Convolutional Layer**: Applies 32 filters of size 3x3, with ReLU activation and padding.
6. **Twelfth Convolutional Layer**: Uses 16 filters of size 3x3, with ReLU activation and padding.
7. **Final Convolutional Layer**: Applies 2 filters of size 3x3, with a LeakyReLU activation (alpha=0.01) and padding, followed by another upsampling layer.

## Summary

- **Input**: Grayscale image of size 256x256.
- **Output**: Colorized image of size 256x256 with LAB color channels normalized.
- **Loss Function**: Mean Squared Error (MSE) or another appropriate loss function for colorization tasks.
- **Optimizer**: Adam or another suitable optimizer for training the model.

## Usage

The model is trained on pairs of grayscale and color images. During inference, it takes a grayscale image as input and outputs a colorized version, effectively learning the mapping from grayscale intensity values to color information. This model is useful for applications in image restoration, old photo colorization, and enhancing grayscale images with vibrant colors.

## Requirements

- Python 3.x
- TensorFlow
- scikit-image
- matplotlib
- numpy
