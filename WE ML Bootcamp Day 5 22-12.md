# KNNs, SVMs, Overfitting

### ChatGPT + Chandra slides + Asokan:
#### SVMs:
- have 2 main optimal parameters:
	- C(regularization parameter): small c = simple decision boundary but some misclassification, large c = complex but correctly classified. tradeoff between complexity of decision boundary and point misclassification.
	- Kernel and its parameters: Kernel is a math function that takes 2 datapoints and computes the similarity score between them. Different types: linear, polynomial, gaussian, sigmoid, etc
- The training of a Support Vector Machine involves solving a quadratic optimization problem to find the optimal hyperplane. 
- $$minw,b ​21​∥w∥2+C∑i=1n​ξi​$$
- smaller c and simpler kernel avoids overfitting, other params w, b are changed and solved using quadratic programming and lagrange multipliers
- not good to use a complex line as hyperplane because overfitting
- SVM tries to _MAXIMISE THE MARGIN_ (difference between the classes)
- we use a broad margin to accomodate for newer datapoints and try to have them predicted correctly.
- good at generalization
- convex optimization on its own, so we don't to worry about local minima.
- HYPERPLANE: a linear surface in higher (more than 3) dimensions.
- Intuition tells us that decision boundary should be equidistant from both classes.
### Non Linear SVMs
- intuition: we transform them to a higher dimension space 
- say theres a circle of dots surrounded by crosses, increase the dimension and apply a transformation to raise the dots to a higher position in 1 dimension, now the 2 classes become linearly separable 
- we go to a dimension where a circle is a line
- technically:  go to 3d, for dots have z = 1, for crosses have z = -1
- Kernel transformations = coordinate transformations
- Not just linear transformation, consult all standard Txs and see whichever works. There is no visual intuition for higher dimensions. So trial and error.


#### KNNs (K nearest: both classification and regression)
- lazy learner: doesn't find the underlying model, just memorizes points in the beginning and classifies class or predicts (based on average of k nearest points).
- instance-based algorithm
- How to choose k: 
	- Usually odd ks are taken to avoid ties in voting (3,5) or do cross validation with each k, pick the k with highest performance metric, or we do the elbow method
	- the larger the k, we're looking at more aggregate based data, we're loosing out on individual info, this is called _SMOOTHING_.
	- A larger k reduces variance (potential for overfitting) but may increase bias. A smaller k reduces bias but may increase variance.
- needs all storing samples at test time, computationally intensive
- outliers (a red among all greens and doesn't have red in top k nearest) affect the prediction 
- Different distance functions: euclidean, minkowski, hamming
##### How scaling affects KNN:
- Scaling (making all features have similar scales) increases accuracy
- otherwise features with higher values will influence prediction more 

##### New insights on KNNs
- Can create a lattice around a certain point if k = 1
- When we increase k, the size and shape of lattice gets affected by a lot of points
- This is meant by smoothening, so we get aggregate behaviour instead of neighbourhood
- Known as _VORONOI DIAGRAMS_: Voronoi diagram, also called a Voronoi tessellation or a Thiessen polygon, is a geometric partitioning of a plane into regions based on the distance to a specified set of points in that plane.

### Asokan Notes:
- FOURIER TRANSFORM: we convert the function into a different domain using trigonometric functions
	- We essentially convert them to their power series expansions
	- Prolly no applications in math because of aperiodicity in ML data

### Outliers
- data between 1 sigma: 65%
- data between 2 sigma (Standard deviation): 95%
- data more than 3 sigmas away is an outlier, and possibly incorrect.
- [[relative probabilities in a normal distribution.canvas|relative probabilities in a normal distribution]]
- In ML, a point that is not in the nearest neighbours of all its nearest neighbors.
- KNN helps find outliers, just calculate the distances and apply above method.
- **KNN is not an ML algorithm.** Because there is no training, it just knows where to find the answers for new datapoints.
- KNN is computationally and memory intensive.
- Can make some approximations to make computation easy:
	- 3 points make a small cluster, if you calculate distance from one you don't need to do it for others
	- Instead of k nearest neighbours, we take a radius and find all points in that vicinity

## Performance Metrics
- Check out the beginning of NLP lectures for most notes
- the malaria "doesn't have" saying model is harmful because it is important to know how expensive a mistake can be in the wrong scenario.
- ##### Confusion Matrix 
	- (False positive is falsely positive bola, it was bad i called it good)
	- Can make confusion matrix for more than 2 classes (diagonal should be larger for good models cause those are the true positive values)
	- also important to know when you misclassify something: "what did i confuse it with?" which is why other diagonals of CM important.
- Precision = how many of the positives i declared were actually positive?
- recall = how many of the positives that existed could i actually declare?
- ROC (receiver operating characteristic curve):
	- false positive rate (x) vs true positive rate (y)
	- AUC gives overall performance of model