## Intro

pixel-wise dense matching; first coarse then fine.

usually you have feature detection, description and then matching.

feature detection reduces your search space for the matching. In the indoor scenario with low textures you might not get enough matches.

previous solution with dense matches and cnn have small receptive field. so here we use transformers

Loft introduces dense matches at low resolution.

## Linear attention

instead of softamax(qK.T)V

use the kernel trick to approximate the softmax soft(xy) = phi(x)\*phi(y)

phi is the elu function

softmax(qk.T)\*v = phi(q)phi(y) \* v

[NxN][Nxdv] -- [nxd][dxdv]

on the left the inner product goes over NxN to the right over Nxd, dxdv is small and can be neglected for the complexity

## coarse level matches

score matrix is the dot product of the feature descriptors

with optimal transport

have a cost assignment  matrix (- score matrix)

or dual softmax:

soft(S )\_on columns or soft(S) on rows

match selection through Mutual Nearest Neighbors

## fine level matches

crop a local window around the remaining matches then use a smaller loftr module to transform the cropped features.

Correlate the center vector from one image with all the other. Compute the final position by expectation over the probabilty disitrubtion  (sub-pixel accuracy : meanign you have a decimal value from the expectation).

## supervision

coars: likelihood over the coarse matches

( I assuming that the two images are homographies and matches can be define over the whole image)

fine:

l2 loss for the heatmap  + weighting by uncertainty. The more certain we are around point i, the smaller the error has to be

## Evaluation

OpenCv + ransac

compute the corner error to compare with methods that use a different number of matches.

Corner error: the l2 distance between the gt camera pose and the estimate pose

## Ablations

drops:

use cnn with a similar number of parameters instead of  a transformer

use positional encoding at every layer (like detr