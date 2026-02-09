# 🧠 Neural Networks — From Basics to Stabilization  
### An Empirical Study of Training Dynamics, Normalization, and Regularization Using PyTorch

---

## Abstract

Neural networks are powerful function approximators, but their effectiveness depends critically on architectural design, data preprocessing, and training strategy. This report presents a structured, experiment-driven study of neural networks implemented using PyTorch, focusing on how different components—such as depth, activation functions, Batch Normalization, optimizers, and dropout—affect learning behavior. Using a real-world weather dataset for binary classification and the Iris dataset for multiclass classification, the report demonstrates how neural networks evolve from basic feedforward models to stabilized and regularized systems suitable for practical use.

---

## 1. Introduction

Neural networks are often introduced as end-to-end models without sufficient emphasis on *why* specific components are required. In practice, poor architectural or optimization choices can lead to unstable training, slow convergence, or poor generalization.

This work adopts a **progressive learning approach**, beginning with a baseline deep neural network and incrementally introducing stabilization and improvement techniques. Rather than optimizing for benchmark performance, the focus is on **understanding training dynamics and representation learning**.

---

## 2. Dataset Description and Preprocessing

### 2.1 Weather Dataset (Binary Classification)

The primary dataset used in this study is the WeatherAUS dataset, sourced from Kaggle. The task is to predict whether it will rain the next day (`RainTomorrow`) based on a small subset of meteorological features.

**Features used:**
- Rainfall  
- Humidity at 3pm  
- Pressure at 9am  
- RainToday (binary categorical feature)

The target variable `RainTomorrow` is encoded as a binary label.

### 2.2 Preprocessing Steps

- Categorical variables are converted to binary numeric form
- Rows containing missing values are removed
- Numerical features are standardized using `StandardScaler`
- Train–test split is performed with stratification to preserve class balance
- Data is converted to PyTorch tensors and loaded using `DataLoader`

This preprocessing pipeline ensures stable gradient-based learning and prevents data leakage.

---

## 3. Baseline Neural Network (Without Batch Normalization)

### 3.1 Architecture

The baseline model is a deep fully connected neural network consisting of multiple hidden layers with ReLU activations. The network outputs raw logits and is trained using `BCEWithLogitsLoss` for numerical stability.

### 3.2 Training Procedure

- Optimization: Adam optimizer
- Loss function: Binary cross-entropy with logits
- Training performed over multiple epochs
- Loss monitored per epoch
- GPU synchronization used for accurate timing

### 3.3 Observations

- The model is capable of learning the task
- Training is sensitive to initialization and learning rate
- Deeper architectures do not automatically guarantee stability

This baseline establishes a reference point for later improvements.

---

## 4. Effect of Batch Normalization

### 4.1 Motivation

Batch Normalization is introduced to reduce internal covariate shift and stabilize gradient flow during training.

### 4.2 Implementation

Batch Normalization layers are inserted after each linear transformation and before the activation function. Weight decay is added to the optimizer for additional regularization.

### 4.3 Observations

- Faster and smoother convergence
- Reduced sensitivity to initialization
- Improved training stability
- More consistent loss behavior across epochs

Batch Normalization proves to be one of the most impactful stabilizing techniques in the study.

---

## 5. Activation Function Analysis

### 5.1 Motivation

Activation functions control non-linearity and gradient propagation. Different functions can significantly affect learning dynamics.

### 5.2 Activations Explored

- ReLU  
- Leaky ReLU  
- ELU  
- GELU  
- SELU  

Each activation is tested within the same network architecture to isolate its effect.

### 5.3 Observations

- ReLU remains a strong and stable default
- GELU and SELU show smoother gradients in deeper layers
- Certain activations require careful initialization and scaling

This section demonstrates that activation choice is a meaningful design decision, not a cosmetic one.

---

## 6. Optimizer Comparison

### 6.1 Optimizers Evaluated

- Adam  
- SGD  
- SGD with momentum  
- AdamW  
- RMSprop  

### 6.2 Observations

- Adaptive optimizers (Adam, AdamW) converge faster
- SGD variants can be more stable but slower
- Optimizer choice affects both speed and loss smoothness

The experiment highlights the interaction between architecture and optimization strategy.

---

## 7. Dropout Regularization

### 7.1 Motivation

Dropout is introduced as a regularization technique to reduce overfitting by randomly deactivating neurons during training.

### 7.2 Observations

- Training loss increases slightly due to noise
- Generalization improves on unseen data
- Excessive dropout can slow convergence

Dropout demonstrates the trade-off between robustness and training efficiency.

---

## 8. Inference on New Data

The trained models are used to perform predictions on manually constructed input samples. This section demonstrates the full inference pipeline:

- Feature scaling using the trained scaler
- Tensor conversion
- Probability estimation
- Threshold-based decision making

This step bridges model training and real-world deployment scenarios.

---

## 9. Extension to Multiclass Classification (Iris Dataset)

### 9.1 Dataset

The Iris dataset is used to extend the neural network framework to multiclass classification involving three flower species.

### 9.2 Model and Training

- Output layer produces class logits
- Loss function: `CrossEntropyLoss`
- Predictions obtained using `argmax`

### 9.3 Observations

- The same neural network principles apply seamlessly
- Only the loss function and output interpretation change
- Demonstrates generality of the neural network framework

---

## 10. Key Insights and Discussion

- Neural networks are highly sensitive to feature scaling
- Architectural depth must be paired with stabilization techniques
- Batch Normalization significantly improves training behavior
- Activation functions influence gradient flow
- Optimizer choice affects convergence speed and stability
- Regularization is essential for generalization
- The same framework supports both binary and multiclass tasks

---

## 11. Conclusion

This study demonstrates that effective neural network training is the result of informed design choices rather than architectural complexity alone. By incrementally introducing normalization, activation strategies, optimization techniques, and regularization, the report provides a clear and practical understanding of how modern neural networks are trained in practice.

The accompanying notebook serves as a **teaching-first reference**, offering learners a transparent view of neural network behavior from basic models to stabilized systems.

---

## Author

**R. Ruthuraraj**  
Assistant Professor (Mechanical Engineering)  
Machine Learning | Deep Learning | Generative AI  

This report accompanies the notebook  
`Neural_Networks_Demo_From_Basics.ipynb`  
and is part of the **ruthuraraj-ml** organization.

---

## License

This project is released under the **MIT License** and is intended for educational and academic use.
