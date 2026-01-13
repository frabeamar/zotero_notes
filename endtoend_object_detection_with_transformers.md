DETR NOTES

remove hand-crafted components:

- no max suppression
- no anchors

easy architecture:

- cnn + transformers

loss function for bipartite matching ( pred / gt )

- uniquely assigns prediction to ground truth
- invariant to permutations

good on large object, bad on small ones

can do panoptic segmention with an ad hoc head.

LOSS FUNCTION:

- hungarian algorithm : one to one assignemnt between prediction and ground truth ( opposed to non-maximal suppresion, or fixed size prediction )

detr predicts N objects. If less than N objects are present in the picture then they predict the label “No object”

BIPARTITE MATCHING: find the permutation of the elements with the lowest cost. The cost is made up by regression and classification loss

- class imbalance -> L / 10
- box loss => boxes are predicted directly. to account for scale they consider l1 loss and generalized IoU loss (latter is scale invariant)

ARCHITECTURE

- extractor
- transformer

  - to learn different boxes you add object queries  ( learnt positional encodings ) they are transformet into an output enbeddigs
  - transformer architecture can reason about relations between objects
- mlp

  - box predictins: normalized center coordinates + class label + [no object ]

  TRAINING:

  - add lsses after each decoder layer