# AML_2019_Group5 Coursework, Part 1
Experiments with different Gradient Descent methods for two varible function
---

## Introduction
The project tested three different gradient descent methods on the same loss function. The chosen loss funtion is THREE-HUMP CAMEL FUNCTION, which has three local minima and a global minimum at [0,0]. We have experimented with different step sizes to compare the speed of convergence and also assess the ability of finding global minimum between three methods. The gradient descent path for three methods are plotted in the code. The following graph is the loss function surface plot and its key characteristics.
<p align="left">
  <img width="400" height="300" src="https://github.com/BigLightMing/AML_2019_Group5/blob/master/images/Loss%20Function%20Surface.png"/400/300>
  <img width="400" height="300" src="https://github.com/BigLightMing/AML_2019_Group5/blob/master/images/Key%20characteristic.png"/400/300>
</p>

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
|`alpha`              | representing how much we take part previous gradient    |

The table below summrized the results of plain vanilla gradient descent with different step sizes.

| Initial Point |Step Size (eta) | No. of Iterations | Minimum Loss |  Minimum values(x,y)  |
| --- | ---| ---| --- | --- |
| [1,1]      |eta=0.001       |        9712         |   3.67217076e-15 |[-2.604316e-08, 6.287376e-08]    |
| [1,1]      |eta=0.002       |        4852         |   3.65178857e-15 |[-2.597079e-08, 6.269903e-08]    |
| [1,1]      |eta=0.003       |        3232         |   3.63130844e-15 |[-2.589786e-08, 6.252296e-08]    |

**Comments:** Regarding to the plain vanilla gradient descent, we have experimented different learning rates from 0.001 to 0.003. With increasing the step size, the number of steps to convergence decreasing. With the same initial point, we have also experimented using Momentum and Nesterov's Accelerated Gradient(NAG), which required an extra prameter alpha representing how much we take part previous gradients. In our project, we choose alpha=0.9. The results are summarized below.

| Gradient Type | Step Size (eta) | No. of Iterations | Minimum Loss |  Minimum values(x,y)  |
| ---| ---| --- | --- | --- | 
| Plain Vanilla | 0.001 | 9712 | 3.67217076e-15 | [-2.604316e-08, 6.287376e-08] |
| Momentum      | 0.001 | 741  | 3.41963907e-15 | [2.5131733e-08, 6.067337e-08] |
| NAG           | 0.001 | 774  | 3.88242297e-15 | [-2.708541e-08, 6.451906e-08] |

**Comments:** For the same learning rate, the number of steps to convergence decreases considerablely after we switched to momentum method and Nesterov's Accelarated Gradient.
