https://colab.research.google.com/drive/1URk9Z9YLTkFMhQ766WAL1l7631C-xAOG#scrollTo=qnY2JDA47Fwv The notebook I made testing curve fitting on Keras Neural networks 

https://colab.research.google.com/drive/1zWXyOf4C9ZVhjFjG8Kh7Xke72z1BT5pU#scrollTo=n8-zUOv25aAd My cleaner notebook on the same, for the simpler function
### Gotcha moments:
- We will get faster results on using tensors start to end (tf.square, tf.sin, tf.reduce_mean) but the tensor objects interfere with the normalization objects so atleast traditional Keras layers can't be created.
- sometimes errors between pred and labels because theyre of different input output shapes, so y_pred.squeeze() can fix them. 
- Mention input_dim 1 less than n_dim in the first Keras layer.
- If you use tensors start to end, use tf.linspace to generate the x values, then np.arrays don't really interfere.
- Regularization works well on smaller datasets, but on larger datasets the loss skyrockets since it removes complexity.
- https://colab.research.google.com/github/mrdbourke/tensorflow-deep-learning/blob/main/01_neural_network_regression_in_tensorflow.ipynb#scrollTo=Fug5_B6Ab7Ah The notebook I used with more or less my features


# Asokan tidbits
- https://www.wired.com/2014/01/geoffrey-hinton-deep-learning/ one of the pioneers of DL