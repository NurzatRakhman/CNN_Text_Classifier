## Multi-Class Text Classification using Convolution Neural Networks.  

This is an example of how effectively use Convolutional Neural Network to classify  
obfuscated(order of words can be mixed) text into 12 classes. 


### Sequence Embedding 
One-hot encoding: Character in sequence represented by vector of size 26, corresponding character has value of 1, the others are 
zero-valued e.g. if a ->  [1, 0, 0, ....0]
   
### Model Architecture  

| Layer (type)  | Output Shape  | Param  |
| ------------- |:-------------:| -----:|
| model_1 (Model)    | (None, 452, 96)  |10080 |
| conv1d_4 (Conv1D)       | (None, 449, 32)      |    12320  |
| activation_1 (Activation) | (None, 449, 32)       |    0 |  
|max_pooling1d_1 (MaxPooling1)  |(None, 89, 32) |    0 | 
|dropout_1 (Dropout)    | (None, 89, 32)  |    0 |  
|flatten_1 (Flatten)    | (None, 2848)    |    0 | 
|dense_1 (Dense)        | (None, 12)      |    34188 |  
|activation_2 (Activation)  | (None, 12)      |    0 | 

Total params: 56,588
Trainable params: 56,588
Non-trainable params: 0 


In conv1d_4 layer, we concatinate results of different N-Grams windows, specifically N = 3, 4, 5, 
which enables us to use look for close and far neighbors.  


