# Recurrent Neural Network (RNN)

# Why RNN

Artificial Neural Networks (ANNs) and Convolutional Neural Networks (CNNs) are powerful tools in the machine learning toolkit, but they have certain limitations when it comes to handling sequential data. Here’s a detailed explanation of why they may not be the best fit for sequential data and what alternatives might be better suited:

#### 1. Lack of Temporal Dependencies

   
Sequential data, such as time series or language data, has temporal dependencies where the order of data points is crucial. ANNs and CNNs, in their basic forms, do not inherently account for these temporal relationships. They treat each input independently and do not maintain information about the sequence in which data points appear.

#### 2. Fixed Input Sizes

   
ANNs and CNNs typically require fixed-size inputs. This can be a limitation for sequential data where the length of sequences can vary. While padding or truncating sequences to a fixed length is possible, it can lead to information loss or inefficiencies.

#### 3. Contextual Information

   
In sequential data, the meaning of a data point often depends on its context within the sequence. For example, in natural language processing, the meaning of a word can change based on the words that come before or after it. ANNs and CNNs do not inherently capture this context. While CNNs can capture some local patterns through convolutional filters, they still lack the ability to maintain long-term dependencies.


# Recurrent Neural Networks (RNNs)
RNNs are designed to handle sequential data by maintaining a hidden state that gets updated as the model processes each data point in the sequence. This hidden state acts as a memory of previous data points, allowing the model to maintain temporal dependencies.

![image](https://github.com/VarshaYK/RNN/assets/31321685/e63546ba-3788-4cbe-a857-3de100140cca)


## How RNN differs from Feedforward Neural Network?

Artificial neural networks that do not have looping nodes are called feed forward neural networks. Because all information is only passed forward, this kind of neural network is also referred to as a multi-layer neural network.

Information moves from the input layer to the output layer – if any hidden layers are present – unidirectionally in a feedforward neural network. These networks are appropriate for image classification tasks, for example, where input and output are independent. Nevertheless, their inability to retain previous inputs automatically renders them less useful for sequential data analysis.

![image](https://github.com/VarshaYK/RNN/assets/31321685/843d6484-1630-47c9-a762-a56c804dd1d4)


##   Integer Encoding

Integer encoding is a method used to convert categorical data, such as words, into numerical form so that they can be used in machine learning models


###  What is Integer Encoding?



#### Categorical Data: 

In the context of Natural Language Processing (NLP), categorical data often refers to words or tokens in text data. For example, consider the sentence "I love cats."


#### Need for Numerical Representation:

Machine learning models, including RNNs, cannot directly work with text data. They require numerical inputs.


#### Assigning Unique Integers: 

Integer encoding involves assigning a unique integer to each word in the vocabulary. For example:




"I" -> 1

"love" -> 2

"cats" -> 3


#### Conversion:

Using the assigned integers, the sentence "I love cats" would be converted into [1, 2, 3].



### Why Use Integer Encoding?  

#### Model Compatibility: 

RNNs and other neural networks require numerical input. Integer encoding provides a straightforward way to convert text to numbers.
Simplicity: It is a simple and effective method for small vocabularies or preliminary text processing.

#### Simplicity: 
It is a simple and effective method for small vocabularies or preliminary text processing.

### Limitations:


##### No Semantic Meaning: 
Integer encoding does not capture the meaning or similarity between words. For example, "cat" and "cats" might be encoded as completely unrelated integers.


##### Fixed Vocabulary Size: 
The vocabulary size must be determined in advance, and new or unseen words need special handling (e.g., assigning a special integer for unknown words).


## Embeddings

Embeddings in RNNs (and other neural networks) are a way to represent words as dense vectors of real numbers, which capture semantic meaning and relationships between words. This method is more sophisticated and effective than simple integer encoding. Here’s a simple explanation:


### What are Embeddings? 


#### Numerical Representation: 

Just like integer encoding, embeddings convert words into numerical form, but they go a step further by mapping each word to a high-dimensional vector.


#### Dense Vectors: 

Unlike sparse representations (like one-hot encoding), embeddings are dense vectors, meaning most elements of the vector are non-zero. For example, a word might be represented as a 50-dimensional vector like [0.2, -0.1, 0.5, ..., 0.3].


#### Capturing Meaning: 

These vectors are learned in such a way that words with similar meanings have similar vector representations. For instance, the vectors for "cat" and "dog" will be close to each other in the embedding space.


### Why Use Embeddings?


#### Semantic Similarity: 

Embeddings capture semantic relationships between words. For example, "king" and "queen" might have vectors that are close in the embedding space, reflecting their related meanings.



#### Dimensionality Reduction: 

Embeddings reduce the dimensionality compared to one-hot encoding. Instead of a vector as long as the vocabulary size, embeddings use much shorter vectors (e.g., 50 or 300 dimensions).



#### Improved Performance: 

By capturing meaning and relationships between words, embeddings often improve the performance of models on NLP tasks.



### How are Embeddings Learned?

#### Training with the Model: 

Embeddings can be learned during the training of the RNN. The model starts with random vectors and adjusts them based on the training data to capture useful patterns.


#### Pre-trained Embeddings: 

Alternatively, embeddings can be pre-trained on a large corpus of text (e.g., Word2Vec, GloVe) and then used in your model. These pre-trained embeddings already capture a lot of useful information about word relationships.


###  Example Process

#### Initialize Embeddings: 


Start with random vectors for each word in the vocabulary.


#### Adjust During Training: 

As the RNN processes the training data, it adjusts the embeddings to minimize the training error.


#### Use the Embeddings: 

Once trained, these embeddings are used to convert words to vectors before feeding them into the RNN.




# Different types of RNNs in terms of their input-output relationships

![image](https://github.com/VarshaYK/RNN/assets/31321685/b5568c3e-1814-4c3d-8411-fd1bde9bbc77)


## One-to-One RNN
### Example: 
Recognizing handwritten digits. (or Image classification.)

#### Input: 
A single image of a handwritten digit.

### Output: 
The recognized digit (e.g., 5).

## One-to-Many RNN

### Example: 
Generating music from a starting note. (or Image captioning.)

#### Input: 
A single starting note.

Output: 
A sequence of musical notes forming a melody.

## Many-to-One RNN

### Example: 
Predicting the next word in a sentence. (or Sentiment analysis.)

#### Input: 
A sequence of words in a sentence (e.g., "The weather is").

### Output: 
The next word (e.g., "nice").

## Many-to-Many RNN

### Example: 
Subtitling a video. (or Machine translation.)

#### Input: 
A sequence of frames from the video (many images).

#### Output: 
Corresponding subtitles (many words).

## Training through RNN

A single-time step of the input is provided to the network.

Then calculate its current state using a set of current input and the previous state.

The current ht becomes ht-1 for the next time step.

One can go as many time steps according to the problem and join the information from all the previous states.

Once all the time steps are completed the final current state is used to calculate the output.

The output is then compared to the actual output i.e the target output and the error is generated.

The error is then back-propagated to the network to update the weights and hence the network (RNN) is trained using Backpropagation through time.


## Advantages and Disadvantages of Recurrent Neural Network

### Advantages

An RNN remembers each and every piece of information through time. 

It is useful in time series prediction only because of the feature to remember previous inputs as well. This is called Long Short Term Memory.

Recurrent neural networks are even used with convolutional layers to extend the effective pixel neighborhood.


### Disadvantages

Gradient vanishing and exploding problems.

Training an RNN is a very difficult task.

It cannot process very long sequences if using tanh or relu as an activation function.

## Applications of Recurrent Neural Network

Language Modelling and Generating Text

Speech Recognition

Machine Translation

Image Recognition, Face detection

Time series Forecasting
