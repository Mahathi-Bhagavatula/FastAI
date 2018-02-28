# Lesson3:- Working of CNN


### How does CNN work?

1. For every 3*3 matrix pixels, multiply with kernels, we get one layer of Convolution
2. After every kernel operation, we use activation function to make the layers more non-linear.
3. For the same image, multiply the 3*3 matrix pixels with another kernels, we get another layer of Convolution.
4. On this first layer of Convolution, use another set of filters we get another two layers of Convolution
5. Do max pooling on these layers, max pooling is nothing but selecting the maximum of a 2*2 matrix.
6. Append the two max pooling layers.
7. Use the weights of pretrained model (or use the weights of newly trained model) on this pooled layer to get the score/ value of the image w.r.t a particular class.
8. Using Softmax or Sigmoid, the class of the given image can be predicted.

In the above case, we are taking two kernels for each layer, but in general that depends on the number of channels that are present in the image, if we have 3 channel image RGB image, then we have 3 kernels for each layer.
