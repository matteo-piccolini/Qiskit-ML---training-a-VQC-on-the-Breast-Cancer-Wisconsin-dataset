# Qiskit Machine Learning - Training a Variational Quantum Classifier (VQC) on the Breast Cancer Wisconsin Dataset

This notebook implements a complete **Quantum Machine Learning (QML)** pipeline to solve a binary classification problem using the *Breast Cancer Wisconsin (diagnostic)* dataset. 

## 🎯 Educational Purpose & "Toy Model"
This project is designed with a **didactic goal**. It serves as a **toy model** to demonstrate how classical data can be processed, reduced, and fed into a quantum variational algorithm. While the dataset is real and clinically relevant, the reduction of dimensionality via PCA and the use of a Variational Quantum Classifier (VQC) allow to probe the fundamental mechanics of hybrid quantum-classical optimization without the prohibitive computational complexity of large-scale systems.

---

## 🚀 Versatility & Modularity
The core strength of this notebook lies in its **highly modular structure**, which encourages experimentation across three main dimensions:

### 1. Multi-Backend Execution
The notebook is hardware-agnostic, allowing you to switch between different execution environments by simply modifying the `execution_mode` variable:
* **Statevector Simulator**: For ideal, noise-free theoretical validation and fast prototyping.
* **Noisy Simulator**: To study the impact of decoherence and gate errors using noise models derived from real IBM Quantum devices.
* **Real Quantum Hardware**: To execute the classification task on actual IBM Quantum processors via the Qiskit Runtime service.

### 2. Plug-and-Play Quantum Components
The architecture is built to be flexible, allowing for the easy replacement of fundamental quantum building blocks:
* **Feature Maps**: Seamlessly swap the `ZZFeatureMap` with other encoding schemes (e.g., `ZFeatureMap` or `PauliFeatureMap`) to test different data embedding strategies.
* **Ansatz Designs**: Experiment with various parameterized circuits (e.g., `EfficientSU2`, `RealAmplitudes`) to find the best balance between circuit depth and expressive power for this specific dataset.



### 3. Integrated Performance Benchmarking
A key feature of this notebook is the persistent **Results Aggregator**. Instead of overwriting data, the notebook collects results from every run (different simulators, different circuit parameters, etc.) into a centralized dictionary. This enables:
* **Cross-Backend Analysis**: Compare accuracy and training time between simulators and real hardware.
* **Quantum vs. Classical**: Evaluate the quantum model's performance against a classical baseline (SVM) stored in the same results table.

---

## 🧬 Methodology in a Nutshell

1.  **Dimensionality Reduction**: Classical preprocessing using **PCA** to compress 30 features into 3 principal components, ensuring compatibility with the qubit counts of current NISQ devices.
2.  **Quantum Encoding**: Mapping the reduced classical vectors into the high-dimensional Hilbert space of the quantum system.
3.  **Variational Training**: Leveraging the **COBYLA** optimizer to iteratively tune the quantum gates and minimize the cross-entropy loss function.
4.  **Real-time Monitoring**: A custom callback function captures the objective function value during training, providing a live visualization of the optimization process.



---

## 🛠️ How to Experiment
1.  **Select Backend**: Set the `execution_mode` in the configuration cell.
2.  **Customize the Circuit**: Modify `reps`, `entanglement`, or the `maxiter` of the optimizer to see how they impact the final accuracy.
3.  **Run & Compare**: Execute the full pipeline and refer to the final `results` summary to see a side-by-side comparison of all your experimental configurations.

---
