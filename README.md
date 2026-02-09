# 🧠 Neural Networks — From Basics to Stabilization (PyTorch)
A Teaching-Oriented Walkthrough of Neural Network Components and Training Dynamics

---

## 📌 Overview

Neural networks are often introduced as black-box models that “just work” once enough layers are added. In practice, however, successful training depends critically on **architectural choices, activation functions, normalization, optimization strategies, and regularization techniques**.

This repository presents a **progressive, experiment-driven demonstration of neural networks using PyTorch**, starting from a basic feedforward model and gradually introducing stabilization and improvement techniques commonly used in real-world deep learning systems.

Rather than focusing on benchmark performance, this project emphasizes **conceptual understanding**—explaining *why* each neural network component exists and *how* it affects learning behavior.

---

## 🎯 Objectives

- Build a neural network from first principles using PyTorch
- Understand the full training loop (forward pass, loss, backpropagation, optimization)
- Observe the effect of network depth on learning
- Study the role of Batch Normalization in stabilizing training
- Compare different activation functions and optimizers
- Demonstrate dropout as a regularization technique
- Perform inference on unseen data
- Extend neural networks from binary to multiclass classification

---

## 🧠 Key Learning Outcomes

✔ Understand how data preprocessing affects neural network training  
✔ Learn why normalization and scaling are critical for gradient-based learning  
✔ Observe how Batch Normalization improves convergence and stability  
✔ Compare activation functions beyond ReLU  
✔ Analyze optimizer behavior and convergence dynamics  
✔ Understand regularization through Dropout  
✔ Generalize neural networks from binary to multiclass problems  

---

## 📊 Experiments and Models Covered

### Binary Classification (Rain Prediction)
- Fully connected feedforward neural network
- Deep architecture with ReLU activations
- Binary classification using `BCEWithLogitsLoss`

### Stabilization and Optimization Techniques
- Batch Normalization vs no Batch Normalization
- Activation function comparison:
  - ReLU
  - Leaky ReLU
  - ELU
  - GELU
  - SELU
- Optimizer comparison:
  - Adam
  - SGD
  - SGD with momentum
  - AdamW
  - RMSprop

### Regularization
- Dropout-based neural networks
- Effect of dropout probability on training behavior

### Inference
- Prediction on manually constructed real-world data points
- Probability-based decision making

### Multiclass Classification
- Iris dataset (3-class classification)
- Softmax-based classification using `CrossEntropyLoss`

---

## 🧪 Datasets Used

### Weather Dataset (Binary Classification)
- Source: Kaggle (WeatherAUS dataset)
- Task: Predict `RainTomorrow` (Yes / No)
- Features:
  - Rainfall
  - Humidity at 3pm
  - Pressure at 9am
  - RainToday (binary categorical)

### Iris Dataset (Multiclass Classification)
- 150 samples
- 3 flower classes:
  - Setosa
  - Versicolor
  - Virginica
- 4 numerical features per sample

---

## 🏗️ Model Architecture (Representative)

### Binary Classification Network
- Input layer: 4 features
- Multiple hidden layers (deep MLP)
- Non-linear activations (ReLU / variants)
- Output layer: 1 neuron (sigmoid or logits)

### Multiclass Classification Network
- Input layer: 4 features
- Hidden layers: 2
- Output layer: 3 neurons (class logits)

The architectures are intentionally kept **simple and interpretable** to focus on learning dynamics rather than architectural novelty.

---

## 📈 Visualizations

The notebook includes:

- Training loss monitoring
- Timing analysis (CPU vs GPU)
- Neural network architecture visualization
- Comparative analysis across:
  - Normalization strategies
  - Activation functions
  - Optimizers
  - Regularization methods

These visual and numerical diagnostics reinforce *why* certain design choices lead to more stable and reliable learning.

---

## 🔍 Key Observations

- Neural networks are highly sensitive to feature scaling
- Depth alone does not guarantee good learning behavior
- Batch Normalization significantly stabilizes training
- Activation functions affect gradient flow and convergence
- Optimizer choice can change both speed and stability
- Dropout introduces robustness at the cost of slower convergence
- The same neural network principles extend naturally from binary to multiclass problems

---

## 📌 Conclusion

This project demonstrates that effective neural network training is not accidental—it is the result of carefully chosen architectural and optimization decisions. By incrementally introducing core components such as normalization, activation functions, optimizers, and regularization, this repository provides a clear and intuitive understanding of how modern neural networks are trained in practice.

The notebook is designed as a **teaching-first reference**, suitable for students, educators, and practitioners seeking a strong conceptual foundation in neural networks.

---

## 🛠️ Requirements

- Python 3.x  
- PyTorch  
- NumPy  
- Pandas  
- scikit-learn  
- Matplotlib  
- KaggleHub  
- Graphviz (for network visualization)

---

## 👨‍🏫 Author

**R. Ruthuraraj**  
Assistant Professor (Mechanical Engineering)  
Machine Learning | Deep Learning | Generative AI  

This repository is part of the **ruthuraraj-ml** organization and is intended for **educational and academic use**.

---

## 📜 License

This project is released under the **MIT License**.
