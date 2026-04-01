# 🌱 AI-Model: ResNet for Garbage Classification

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.13-orange?logo=tensorflow)
![License](https://img.shields.io/badge/License-MIT-green)
![GitHub Repo](https://img.shields.io/badge/GitHub-AI--model-black?logo=github)

This repository contains a **ResNet model for garbage classification**, designed to classify recyclable and non-recyclable materials. The focus is on **image-based classification** for environmental applications.

## 🗂 Project Structure

- `ResNet.ipynb` – Notebook containing the ResNet model implementation.  
- `model.hd5` – Saved Keras model in HDF5 format.  
- `README.md` – This file.  

## 📸 Dataset

The dataset includes images of six classes:

- `cardboard`  
- `glass`  
- `metal`  
- `paper`  
- `plastic`  
- `trash`  

Images are resized to **224x224 pixels** before training.

## 🧠 ResNet Model Architecture

- Based on **Residual Blocks** (ResNet architecture)  
- Convolutional layers (`Conv2D`) with **ReLU activation**  
- Max pooling layers (`MaxPooling2D`) after each block  
- Flatten layer followed by a dense output layer with **softmax activation**  
- Loss function: `categorical_crossentropy`  
- Optimizer: `Adam`  

This model can be used for **image classification tasks** and exported for **mobile deployment**.

## 🚀 How to Use

1. Clone this repository:
git clone https://github.com/fadou4/AI-model.git
cd AI-model

2. Install dependencies:
pip install tensorflow numpy matplotlib pillow scikit-learn

If you are using Anaconda, create an environment:
conda create -n ai_model python=3.10
conda activate ai_model
pip install tensorflow numpy matplotlib pillow scikit-learn

3. Run the notebook:
jupyter notebook

Open the file:
ResNet.ipynb

Run the cells sequentially to load the dataset, train the model, evaluate it, and save the trained model.

Dataset Loading and Preprocessing:

Images are loaded from directories and resized to 224x224 pixels. Example preprocessing:

import torchvision.transforms as T

transformer = T.Compose([
    T.Resize((224,224)),
    T.ToTensor()
])

The dataset is divided into training, validation, and test sets to properly evaluate the model and reduce overfitting.

Model Training:

The model is trained using:
- Optimizer: Adam
- Loss Function: categorical_crossentropy
- Evaluation Metric: accuracy

Model Export:

After training, the model is saved as:
model.hd5

Example Prediction:

from tensorflow.keras.models import load_model
import numpy as np
from PIL import Image

model = load_model("model.hd5")

img = Image.open("sample.jpg").resize((224,224))
img = np.array(img)/255.0
img = img.reshape(1,224,224,3)

prediction = model.predict(img)
print(prediction)

The output gives the probability for each of the six classes.

Future Improvements:

- Increase dataset size and variety
- Apply data augmentation to improve generalization
- Experiment with deeper ResNet architectures or other transfer learning models
- Optimize for mobile deployment and real-time inference

Integration:

This AI model can be integrated into:
- Mobile applications using TensorFlow Lite
- Smart recycling systems
- Web-based waste classification services
- Educational tools for environmental awareness

License:

This project is licensed under the MIT License.
