# Lesson1:- Introduction to Neural Networks & CNN

Any Successful algorithm should be having the following features:

1.Infinitely flexible function
2.All- purpose parameter fitting
3.Fast and scalable
 
 Let us see for Neural Networks:- 

1.Since neural networks rely on the concept of universal approximation theorem, it can solve any function closely enough with proper parameters. Hence can be Infinitely flexible function.

2.Gradient descent works pretty good for Neural networks because there are not many local minima and different global minima, all you have is equally good global minima so it can find the all purpose parameter fitting.

3.Scaling to different functions is possible with multiple hidden layers in the neural network. May not be possible with one hidden layer.


*CNN have linear layers to do matrix manipulations.
*Use any kind of non-linear functions to get non linear layers.. Ex:- Sigmoid, ReLU, etc
*Gradient descent is used to get the minimum in  the curve.

These three will constitute to CNN Architecture


How to determine the accurate Learning Rate:- 

1.Start with very small learning rate
2.increase/ double the learning rate
3.Stop where the loss function shoots up
4.Take the point where the loss function started decreasing rapidly
5.Note:- do not take the minimum. Just take the point before the minimum where the loss decreasing rapidly.

