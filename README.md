# 🧠 Sound Mixed Fixed-Point Quantization of Neural Networks
*CS637: Embedded and Cyberphysical Systems Course Project*  
*👤 Abhijit Dalai, Abhishek Kumar, Aryan Singh, Ayush Srivastava*

## ✨ Overview
This project explores **sound mixed fixed-point quantization of neural networks** for safe, efficient deployment in embedded and cyber-physical systems. Our work adapts the EMSOFT 2023 approach using open-source tools and demonstrates it on a real neural network controller.

## 🎯 Motivation
Neural network controllers in embedded systems (like drones and medical devices) must balance **accuracy, speed, and hardware constraints**. Floating-point arithmetic is often too heavy for such platforms.  
**Mixed-precision fixed-point quantization** can drastically reduce memory and power requirements, but must be done carefully to avoid unsafe errors.

## ❓ Problem Statement
- How can we **automate the assignment of fixed-point precisions** across a neural network to minimize resource usage while guaranteeing output errors remain within safe bounds?
- Can we do this efficiently for real-world, safety-critical applications?

## 🛠️ Approach
- **Mixed-Precision Quantization:** Assigns different fixed-point precisions to different network layers/operations.
- **MILP Formulation:** The quantization problem is encoded as a Mixed Integer Linear Programming (MILP) problem, solved with [Pyomo](http://www.pyomo.org/) and the CBC solver.
- **Dataset:** We use weights from a pre-trained neural network (single pendulum simulation).
- **Implementation:**  
  - The MILP model minimizes total fractional bit-widths while keeping quantization error below a user-specified bound.
  - Quantized weights are then used in a C++ neural network implementation.

## 📁 Repository Structure
- `CS637_final_final.pdf` # Project report and slides
- `QuantizedNeuralNetwork (2).cpp` # C++ implementation of quantized NN
- `SinglePendulumNN (1).scala` # Scala reference implementation
- `pyomo (1).ipynb` # Pyomo implementation code

## 📊 Key Results
- **Memory Reduction:** Significant memory savings by using lower bit-widths for less sensitive layers.
- **Accuracy:** Mean Absolute Error (MAE) between original and quantized weights: **0.0321** (minor deviation).
- **Performance:** Minimal change in model predictions, confirming the effectiveness of the approach.

## 🚀 How to Run
1. **Solve the MILP for optimal fractional bits** (Python with Pyomo and CBC).
2. **Quantize the neural network weights** using the optimized bit-widths.
3. **Compile and run the C++ implementation** (`QuantizedNeuralNetwork-2.cpp`) with the quantized weights.

*Note: The original Aster tool could not be run due to software version issues; we implemented the MILP approach independently using Pyomo.*

## 🏭 Applications
- **Automotive:** Adaptive cruise control, collision avoidance
- **Aerospace:** UAV and aircraft collision avoidance, flight control
- **Healthcare:** Wearable and implantable medical devices
- **Industrial:** Robotics, predictive maintenance
- **Energy:** Smart grid control, environmental sensors
  
