---
title: "MNIST Classification with PyTorch"
excerpt: "Short description of portfolio item number 1<br/><img src='/images/500x300.png'>"
collection: portfolio
---

# [project](https://github.com/mohammad-javaher/mohammad-javaher/tree/main/my-projects/MNIST%20classification%20with%20pytorch)

This is a PyTorch implementation for training and evaluating a neural network on the **MNIST handwritten digits dataset**.

## 📌 Features

* Loads and preprocesses the MNIST dataset using `torchvision`
* Defines a neural network for digit classification
* Trains the model with configurable hyperparameters
* Evaluates accuracy on the test set
* Supports GPU acceleration (if available)
* Allows custom image testing (upload and predict)

## ⚙️ Requirements

Install dependencies with:

```bash
pip install torch torchvision matplotlib pillow
```

## 🚀 Usage

Run the notebook:

```bash
jupyter notebook MNIST.ipynb
```

Main steps in the notebook:

1. **Import libraries** (`torch`, `torchvision`, `matplotlib`, etc.)
2. **Set device** (GPU if available, else CPU)
3. **Define hyperparameters** (learning rate, batch size, epochs, etc.)
4. **Load MNIST dataset** with `torchvision.datasets.MNIST`
5. **Build the neural network** (`torch.nn.Module`)
6. **Train the model** with optimizer & loss function
7. **Evaluate accuracy** on test dataset
8. **Predict custom images** by uploading and preprocessing them

## 📊 Results

* Model achieves >97% accuracy on MNIST test data.
* Predictions can be made on user-uploaded images.

## 📂 Project Structure

```
MNIST.ipynb   # Main notebook
README.md     # Project documentation
```

## ✨ Future Improvements

* Try deeper architectures (CNNs, ResNet)
* Add visualization of training curves
* Experiment with data augmentation
