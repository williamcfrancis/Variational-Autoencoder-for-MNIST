## Variational Autoencoder for MNIST
In this project I trained a variational auto-encoder for generating MNIST digits. 
To learn about variational autoencoders, please refer to [Auto-Encoding Variational Bayes](https://arxiv.org/abs/1312.6114) by Kingma & Welling.

### VAE Architecture 
The encoder consists of two fully-connected layers, the first has 14×14 = 196 inputs and 128 outputs (and tanh nonlinearity) and the second layer has 128 inputs and outputs (and no nonlinearity). Therefore, the latent factor z ∈ R (8 output neurons for the mean and 8 more for the standard deviation). The decoder takes in as input z ∈ R, pushes it through one layer with 128 outputs (and tanh nonlinearity) and then another layer with 196 output neurons (with sigmoid nonlinearity).

Let the parameters of the encoder be u and the parameters of the decoder be v. We maximize the objective
![image](https://user-images.githubusercontent.com/38180831/205464260-d2b5d371-5418-44ee-8a78-85890174bacb.png)
