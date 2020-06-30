# Machine_Learning_for_Signal_Processing

[Central Limit Theorem](https://github.com/prajakta0111/Machine_Learning_for_Signal_Processing/blob/master/00_Central_Limit_theorem.ipynb)


According to CLT, the sum of random variables gets closer to a Gaussian distribution. If
there are more random variables (i.e. scenes) added up, the mixture of them will be more
Gaussian-like. Therefore, you can measure the Gaussian-likeness of the sample distributions
of the three pictures to see which one is with more scenes. “A scene” here means the visual
object that can be observed without the shaken effect, while a shaken photo is a sum of
multiple “scenes” due to the too long exposure.
We will use a non-Gausianity metric, called “kurtosis,” for this. 
We will be standardizing the vectorized images by subtracting their sample means and by dividing by their
sample standard deviation.
Then we will calculate the kurtosis. The best image will be chosen based on this.
The images that we have are:

<img align="left" width="250" height="250" src="https://github.com/prajakta0111/Machine_Learning_for_Signal_Processing/blob/master/images/luddy1.jpeg">
<img align="left" width="250" height="250" src="https://github.com/prajakta0111/Machine_Learning_for_Signal_Processing/blob/master/images/luddy2.jpeg">
<img  width="250" height="250" src="https://github.com/prajakta0111/Machine_Learning_for_Signal_Processing/blob/master/images/luddy3.jpeg">



[Gradient_ascent_eigendecomposition](https://github.com/prajakta0111/Machine_Learning_for_Signal_Processing/blob/master/01_Gradient_ascent_eigendecomposition.ipynb)

We are looking for the largest eigenvalue, we would like to maximize this value, which is our
optimization goal. Differentiate the objective function, λ with respect to the parameters. The derivative is the gradient direction. Using the gradient direction, update your parameter. Your learning rate should be a small number so that the update is gradual. Be careful with the sign of the gradient. This time, you are MAXIMIZING your objective function, rather than MINIMIZING it. So, the update algorithm is actually gradient ascent, not descent. Another tricky part is the constraint that the eigenvector has to be a unit vector.
Once you subtract the contribution of the first eigenvector, your X won’t have
any variation along the direction defined by the first eigenvector. Repeat your gradient ascent-based eigendecomposition process on the new X matrix which
doesn’t contain any compoent from the first eigenvector.
