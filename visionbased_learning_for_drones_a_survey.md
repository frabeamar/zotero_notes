### Visual percetion  - indirect method

detect - map -> action

you have rgb-d cameras, you don’t need to generate depth from a monocolar image

for MAPPING, you still need to generate a point cloud map or octmap.

PATH PLANNING

- offline

  - dijkstra
  - a star
  - rrt connect
  - sequntial convex optimization
- online

  - fast-planner
  - ego-planner  
    faster than the above but requires rgbd and lidar

# End to end method

reifnorment learning - but a lot of data to generalize

ON POLICY: evaluate or imporve the policy used to make decision

- sarsa
- ppo

OFF POLICY: try to learn policy different than what is used to generate the action

- q learning
- imitation learning; mimic tasks execution

MULTI AGENT reinformcemnet learning

- each agent has to collaborate for the success of the group

To train for generatlization policies are trained in simluations. Different environment eists.

# semi direct methods

either predict the necessary information from the image (position of the obstacle and teh lr or get the states and then train the control policy

# interect method

intermediate feature, leike position and velocity