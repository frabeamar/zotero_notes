LLMs are trained to predict the next token, there is no knowledge of user intent.

train a model that is helpful, honest harmless

user reinformcement learning from human feedback to fine tune gpt3

write prompt and human answer, then collect comparisons between outputs from human and the model. train a reward model to predict which output would be the preferred on.

Train with ppo.

results:

less hallucinations, less harmful messages. Lower performance on certain nlp datasets (alignment tax). You can revert this by mixing ppo updates with updates that increase the log likelihood

finetuning lm on a range of nlp tasks with instructions improves their downstream performance on held-out tasks.

## Mitigate harm

removing documents where you have a high dconditional likelihood of generating trigger phrases. +

data filtering , removing n-grams during generation safety specific control tokens [model acts as a classifier when generating the next token, when it is detected either filter or activate chain of thougth in case is a false positive]

word embedding regularization , data augmentation, null space projection

null space of a matrix A is a collection of vectors x that project into 0. Gradient updates on this space will not affected (similar to continual learning - orthogonal gradient descent)

different objecting function

## Dataset

Create 3 different datasets:

- arbitrary tasks
- instructions + query  and response
- create the prompt for an pre-existing use case.

from this you create a dataset fro fine tuning, one to train a reward model, and the ppo dataset, without human labels. user for the rl hf finetuning.

## Training stages

supervised fine tuning  -  model overfits on validation loss after 1 epoch, but it helps RMscore and human preference ratings

RM  - cross entyropy loss (better output 1, other 0) trained with log odds that the response is preferred.  [previously]

train with sigmoid of the difference of the reward output for the human and the predicted output. [now] has less overfitting

RL - Train with ppo. Take a prompt produce a random response. Add a per-token KL penalty from the SFT model. Train to mix pretraining ggradients into the PPO graidents to fix the performance regression.

with ppo you train with ratio between the current and the old model. this is usually clipped to avoid that the model extract some high reward in a space that outputs only gibberish. Here we have the ration of the RL model wrt to the finetuned one.

QUESTIONS:

- what kind of training do you do for supervised learning with chatGPT? usually you predict the next word

  - => the loss is always cross entropy (between the predicted token and the real one). For supervised finetuning you fix the sequence to be the one from the labeller
- How do you evaluate truethfullness (in an automatic way)
- How do you train a reward model?