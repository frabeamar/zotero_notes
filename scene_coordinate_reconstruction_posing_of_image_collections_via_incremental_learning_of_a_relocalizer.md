Summary

take a visual relocalizer (ACE), train in a self-supervised fashion, make it faster by early stopping.

To train in a self-supervised manner you need to reformulate the task: do scene coordinate reconstruction instead of regression

ACE is trained with estimated gt, therefore you have a pose refinement step.  
To avoid drift (nothing is fixed here) use regularization : small weights update in the refinement step

initialization

- uses an additional network (for depth estimates)

QUESTION:

are they using gt at all?