pre-training: supervised training

self-training: train on coco, generate labels for imagenet, pseudo labelled imagenet and labelled coco are trained for a new modl.   
If you pretrain on the same dataset, you can hurt your performance on your target dataset

OBSERVATIONS

- pre-training hurts when stronger augmentation is applied
- pre-training important when you don’t have so much data
- self -training works always, also with stronger augmentations
- self training works with after pretraining
- unsupervised training also reduce performance, even if it ignores labels as self-training.