# Supervised Learning
- Process of training the model based on information deduced from the error function of the previous iteration to modify parameters
- Data = numbers, model = complicated mathematical equations
## How to use the feedback after every iteration
- Feedback = cost function E(m, c) = y1 - y' = mx1 + c - y'
- Our aim = minimize the cost function
- Its a minimization / optimization problem
- Gradient descent = 1 technique to solve this (moving towards the depth of valley formed by E, m, c by finding the derivative for steepest descent)
- computing gradients after each datapoint (stochastic GD) , after all (batch gradient descent), or after a subset of datapoints (mini-batch GD)
- epoch = going through the batch training one time

## Gradient Descent

Requirements for a function to be able to do GD:
- differentiable
- needs to be convex (has a global minima) (second derivative >= 0)

Gradient descent is an optimization algorithm used to find the minimum value of a function, without knowing the function but by only moving in the direction of the steepest ascent of the derivative at that point. 
```
∇f(x) = [∂f(x₁)/∂x₁, ∂f(x₂)/∂x₂, ..., ∂f(xₙ)/∂xₙ]
```
Iteratively, 
```
x_n+1 = x_n - α * ∇f(x_n)
```
where  ```α``` is the learning rate, positive constant controlling value of step size, x_n and x_n+1 are current and updated values. In early stages we take huge learning rates, then reduce or stick to a constant (0.1)

After each iteration we step in the opposite direction of gradient.

![[Pasted image 20231220102749.png]]

Hyperparameter = a parameter that isn't derived from the data and we can't influence it

## Bias and Variance
- Bias (impartiality): 
	- systematic error of model, diff between average prediction and true underlying value
	- an ML system with bias is going to make a consistent error
	- means youre prolly missing a feature, not taking something into account
	- a more complex model is needed
- Variance: 
	- measures sensitivity of model to specific data
	- errors are all over the place
	- model is too complex and easily influenced by features, there is a need to simplify the model
- need to find optimal point
- Solutions:
		- Ensemble: combine predictions from different algorithms, and all those classifiers decrease variance and find bias 
		- example: Random Forest
		- Different Ensembling techniques: use all datapoints but not features, or change some other technique (sampling technique) in different iterations, or randomly choose a few datapoints (not disjointly)
		- this is how its different from different splitting/cross validation techniques (cause similar model used for diff iterations, not the same or a model from scratch)
Summary:
		- Ensembles focus on creating diversity among models to enhance overall prediction.
		- Splitting/cross-validation focus on evaluating a single model's performance on different data splits.

TIMELINE AND SUCCESS THRESHOLDS
timeline: assign 2-3 days for every stage of the project, 3-4 days for the Stanford course
success = 1 if we complete KG creation, visualization and application of 2-3 GNNs 
success < 1 for KG creation + visualization + 1 GNN application
success > 1 various applications with code and proper documentation for all 3 stages, while accomplishing 2-3 tasks with the dataset

## Fibonacci Sequence
f(n) = f(n-1) + f(n+1)
1 1 2 3 5 8 13 21 34 55 89
f(n+1)/f(n) = golden ratio 
miles to km, 13 miles is approx 21 km, and ulta ke liye check 
GR = 1 + 1/GR (golden ratio)
used to divide the rectangle into a square and another golden rectangle

### 7 * 11 * 13 = 1001 
figure out the ulterior motive happening, get the same number by dividing by 1001 if multiplied beforehand

### Examine your assumptions while doing any task
7 _ 7 _ 7 = 5 
ans = 747 / 7

- pin the tail to the donkey (who asked you to put the blindfold on?)

### How many blindfolds do you put on?

## Abstraction: Power of Math
- We hated math cause we couldn't see it
- Finding patterns 

## You're in the top 2% of the country. Don't think of yourself as unprivileged, middle class or anything.
You have primary education in an institute of your choice. So you are privileged. Don't blame the education system.
# To Read
- "The Unreasonable Effectiveness of Mathematics in the Natural Sciences" is a 1960 _article_ by the physicist _Eugene Wigner_
- Asokan told to check GPT4All for the project