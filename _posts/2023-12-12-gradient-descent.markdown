---
layout: post
comments: true
title: "Gradient Descent"
excerpt: "an optimization technique for training machine learning models."
date:   2023-12-12 07:00:00
mathjax: false
---

A machine learning model is essentially a set of parameters that are computed on a given input data to produce an output.
Therefore, in order to improve model performance, we need to find the best set of parameters that effectively map the input-output pairs. One of the most well-known algorithms for achieving this is called **gradient descent**, commonly used for training neural networks.

The gradient descent algorithm is generally comprised of the following steps:

### 1. Forward Propagation
> **Goal**: Compute Loss

During forward propagation, the input data is passed through the network, and the model's predictions are generated. The loss function then calculates the discrepancy between these predictions and the actual output.
<!-- Hyperparameters: batch size, loss function, regularization -->

### 2. Backward Propagation
> **Goal**: Compute Gradients

In backward propagation, gradients of the loss function with respect to each parameter in the model are calculated. These gradients indicate the direction and magnitude of change required to minimize the loss.
<!-- Gradients are ... -->

### 3. Parameter Update
> **Goal**: Reduce Loss

Using the gradients computed in the previous step, the parameters of the model are adjusted to minimize the loss. This adjustment is typically performed by subtracting a fraction of the gradients from the current parameter values, scaled by a learning rate.

$$θ_{new} = θ_{old} - α ⋅ ∇L(θ_{old})$$

Where:
* $θ_{new}$ is the updated parameter vector.
* $θ_{old}$ is the current parameter vector.
* $α$ is the learning rate, determining the size of the step taken in the parameter space.
* $∇L(θ_{old})$ is the gradient vector of the loss function with respect to the current parameters.

<!-- Hyperparameters: optimizer, learning rate -->

We repeat these steps to minimize the loss. At a certain iteration, the loss may plateau, meaning that further adjustments do not significantly reduce the loss, indicating that the model has reached its optimal performance level.