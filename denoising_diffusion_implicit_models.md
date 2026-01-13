# Summary

diffusion model are slow to sample from. To make it faster, you take shortcuts, for markov chain the next state depends only on the current one. Make it non-markov to jump part of the chain

Advantages over DDPM (prob models instead of implicit modesl)

1) superior sample generation quality

2) consistency : for chain of various length, you get similar high level features

3) because 2 -> you can perform semantically meaningful image interpolation

You have a long chain , T ~= 1000 so that the process become as good approximation of a gaussian conditional distribtuion. This makes it slow. So try to find alternative expression that lead to the same objective function  as DDPM

you train a model to predict the injected noise at step t, given the noise image of t so e = f(x\_t, t)

from some equation you get x\_0

you combine x\_o and your predicted noise to get back x\_{t-1}

The equation can be rewritten so that it’s formulation is the solution to an ODE with an Euler method.

# Various insights

you maxime the variational lower bound -> find the parameteres in the way that you describe your data the best

FID - Frechet inception distance:

distance between two distribution, the one on the pixels of the generated image and the real distirbution. Called inception as it take the feature vector of the architecture inception v3. assumes the images where taken from a multidimentional gaussian and it compare them with the wasserstein distance

Wasserstein distance - earth moving  - optimal transports

evaluates how much does it cost to transform one probability into the other one

# Questions

- ddps are learned with a fixed inference procedure [what does that even mean] instead of a trained one

  - you could say it is only sampling there is no nn in the loop, but then it would be random rather than fixed

- what is an implicit probability model
- to generate interpolation on a line you generate them with spherical linear interpolation ? why spherical ? normalized feature vectores?