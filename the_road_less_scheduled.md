Summary

Having a stopping step gives better performance, but you don’t have theoretical worst cast performance

So:

schedulers have worst-case convergence guarantees, SGD does not but it works better in practice  
- there is an optimal choice for the learning rate give any fixed time training (in theory! they perform badly) larger steps perform better

Questions:  
- what do they mean by stopping step. Schedulers usually start after some steps?

- optimality means lowest test loss? yes
- D = |x1- x\*|,  
  G = g-lipshitz ??? maxium of all the gradients of the loss function?  
  T=stopping time

- what is online-to-batch  conversion theorem
- what are x,z,y, c (state, weights, output, schedule?)