# Lesson2:- Data Augmentation & Differential Learning rates

### Data Augmentation :- 
1. In case we do not have much data to train and validate, then we use data augmentation to avoid over-fitting
2. Data augmentation is a procedure in which images are rotated, zoomed and manipulated such that each image can be represented as different images
3. Test time augmentation:- augment images and send for testing. This is mainly helpful if the images are of big size and are cropped inappropriately while testing.

Activation of a layer means that this particular feature (like eye ball, wheel, etc) is in this particular location with a certain probability.

### Annealing:-  
The concept of reducing the learning rate when it is getting closer and closer to global minima is called annealing. Cosine annealing is where the decrease in the learning rate is like a cosine curve. 

### Stoichastic Gradient Descent with restarts:-

1. While finding the global minima, there can be chances of picking not the exact global minima due to spikes in the sample dataset that has been picked up.
2. To reduce such possibility, whenever the algorithm reaches to global minima, we slightly increase the value and try to find the minima again.
3. Repeating this procedure, will land up getting a global minima which is irrespective of the dataset.
4. This procedure is referred to as Stoichastic gradient descent with restarts. 
5. Cycle_len is the parameter which indicates the number of restarts.
6. The concept of annealing when used along with cycle length,  will help to get correct global minima discarding the possibilities of differences in dataset. 
7. Cycle mult:- parameter which will increase the length of cycle for each iteration. This helps because every time we go deeper for each cycle to find the global minima.

### Differential Learning Rates:-
1. When the model is trained with pretrained weights, usually the last layers are trained with the data. To make sure that even the previous layers are trained with the new data, we use differential learning rates.
2. Unfreeze the previous layers. Frozen layers will not get updated. Unfreezing the layers will update the weights with new dataset as well.
3. Apply different learning rates at different layers.
4. Lower the learning rate implies there is so less for the layer to learn.
5. Hence, give lower learning rates to starting few layers as they have learned enough. Slowly increase the learning rate and apply to middle layers. Finally the highest learning rate is applied to the new layers.


### Steps to follow in training a CNN:- 
1. Enable data augmentation with precompute = True
2. Find the learning rate
3. Train last layers with precompute architectures for 1-2 epochs
4. Train last layers with data augmentation and precompute = False for 2-3 epochs with cycle_len = 1
5. Unfreeze all layers
6. Set earlier layers with 3x or 10x lower learning rates than next layer
7. Use lr_find again
8. Train full layer with cycle_mult= 2 until overfitting
 
### Some important points:-
1. Do not take lowest learning rate because you may have to decrease the LR more using this annealing concept.
2. When you do batch processing, it is generally 64 or 128 images we use for each batch.
3. Whenever you run the model for learning rate (lr_find), usually we run for one epoch. If we unfreeze layers, we run again for one epoch. No harm in running for many epochs.
4. If the images that we are dealing with is similar to imagenet dataset, then reduce the learning rate to 10X in step 6. Otherwise make it 3X.
5. If size and batch_size are less, then the model will learn fast and takes less memory.
6. Epoch is one pass through the data and cycle is number of epochs.
7. If we increase the size of same images and train again, then we can deal with overfitting, because the model considers the bigger images as new set of images all together.
8. The best ways to deal with unbalanced dataset is to make copies of smaller images.




