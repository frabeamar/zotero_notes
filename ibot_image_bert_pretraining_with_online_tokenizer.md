Interesting:

- you can use the k patch tokens with the highest attention score to do part-wise linear classification.

  - not computation efficient (you still need them all). If you add a matchbility token then you do something similar to lightglue
- Visualizing the attention maps from different heads shows that the network focuses on parts of the objects

Questions:

- what is the difference between local and global crops
- a