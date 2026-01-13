You have a set of images.

you predict: camera parameters (extr + int insics) + depth maps + point map  + tracks   
tracks are not 3d points but features, which are then used for tracking

the first image is your reference frame, the rest of the ordering does not matter.

you predict even related quantities, even if they have closed form relationship: better performance during training.

During inference it;s better to generate the point maps from depth+camera params

you only have self attention. This is applied at each frame or globally (so I guess each token in a specific location at different times?)

## prediction heads

each image token gets augmented with a camera token and four register tokens. The camera and register token of the first frame are a different set of learnable parameters than all the rest ( make the remaining sequence permutation invariant)

register tokens are discarted.

the iamge token are are used to predict the depth maps, point maps and tracking features. The tokens are reassembled into image via dpt layer.

you predict both mean and the uncertainty.

For tracking you use cotracke2. take image 1 (but any other works) find a query point, construct a set of correlation maps to find which 2d point correspond the the same point you selected

## losses

camera : huber loss

depth loss: you add the uncertainty into the loss function. they add a gradient based term. Gradient is useful for sharp edges. otherwise you only care about your average error. you get avoid having steps into your depth function prediction. it implicitly set the prediction fo correct surface normal (gradient of a depth map is a  surface normal) ? is it?

point loss, same as above

# Questions

how does alternating attention work:

attention should shift between frame-wise and global (is this the same module)

what are register tokens?

you can have some high norm artifacts in the attention maps, its’, specifically around background, where the model tries to save global information. To avoid cluttering the image you add register tokens which are then removed.

what is a dpt:

unflatten the list of takens and transform it back into an image. The 1x1 and 3x3 convolution are applied.