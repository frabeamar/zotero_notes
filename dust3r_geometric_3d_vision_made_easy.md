Summary:  
Have an image, you want to estimate all camera parameters (extr, intr).   
Use Croco + a lot of data  
The network predicts point map (+confidences), optimize 3d projections

Insights

- they optimize 3d points to recover the depthmaps
- they don’t have gt camera poses, but gt point maps

Questions:

- what is a DPT
- what does MAE do