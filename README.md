# AML_2019_Group5 Coursework, Part 1
Experiments with different Gradient Descent methods for two varible function
---

## Introduction
The project tested three different gradient descent methods on the same loss function. We have experimented with different step sizes to compare the speed of convergence and also assess the ability of finding global minimum between three methods. 

## Basic Background of Gradient Descent
Why is gradient descent important in machine learning?

In each Machine Learning model has a specific cost function. When we are training the model, we are aiming to find the coefficients that can minimise the cost function. Gradient descent is an optimization algorithm used to minimize the function by iteratively update the parameter of the model. It is the most common optimization procedure that can be applied to many machine learning algorithms.

How does plain vanilla gradient descent work?

The plain vanilla gradient descent starts with initial value of the coefficients for the cost function. Then calculating the cost of the function by plugging them into the function. Next step is to calculate the gradient at the point so that we can determine the moving direction of the coefficients to get a lower cost on the next iteration. From the derivative, we know which direction is downhill. Then we specify a learning rate that controls the updating speed for the coefficients. The process is repeated to update coefficients until the cost of function is zero or close enough to zero.

Two modications to plain vanilla gradient descent.

There are some conditions that make plain vanilla gradient descent very slow since the update rule of the algorithm that only depends on the gradients at each iteration only. Momentum method is a technique can be used to mitigate these problems, which can accelerate gradient descent by taking accounts of previous gradients in the update rule at each iteration. Another method that is closely related to Momentum method is Nesterov Accelerated Gradient. The difference between Momentum method and Nesterov Accelerated Gradient is in gradient computation phase. In Nesterov Accelerated Gradient, we apply the velocity  to the parameters to compute interim parameters. We then compute the gradient using the interim parameters We can view Nesterov Accelerated Gradients as the correction factor for Momentum method.

## Experiments
Some crucial parameters defined in the code with explanations.

| Parameter      | Explanation |
|----------------|-------------|
|`x_init`             | an initial guess for the value of x that minimises the function|
|`y_init`             | an initial guess for the value of y that minimises the function|
|`n_iter`             | the maximum number of iterations|
|`eta`                | the step size           |
|`tol`                | when the gradient is "tol" away from zero, iterations will stop |
|`loss_fn_min`        | the minimum value of the loss function that has been found     |
|`x_at_min`           | the value of x which gives the minimum value     |
|`y_at_min`           | the value of y which gives the minimum value    |

## Conclusion
