# Quantum-Machine-Learning

This project demonstrates how to use a **quantum-classical hybrid model** to classify images from the MNIST dataset using the **PennyLane** library. It leverages the potential of quantum circuits for feature extraction and combines them with classical layers for classification.

---

## Overview

### Key Components
1. **Quantum Circuit:**
   - Uses `AngleEmbedding` to encode image data into quantum states.
   - Employs variational quantum layers (`StronglyEntanglingLayers`) with trainable parameters to extract features.

2. **Classical Layer:**
   - Processes quantum features to perform final classification.

3. **Hybrid Approach:**
   - Combines quantum computation's high-dimensional feature space with classical computation's versatility.

---

## Steps

### 1. Preprocessing MNIST Data
- **Dataset:**
  - MNIST dataset is filtered to include only two classes (`0` and `1`).
  - Images are normalized and reduced in size using **PCA** to fit within the limitations of quantum circuits.

- **Reason for Dimensionality Reduction:**
  - Quantum simulators and hardware have a limited number of qubits. PCA reduces the 784-pixel input to an 8-dimensional feature space.

### 2. Quantum Circuit
- The quantum circuit:
  1. Encodes the reduced feature vector into qubit states using `AngleEmbedding`.
  2. Applies `StronglyEntanglingLayers` to transform these states.
  3. Outputs a measurement value to predict the class.

### 3. Training the Model
- The circuit parameters are trained using a **gradient descent optimizer** to minimize the **mean squared error** (MSE) between predicted and actual labels.

### 4. Evaluation
- The model is evaluated on the test dataset, and its accuracy is calculated.