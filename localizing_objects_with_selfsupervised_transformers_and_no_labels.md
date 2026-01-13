LOST:

detect object ( =construct bbox) by using dino similiarties. You construct a graph by assigning a edge to patches with positive correlation. You choose a seed point as the patch with the lowest degree. you expand this point by joining patches with positive correlation to the seed and low degree.

Based on the assumption:

- object is small (not always true for our application)
- object correlates negatively with the background (also not true for use)