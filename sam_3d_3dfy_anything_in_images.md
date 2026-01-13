# multistage training

- supervised pretraining with synthetic images
- mid training with rendered objects into real images

  - these two parts are trained with *rectified conditional flow matching*
- model in the loop

  - you automatically create a 3d shapes, a human annotator selects the best one, or declare that non of the options are good. + some objects 3d artists create ground truth
  - close the domain gap (train with real data) and align for preference in shape quality
  - cold start problem: the model does not generate good samples at the beginning of training. so you retrieve good examples to add them to the training set
  - select the best candidate out of N choices.

    - for data that is rare in training, sample often and use reward models to select the best one
- render and paste pipeline  
  use a synthetic 3d object in a natural image (i guess you have gt) position and size are determined by the object mask A pointmap from a single-image depth estimator helps to guide visibility and occlusion.
- object swap  
  removes the original object via inpainting, inserts the rendered mesh with a random 3d + rotation R
- object swap

# Questions

- wtf is latent flow
- mixutre of transformer architecture?
- what is the reward for the reward model? -> the human annotation
- how do you use flow matching with 3d?does it