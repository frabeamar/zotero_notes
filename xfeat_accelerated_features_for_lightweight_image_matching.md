Questions :

- if you triple the channel count instead of doubling it like other methods don’t you end up having more paramenters instead of less?

  - because you reduce more with higher res earier

Summary

Keypoints based based are good for Sfm, dense feature for relative pose estimation.

Superpoint, alike, silk slow down with higher resolution

Xfeat is hardware independent

does not make depthwise sep convolution on large image resolution. It’s better to downscale the image.  and have a lighter network

Superpoint detects keypoints out of descriptors, here they have a separate branch that detects it out of the image directly. this is only because xfeat\* gets worse. feels ad hoc

for the keypoints head: reshape an 8x8 patch into 64 dim feature

you are training on dense feature->take the whole dense map for similarity values. you want high values on the diagonal (point correspondences)