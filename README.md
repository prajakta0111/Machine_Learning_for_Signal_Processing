# Machine_Learning_for_Signal_Processing

## [Central Limit Theorem](https://github.com/prajakta0111/Machine_Learning_for_Signal_Processing/blob/master/00_Central_Limit_theorem.ipynb)


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



## [Gradient_ascent_eigendecomposition](https://github.com/prajakta0111/Machine_Learning_for_Signal_Processing/blob/master/01_Gradient_ascent_eigendecomposition.ipynb)

We are looking for the largest eigenvalue, we would like to maximize this value, which is our
optimization goal. Differentiate the objective function, λ with respect to the parameters. The derivative is the gradient direction. Using the gradient direction, update your parameter. Your learning rate should be a small number so that the update is gradual. Be careful with the sign of the gradient. This time, you are MAXIMIZING your objective function, rather than MINIMIZING it. So, the update algorithm is actually gradient ascent, not descent. Another tricky part is the constraint that the eigenvector has to be a unit vector.
Once you subtract the contribution of the first eigenvector, your X won’t have
any variation along the direction defined by the first eigenvector. Repeat your gradient ascent-based eigendecomposition process on the new X matrix which
doesn’t contain any compoent from the first eigenvector.


## [Eigenvectors for two notes](https://github.com/prajakta0111/Machine_Learning_for_Signal_Processing/blob/master/02_Eigenvectors_for_two_notes.ipynb)

flute.mat is a matrix representation of the two musical notes played by a flute. The input matrix X has 143 column vectors, each of which has 128 frequency elements. Estimate two eigenvectors from this by using the program we used in [Gradient_ascent_eigendecomposition](https://github.com/prajakta0111/Machine_Learning_for_Signal_Processing/blob/master/01_Gradient_ascent_eigendecomposition.ipynb). This time, since the
eigenvectors are multidimensional, you need to draw a graph of each of them rather than a
line. Once again, it will look like the tall two-column matrix. Now you know the representative spectra for the two notes. How would you recover their
temporal activations? They will be two row vectors for the two notes, respectively. You need
to come up with an equation for this, and plot the activation (row) vectors you got from this
procedure in the report. Finally, since you know the basis vectors and their activations, you can recover each source
separately. How would you recover the first note? Come up with an equation for this, and
plot the result.

## [De-Beeper](https://github.com/prajakta0111/Machine_Learning_for_Signal_Processing/blob/master/03_De-Beeper.ipynb)
x.wav is a speech signal contaminated by a beep sound. we will learn how to do
STFT, so we will manually erase the beep sound from this signal to recover
the clean speech source. If you have a perfect pitch, you might be able to know the pitch of
the beep, but assuming that we don’t, we have to see the spectrogram to find
out the beep frequency. First off, create a DFT matrix F.

Prepare your data matrix X. You extract the first frame of N samples from the input signal,
and apply a Hann window (or any other windows that can overlap-and-add to one). What
that means is that from the definition of Hann window1
, you create a window of size N and
element-wise multiply the window and your N audio samples. Place it as your first column
vector of the data matrix X. Move by N/2 samples. Extract another frame of N samples
and apply the window. This goes to the second column vector of X. Do it for your third
frame (which should start from (N + 1)’th sample, and so on. Since you moved just by the
half of the frame size, your frames are overlapping each other by 50%.

Apply the DFT matrix to your data matrix, i.e. F X. This is your spectrogram with complex
values. See how it looks like (by taking magnitudes and plotting). Locate two thin horizontal
lines. They are from the beep sound. Note that due to the conjugacy your spectrogram is 
mirrored vertically. The bottom half is a mirrored version of the top half in terms of their
magnitudes, although their imaginary parts are with a different sign (complex conjugate).
The spectrograms you’ve seen in class are the top half of a spectrogram, because the bottom
half has no useful information (except for the flipped phase). This is why you see two beeper
lines in your spectrogram. Anyway, locate them, and make the entire row zero.

Apply the inverse DFT matrix, which you can also create by using the equation in L4 S12.
Let’s call this F. Since it’s the inverse transform, F∗F ≈ I (you can check it, although the
off diagonals might be a very small number rather than zero). You apply this matrix to your
spectrogram, which is free from the beep tones, to get back to the recovered version of your
data matrix, Xˆ . In theory this should give you a real-valued matrix, but you’ll still see some
imaginary parts with a very small value. Ignore them by just taking the real part. Reverse
 the procedure we did earlier to get the time domain signal. Basically it must be a procedure that
transpose every column vector of Xˆ and overlap-and-add the right half of t-th row vector
with the left half of the (t + 1)-th row vector and so on. Listen to the signal to check if the beep tones are gone.


## [Parallax](https://github.com/prajakta0111/Machine_Learning_for_Signal_Processing/blob/master/04_Parralax.ipynb)
You live in a planet far away from the earth. Your solar system belongs to a galaxy, which
is about to merge with another galaxy (it is not rare in the outer space, but don’t worry, the
merger takes a few billions of years). Anyhow, because of this merger, in the deep sky you
see lots of stars from your galaxy as well as the other stars in the other neighboring galaxy.
Of course you don’t know which one is from which galaxy though.

You are going to use a technique called “parallax” to solve this problem. It’s actually very
similar to the computer vision algorithm called “stereo matching,” where stereophonic cameras
find out the 3D depth information from the visual scene. That’s actually 
