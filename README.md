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
