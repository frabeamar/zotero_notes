WHY:

why do you add the output of the prediction to the loss?

- force to learn a low magnitude feature representation
- object: predict more than just this image is different than the usual distribution
- => they escapes me

Real time application->

- 2ms latency and 600 images per second  
    
  student network approach:

- train a student to predict the features computed by a pretrained teacher network on anomaly-free images
- student has never seen anomalous images->it will not predict them well. Differences in the anomaly scores -> anomaly detection

to enhance this you could try *architectural asymmetry* .

Otherwise *loss-induced* asymmetry for *structurally difference in images*

For logical constraints: autoencoder

- size, arrangement

outlier detection and density estimation in feature space

- feature vectors mapped to input pixels you have a 2D map
- to do so:

  - multivariate Gaussian distribution
  - Gaussian Mixture Models
  - Normalizing Flow (Patch Core, FastFlow)
  - Knn algorithm

Autoencoder can reconstruct images with anomalies

-> compare the original with the reconstructed image, but does suffer from false positive  
-> generate synthetic anomalies in the pretrained feature space to train a discriminator

EFFICIENT PATCH DESCRIPTORS

- each patch (33x33) correspond to an output neuron

  - you cannot trigger the same anomaly twice
- 4 layers-> small -> distill a deep pretrained calssification network
- FLOPs and throughput is not always the same

Loss to favour asymmetry between teacher and student.

- find the right balance between training for too long (ST are equal no anomaly) or too little (S is too dumb)

HARD FEATURE LOSS

- compute ( output\_image\_teacher - output image\_student) \*\*2, take the most difficult ones ( > p\_hard, chosen as a quantile) for backpropagation

  - you are assuming that outliers are not within that quantile
  - you are assuming that anomaly gives *consisten*t signal and noise will be optimized out ( beginning of training)
- inference: average across channels
- add magnitude of the student on images taken from ImageNet ( to avoid predicting anomlies only for out of distribution )

LOGICAL ANOMALY DETECTION

- train autoencoder to predict the output of the teacher.
- on image with anomalies the autoencoder fails  ( it has a bottleneck) BUT it also has problems on normal images
- teach the student to predict the output of the autoencoder

  - student learns systematic errors on the autoencoder, but not the anomalies, because it has not been trained on them.

GLOBAL ANOMALY MAP : autoencoder-student

- know the reconstruction error of the autoencoder

LOCAL ANOMALY MAP: student - teacher.

combine the above -> needs to be normalized, so that detection in one of the maps don’t prevail.