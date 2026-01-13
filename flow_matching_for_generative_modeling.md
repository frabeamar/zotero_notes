flow matching wants to directly predict the end distribution from a standard gaussian without going through the denoising process. is a *simulation free approach* you don’t have to replay the whole path to get where you need to

you have a probability density which is dependent on time, a *probability density path*

you have a time dependent vector field, called *flow, aka, the way of moving throught the probability space*

at time 0 you have the sample

you learn the vector field

how do you set up the paths and the vector fields?

with flow matching you can end up at your target distribution in finite time

with diffusion models you move in circles: you move away from the point you were before and slowly get closer to the target

with cNF you can move in a straight line

# questions

what is denoising score matching