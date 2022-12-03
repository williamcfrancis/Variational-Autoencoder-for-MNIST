## Variational Autoencoder for MNIST
In this project I trained a variational auto-encoder for generating MNIST digits. 
To learn about variational autoencoders, please refer to [Auto-Encoding Variational Bayes](https://arxiv.org/abs/1312.6114) by Kingma & Welling.

### Architecture 
The encoder consists of two fully-connected layers, the first has 14×14 = 196 inputs and 128 outputs (and tanh nonlinearity) and the second layer has 128 inputs and outputs (and no nonlinearity). Therefore, the latent factor z ∈ R (8 output neurons for the mean and 8 more for the standard deviation). The decoder takes in as input z ∈ R, pushes it through one layer with 128 outputs (and tanh nonlinearity) and then another layer with 196 output neurons (with sigmoid nonlinearity).

Let the parameters of the encoder be u and the parameters of the decoder be v. We maximize the objective
![image](https://user-images.githubusercontent.com/38180831/205464260-d2b5d371-5418-44ee-8a78-85890174bacb.png)

We are modeling pu(z | x) as a Gaussian distribution and the neural network predicts the mean µu(x) of the distribution and the diagonal of the covariance σu(x). The KL-divergence is:
 ![image](https://user-images.githubusercontent.com/38180831/205464297-1ddc9aea-b133-4ff2-a5da-be4fc979cee5.png)

We use a Bernoulli distribution to model pv(x | z) because we are using the binarized MNIST dataset
![image](https://user-images.githubusercontent.com/38180831/205464311-14ece9e1-a9c5-439d-a167-31de1c233ef6.png)

The auto-encoder is trained using the re-parametrization trick for computing the gradient of the u and standard back-prop for computing the gradient of the log pv(x | z).
