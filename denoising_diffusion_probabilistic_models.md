you have a markov chain where at each step you add random gaussian noise. you train a model to learn the reverse diffusion process.

codelength use to describe imperceptible (high frequency details) DDIM adjust this with compression

both the forward and the reverse process have the same functional form when the noise variance is small ->

if the noise you add is small there you can say that xt will be almost certaintly around x\_t-1

then you can have sampling at arbitrarily point t -> you consider all noise steps together

therefore you can optimizer for random steps into the chain

fix the noise as constant-> the forward process is deterministic

you want the gap between the train and the test likelihood to be possibly small to show that  you are not overfitting

i

# Modelling the reverse process

- diagonal variance => calculation of the expectations depends on the means

# Interpolation

start with a source image, then predict the noise you would need to get to the target image.

# Langevin dynamics

is a way to sample from a distribution with an energy function:

you take a step into the direction of the gradient and then you add noise

# Questions

- what does it mean to have a competitive log likelihood?
- parametrization of diffusion models reveals an equivalence with denoising score matching?
- what are codelengths in this setting

  - codelength := how many bits you need to encode the data without loss  
    codelength and negative log likelihood are the same thing  
    E[p(x)] <= elbo   
    E[p(x)] = H(x) -> and the entropy < elbo