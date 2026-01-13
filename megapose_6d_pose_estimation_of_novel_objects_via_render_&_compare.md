Summary:

first predict coarse pose and classify whether that pose can be refined or not, then refine the pose.

The refiner takes a query and a reference pose. Each step k you render a new image (refined pose from the previous iteration).

you assume that the refiner is able to correct perturbance seen in training.

-> not always true imo. In our experiment you could extend the training range to inf but that does not make your coarse model inf better

Questions:

- why do you need an anchor point?  
   -> higher error
- there is novel in the title but they specify that detection of novel object is outside the scope of the paper? do they mean it in the sense that they can refine each pose? but have to use a trained one for the coarse estimation?
- what is the anchor point

Concat:

augmentation for cozy pose were good for sim to real transfer: can we use them?