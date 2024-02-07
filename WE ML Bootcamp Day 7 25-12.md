# Word2vec
- Word2vec is a numeric representation of words. It is the starting point for all the LLMs like ChatGPT since it got superceded by BERT.
- Bag of words = orderless and could contain duplicates (a data structure more primitive than a set).
- We create a masterlist of words in a document to create a reference order for words.
- Then we create a number representing relative frequencies of those words in the document.
- Term Frequency looks at what words characterize a document (but 'the' could also be the most frequent in most docs), but Inverse Doc Frequency (IDF) looks at what words **distinguish** a document.
- Multiplying TF by IDF gives only the most important words in each vocabulary.
### How to Represent each word?
- A word is a document with just that word
- One-hot representation
	- Useful for representing colors and other categorical variables (Is present/absent)
	- All words represented as unit vectors (the single 1) in the space.
	- Now distance between any 2 words = root 2.
	- So no semantic relationship captured. ('one' 'two' at the same distance as 'one' 'mango').
	- Also different words can mean the same one, no way to represent this either.
- Idea behind word2vec = Words closer in meaning will be close to each other or lie on the dimension representing that meaning.

### Word2vec
- What we want to do with word2vec: man - woman + queen = king
- "Marco saw a furry little wampikmuk hiding in the tree." meaning of a word is hidden in the words surrounding it.
- Similarity of words in representation has nothing to do with meaning, but with lexical context.
- (Achieved by a proxytask) We wish to learn a representation such that:
	- x3 = f(W, x1, x2, x4, x5)
	- W = learnable paramaters/weight matrix
	- xi = R(ai)
	- ai is the ith word, xi is its representation
- Intermediate relationship of words is captured by classifier, since we classify relationship of x3 based on surrounding words, knowing ONLY their representations and the order in which they occur in a sentence in the document.
- We want representation of middle word to be sum of representations of left and right words.
	- R(a3) = F(R(a1), R(a2), R(a4), R(a5))
- We want [ Nx1 ] (dense, semantic representation) = [ NxV ] (learned weights) . [ Vx1 ] (one-hot sparse) at the end of **_training_** (the process of predicting the middle word correctly for a fixed N (size of representation we choose) for a training but a fixed V (vocab) overall).
- No labelling was required, we get equidistant equimeaninged words only by training from the corpus.
- Word similarity = vector similarity
- https://projector.tensorflow.org/ even on dimensionality reduction, the points of similar meaning words (days of the week) are way closer.
- https://github.com/MaxwellRebo/awesome-2vec node2vec, or similar 2vec models inspired by word2vec
**- Imp: vector size in word2vec is 300 (dimensions)**
- https://arxiv.org/pdf/1610.08229.pdf a paper highlighting word2vec for sentence classification tasks
#### Glove by Stanford
- https://nlp.stanford.edu/projects/glove/ focused on how frequently words co-occur with each other
- Trained just on wikipedia corpus
- easier to see through heatmap (color-coded visualization)

#### Bert by Google
- Checked the word relation representation in the backward direction too, so we got 2 datapoints
- Checks both left and right contexts
- LLMs are nothing but evolutions of word2vec
- ChatGPT analyzes statistical probabilities of words and sentences to generate legal combinations of words that can occur together.
 
## From the tensorflow documentation
- Embedding = each word gets assigned a dense vector w each dimension representing semantic features, the closer the words in meaning, the closer they are in the "embedding space"
- optimizer to learn word embeddings from large datasets
- 2 representations of words:
	- Continuous Bag of words: predicts middle word on basis of neighbouring
	- Skip-gram model: predicts words in n-range before and after current word (predicts neighbours given the certain word)

### Skip-gram model
- Training objective = maximize prob of predicting context-words(before and after, defined by window-size n) given target word (current).
- ![word2vec_skipgram_objective](https://tensorflow.org/text/tutorials/images/word2vec_skipgram_objective.png)
- c = window size
- We compute a **Softmax** over the entire word vocabulary to convert their frequency scores into probabilities of being context word to the given target word.
- Negative samples: generating context words unlikely to be in the same context as target-word 
	- Then minimize their probability and maximise positive sample (actual context word) during training. 

## Mahabharata word2vec Demo
https://colab.research.google.com/drive/1I9biKb8QOFzlXxXgcwt0_HGfCnuhzhNw?usp=sharing#scrollTo=_-v2yVWouGM2

There was a drastic reduction from 893918 words to 1650 after removing stopwords, duplicate occurrences as well as stemming the words to remove suffixes and representing them in their primitive form. On training word2vec, embedding vectors with 100 dimensions (default vector_size, unless defined otherwise), generated for 1650 unique primitive words in the vocabulary. PCA implementation in scikit-learn can be used to reduce the dimensions to 2. In the end, from the list of similar words for the specified character we can see that the different names for a character have come together (eg. Krishna and Arjuna). People sharing relationships have also come together in the word vector representations. We can also see that characters sharing scenes together have similar list of similar words (eg. Nakula and Sahadeva), the words that have been in a sentence frequently also share a similarity. We lose specificity and get aggregate results if we try to extract top 10 relations out of mere 1650 words in the document.

We lose specificity and get aggregate results if we try to extract top 10 relations out of mere 1650 words in the document. (The KNN document)

Draupadi had most conversations with Bheema but the model couldn’t capture their relationship due to lesser data.

**![](https://lh7-us.googleusercontent.com/UaantCf2ZNEB9QNJ0Es83fzM_CZv25KOsbb7juUG4BPE2Hummfzg8J50N2PoBLkOkXp-jSv8R1U8jQYMAQqY9O0LSbiHQxYy5_uTO-hJC_Txtxvmt71lzZm2dSQrXTIAlZbXLyIF4ew7T0DRzpkgYqg)


# Neural Network Training and CNNs
- Dividing the datapoints into batches of 1000, running them once is 1 epoch, typically 1000 epochs are run.
- ![[Pasted image 20231225143733.png]]
- Dense layer = each neuron in a layer is connected to every neuron in another layer.
- In a lot of tasks (esp Image Recognition), we need to capture local relationships since pixels far away don't contribute to our cognition of the picture.
	- So we make local filters to do a convolution over neurons in 1 layer, to get fewer neurons in the next layer.
	- ![[Pasted image 20231225144245.png]]
	- padding extra samples so output size isn't reduced
	- The filter will define some relationship about the neurons its applied to, such as 101 implies how much weight the neighbors have on the neuron.
	- stride = step size of filter over the matrix
- ![[Pasted image 20231225150159.png]]
- We get a new piece of information with every new layer of neurons
- One layer detects nose, one detects eye
- But we can't decide the NN knowing which layer will detect what.
- ![[Pasted image 20231225150448.png]]
- Convolutional layers = locally connected and reduces the parameters needed to be trained because they do "pattern recognition" in different local areas. 
- Filters do local transformations 
- In order to look for 10 characteristics/features (patterns) in different places, we need to build 10 filters.
- Tensor = 3d or more dimensional matrix
- 2012 had the boom in Deep Learning due to the development of gaming PCs with advanced GPUs which specialized in matrix multiplication (introducing first person universe creation on scrolling POV by scaling our matrices). ImageNet challenge saw cat detection get a massive accuracy jump due to CNNs.

## Autoencoders
- What if i don't have labels? How to still use NNs?
- You train the model until the output resembles the input
- Say input layer has 7 neurons, hidden layer has 4 neurons and output resembles input, then the 4 neurons capture the information of the 7 neurons.
- Bottleneck layer: the smallest layer that ENCODES the input layer.
- Once the input matches output, we can throw away the model before the bottleneck layer.
- Can be used for **Dimensionality Reduction**.
- Gives better results than PCA (linear dim reductioner) because its a non linear dimensionality reductioner.
- ![[Pasted image 20231225161830.png]]
- Denoising auto-encoders: 
	- Clean image -> add noise -> encode and get output -> loss function compares original image with output
	- This idea of negative samples, or adding noise is used for non-labelled data, and falls under **Self-supervised learning**.
		- I saw this repeating throughout word2vec implementations (adding negative samples), knowledge graph triplet corrections (generating incorrect triplets) and they check against the positive sample (the input that we already have).