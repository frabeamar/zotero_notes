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

QUESTIONS:

- what kind of training do you do for supervised learning with chatGPT? usually you predict the next word

  - => the loss is always cross entropy (between the predicted token and the real one). For supervised finetuning you fix the sequence to be the one from the labeller
- How do you evaluate truethfullness (in an automatic way)
- How do you train a reward model?