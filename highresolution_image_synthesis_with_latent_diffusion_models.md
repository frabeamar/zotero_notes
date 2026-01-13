SUMMARY

latent diffusion is expensive -> apply them in the latent space of autoencoders

likelhood models maxime the likelihood on the dataset. Failure of covering the dataset would increase the loss -> they cannot output alwyas the same  the same like gans

previous method where learning a 1d compressed vector, destroying the structure of the image

computationally expensive:

- computation resources are use to model imperceptibile details (gradient backprop on background for example)
- can be reduced undersampling the initial denoising step

two stages:

- perceptual compression: removes high freq detail + little semantic variation
- semantic compression: learn the actual semantic and composition of the data

to reduce computations actually separate the two stages -> latent diffusion models

- train a low dim autoencoder

  - loss: perceptual loss + patch based adversarial objective ( local realism, avoid blurring)
  - regularization:

    - KL reg -> kl penality to make it similar to a VAE
    - vq-reg -> has a vector quantization within the decoder
- dunno

LATENT DIFFUSION MODEL

probabilistic model, they denoise a normally distributed variable => aka reverse process of a fixed Markov Chain  ( the next state depends only on the current state)

CONDITIONING:

Add a domain specific encoder for prompts, then map it to intermediate layers of unet via cross attention layers

QUESTIONS

- why are diffusion models likelhood models
- why do you have a score-based prior
- is the noise added to the latent space?