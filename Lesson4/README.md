# Lesson4:- Structural Neural Networks & Neural Networks for NLP

This lecture mainly focuses on both structural neural networks and Neural networks on NLP.

### Structural Neural Networks:

When  data which is well structured in the form of tables, defining each table and column are fed to Neural networks, the procedure of Structural Neural Networks is generally used.

A preliminary round of Feature Engineering is usually done on this data.

Features can be classified as two types, categorical and continuous variables

Continuous variables:- Variables whose data points can form a smooth curve if drawn on a curve. 

Categorical variables:-  Variables whose data points are discrete.

While selecting the features, categorical variables are always considered to be categorical. But continuous variables can be considered continuous or categorical depending on the feature. For example, features like Year, Date though they are continuous variables, they doesn’t show much significance if considered continuous (difference in the years might not show much significance). Hence can be preferred to be categorical

Creation of Embeddings for the Continuous and Categorical Variables is the important part of this lecture.

#### Embeddings for Continuous variables:- 
* Let us assume that there are 50 continuous features for the given dataset.
* Then the feature vector will be of dimension 1X50
* Now, if we want to project the data to a 300 dimension in a hidden layer
* The dimension of hidden layer matrix would be 50X300
* Note:- the number of rows of hidden dimension should be equal to the number of columns of feature vector.
* After matrix multiplication, the vector formed will be of dimension 1X300. This layer is referred to as linear layer
* Apply ReLu on top of the linear layer to make it non-linear
* Now, repeat the steps of choosing a hidden dimension, creating a matrix of hidden dimension, matrix multiplication and applying Relu for any number of times.
* Finally on the last layer instead of applying Relu, we apply Softmax for predicting the final result.

#### Embeddings for Categorical Variable:-
* Categorical variables are usually discrete values and doesn’t have a dimension >1
* Hence, assume a random dimension and initialize randomly.
* Thus, if we assume the dimension of categorical variable as 10, then dimension of the vector is 1X10
* If we want to project the hidden dimension as 300, the dimension of hidden matrix is 10X300.
* Now, upon matrix multiplication, the linear layer is 1X300
* Apply Relu to the linear layer for non-linearity
* Repeat the process of steps 4,5,6 for any number of times according to the dataset and the problem.
* Finally on last repetition, replace Softmax for Relu for predicting the final result

Note:- Both in Continuous and Categorical embeddings, there are dropout layers in between with the defined probability.

Thus, using these embeddings, we get to define and fit the model with different cycle_lengths and metrics (as defined in the problem statement).


### Neural Networks for NLP:-

Unstructured text is the main dataset for NLP tasks. 

NLP tasks includes the following steps:

* Tokenization:- splitting the text into words and special characters is referred to as tokenization
* Creating a language modelling model. 
* Language model can be described as the machine learning the sequence of text by looking into the repetitive sequences of text numerous times.
* So, a language model can easily predict the next word, given a sequence of words.
* This language model can be used as a pretrained model for any classification tasks on text.
* Intuition behind this idea is that, the pretrained model will learn the text and the sequence of text. So, any additional layers on top of this learned model will give a better understanding of the text.
* Language modelling on letters instead of words as a pretrained model can give even better results (need to be experimented).



#### Building Language Model:-
* Entire text is converted into vocabulary (unique set of words) greater than a min term_frequency
* Each word in the vocabulary is assigned an index. Such that entire text can be converted to vectors of corresponding indexes of text.
* Now, given a batch size, split the entire vector into equidistant vectors. For example, given a text of size 4000, the index vector size will also be 4000. Now, if the batch size is 40, then the 4000 vector is converted to 100X40 matrix.
* Given another parameter BPTT (backpropagation through time), we get to split the matrix formed previously by rows. For example, if the bptt is 10, then the matrix 100X40 can be split into ten 10X40 matrices.
* Now, considering an embedding of 200 dimension vector randomly assigned for each index in 10X40 matrix, we get to train the model and learn the embeddings.

#### Building the classifier model:-
* Consider the embeddings created in the language model.
* Using them as pretrained vectors, a classification model has been trained on the tagged data.
* Clip is a functionality which makes sure that the learning rate doesn’t go too high.
* Use similar functionalities of lr_find,freeze, fit, unfreeze, cycle_len as that of any classification models.

### Dropout :-

* Another important concept that has been discussed in this lesson is regarding dropout.
* Dropout is a concept of removing certain number of weights with a defined probability.
* The average weight of the entire matrix is remained intact even after dropout by doubling the remaining weights
* The reason behind doubling the remaining weights is that the thresholds and other parameters are kept intact even after dropout. 
