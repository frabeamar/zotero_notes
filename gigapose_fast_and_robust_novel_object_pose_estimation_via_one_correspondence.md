Comment: CVPR 2024

you have two networks :

- estimates azimuth & elevation
- scale & roll

by splitting the DOF recognition you can generate less templates.

They say you can make the network faster during inference by reusing computation during onboarding by splitting the network. Can’t you do the same with a normal network?

input is RGB - D

Need to read the megapose paper to understand the comparison