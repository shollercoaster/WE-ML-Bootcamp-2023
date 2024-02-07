- Assumption of ML: only my data must be sufficient to represent reality
# Neural Networks
- No different than a linear classifier
- Gets a lot of inputs, calculates wixi + b 
- 4 neurons in 1 layer, each getting 4 inputs, so this layer i can have 4 * (4 + 1) = 20 (extra bias) parameters to play with
- they'll give 4 outputs, if they go to one neuron, then another 5 parameters to play with
- ML is essentially curve fitting (how to best fit inputs to outputs)
- so straight line (2 parameters) gives me no bend 
- But polynomial function assumptions restricts us to more diverse functions that might fit better
- Solution: Piecewise functions (divide function into regions for more independent control)
- If at points of connection of different pieces, the values of function and 1st 2nd derivatives are equal, then its called a cubic spline.
- We introduce non linearity because otherwise all weights can be collapsed into 1 matrix (1 layer), so essentially we can only meddle 1 parameter.
- So non linearity = activation function added. So instead of wixi, we're applying activation functions to it.
- Neural networks = ultimate ensemble (each linear classifier connected in a new manner)
- Neural networks = ultimate approximators in curve fitting

### CNNs
- features of images are local
- Treat the image as a whole, and get the important features
- 

## Decision Trees
- Creating model = coming up with data to collect to find out who will get in a big company: For college: not the name, yet some ranking/number that will determine its effect
- The success of the model depends on if statements
- DT algo decides threshold for importance of a feature, and the order of those if statements
- How many should be selected from the whole population: "The data should reflect reality."
- The advantage: can get a trace of explanation about why a certain prediction was made, can't get this in NNs
- Disadvantage: very prone to overfitting (will get an answer somehow)
- computationally expensive for training, but easier to run
- Good for categorical data 
- Pruning (removing a subtree or reducing depth) and other techniques to help overfitting
- Random Forest = each tree selects random subset of all features (only once, not random every time)


## Resource: How to create NNs from scratch in python
https://towardsdatascience.com/math-neural-network-from-scratch-in-python-d6da9f29ce65
Layers by layer work:
1. We feed **input** data into the neural network.
2. The data flows **from layer to layer** until we have the **output**.
3. Once we have the output, we can calculate the **error** which is a **scalar**.
4. Finally we can adjust a given parameter (weight or bias) by subtracting the **derivative** of the error with respect to the parameter itself.
5. We iterate through that process.

# My ZiroTutor Notes
- The point of applying convolutions through filters in CNNs is to reduce dimensionality of input by downsampling and extracting the important features from the input and capturing important patterns. 
- CNNs also do:
	- Parameter sharing: same weights are applied to different part of the input, this makes learning easier and makes them robust to invariance of data in features
	- More local relationships capturing than global relationships
- Fully connected layer = all neurons in 1 layer connected to all neurons in the next 


# Counting and set theory session
- "One, two, three infinity" - Gamow
- [[WE Bootcamp 2022 Counting Lecture]]

# How to Read a Research Paper
by Dr Anoop IIITH
- "I researched about something" - searching and learning != actual research
- Research = start with not knowing things + KNOW that you don't know about it + KNOW that its knowable/solvable
- Try to extend the boundary of knowledge (by seeing an angle to solve a problem that is _just_ outside the problems we can solve currently)
- Can't want to solve a problem just because its "nice", it needs to be appropriately solvable, need to know adequate prior knowledge
- "I hate this subject" - you don't know it well enough
- Things are going to change very fast, faster than they have been till now, don't stay fixated on a subject. Accept change.
- A researcher is a _creative_ problem solver.
- "People are solving such difficult problems" They just figured out the prerequisite knowledge, and are going other way around to solve one tiny problem outside the boundary of knowledge
		Storytelling is very important in Research.
- They also don't know every single detail of what they talk about.
- Just keep reading and getting rough ideas. Its okay to not know.

### Stages of reading a RP
1. Finish reading in 5 mins: Headings, abstract, some pictures, some conclusions
2. Next time in 0.5 hour, next time in an hour, and you increase time the more you read it
3. You don't need to know everything, you read most papers in just 5 minutes.

The light component separation paper he mentioned: https://www.cs.cmu.edu/afs/cs/academic/class/15462-s12/www/lec_slides/Krishnan_TOG06.pdf

- Different ways of consuming papers now: reading, watching vids, elctures, discussions
- Whatever you feel excited about, cause doesn't matter if you know things or don't know them
- Be comfortable with learning from tough words, at higher levels of abstraction
- Change is good for researchers, cause we always ask "what next?"
- A lot of times people solve the same problem parallelly, Newton and Leibnitz discovered calculus parallelly.
- Don't get overwhelmed reading papers - start with the premise that you won't understand it.
- Be comfortable with working in layers of abstraction.
- Make a beginner assumption in the 5 minute read and read the paper to re-validate the assumption.
- Maybe apply the last 3 points to technical articles/concepts outside of research papers too.