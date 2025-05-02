## Handwritten Digit Recognition
This project demonstrates the evolution of a handwritten digit recognition system using the MNIST dataset, showing significant performance improvements through model architecture optimization.

### Project Overview
The repository contains two models for digit recognition:

* `handwritten.keras`: A simple neural network implementation (~40% accuracy, ~39% loss)
* `improved_handwritten.keras`: An optimized CNN-based model (~99.3% accuracy, ~2% loss)

The project shows how proper model architecture, preprocessing techniques, and training approaches can dramatically improve performance on image classification tasks.

### Models Comparison
Basic Model (`handwritten.keras`)

Implemented in main.py, this first approach uses a simple architecture:

* Architecture: Simple feedforward neural network
  * Flatten layer (converts 28×28 images to 784-length arrays)
  * Two dense layers with 128 neurons each
  * Output layer with 10 neurons (one per digit)
* Training Parameters:
  * Only 3 training epochs
  * Default Adam optimizer
  * No validation monitoring or early stopping
  * No data augmentation or normalization techniques
*Preprocessing:
  * Basic normalization using tf.keras.utils.normalize
  * No image reshaping for convolutional processing

Improved Model (`improved_handwritten.keras`)

Implemented in v2.py, this model uses modern CNN architecture with multiple optimization techniques:

* Architecture: Convolutional Neural Network (CNN)
  * Multiple convolutional layers (32 and 64 filters)
  * Batch normalization after convolutional layers
  * MaxPooling layers to reduce dimensionality
  * Strategic dropout layers (0.25 and 0.5) for regularization
  * 256-neuron dense layer before classification
* Training Parameters:
  * Up to 50 epochs with early stopping
  * Validation-based training with patience=3
  * Best weights restoration
  * Proper input shape management for CNNs (28×28×1)
* Preprocessing:
  * Proper normalization (division by 255.0)
  * Correct reshaping for CNN input (adding channel dimension)
  * Better image preprocessing pipeline for test images

### Key Improvements
1. Convolutional Architecture:
  * CNNs are specifically designed for image processing, capturing spatial relationships in the data.
2. Regularization Techniques:
  * Dropout layers to prevent overfitting
  * Batch normalization for faster, more stable training
3. Training Strategy:
  * Early stopping to prevent overfitting
  * Longer potential training time (50 epochs max vs. 3 fixed)
  * Monitoring validation loss for optimal model selection
4. Image Processing Pipeline:
  * Proper grayscale handling
  * Consistent resizing
  * MNIST-compatible inversion and normalization

### Usage
The repository includes code for:
1. Training both models on the MNIST dataset
2. Evaluating the models on custom images in the digits folder
3. Visualizing predictions and input images
To use the improved model on custom handwritten digits:
```
# The script will:
# 1. Load the improved model
# 2. Process images from the digits/ folder
# 3. Display predictions and visualizations
```
### Results
The improved model achieves approximately 99.3% accuracy and 2% loss on the test set, compared to around 40% accuracy and 39% loss for the basic model, demonstrating the importance of proper CNN architecture and training techniques in computer vision tasks.
