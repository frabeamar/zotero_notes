OOD (out of distribution detection) or anomaly or normality detection means identifing a sample which is outside of the training data. The OOD space can be much bigger than the training data. Modelling the data distribution directly is prohibitibe

Previous method tried:

- to encode normality
- to define a new detection score
- contrastive learning
- reconstruvtion based  
  the reconstruction loss is the detection score. the network would not be able to reconstruct anomalies
- density based  
  use likelihood as the detection score - not good for deepl
- one-class classifier  
  learn a decision boundary between in and out of distribution samples; good for deep representation
- self supervised

# CSI: contrasting shifted instance

Apply augmentation which bring the sample out of distribution, use it as a negative sample

Use Contrastive learning (SimCLR) + instance discrimination.

The positive is an augmentation of the sample and the negative is a different image

Some transformation like rotation degrade the performance: it is more useful to have them as negative.

This paradigm does not help standard classification but it helps with ood.

Train with an auxiliary task -> which shifting transfomration is applied to a given input: sdd a linear layer to predict it.

The final loss is a combination of the two.

Measure ood=ness by AUROC, where this is calculated using the detection score. Use the transformation which perform better with this value. There are two effective detection scores:

- cosine similiarity to the nearest sample
- the norm of the representation ( constrastive loss increases the norm of in-distribution samples. you can minimize the cosine similarity by increasing the denominator. Still weird this happens since SimCLR uses the normalized features to compute the loss

Combine both to get cos-sim(z1, z2) |z1|. You can reduce computation by choosing a proper subset (coreset) of the training samples

Additional scores which are in parallel to the additional losses

- one is the expectation over the previous score cossim(z1, z2) \* |z1| ( how is this a probability distribution)
- the other is 1/Z (normalizing factor) \* W (of the linear layer for transformation prediction) \* encoder output

The score is more robust if you take it over random augmentations.

CONFIDENCE CALIBRATED CLASSIFIERS with supervised constrastive learning: instead of constrasting every instance here every representation of the same class is considered positive.

Some dataset have an easy way to detect out of distrubtion since they have image artificats

Here they propose to reduce analsys on image whcih have a smooth input. they define a smoothenss score based on how many pixel vary in the neighbourhood vs how many pixel vary in the image

# Result

winner on all benchamrks of one-class datasets (you don’t use labels)

particular effective on detection hard ( = near-distribution) samples.

Even if you have another image as a negative, overall training pushes together samples of the same class. (plot where you take the cossim of the second neareset sample (another sample after itself)

# ece

expected calibration error: divide the prediction in bins -> you want to have that the highest likelihood point has also the highest confidence

# Questions

- how do they use their new score function
- How do you know you are correct on unlabelled classes
- what are other methods to improve ece