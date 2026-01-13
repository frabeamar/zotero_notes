Contrastive loss: for example penalize if the same image with two different augmentation has not the same label.   
or -> if they are different crops from the same image (do they need to share some)

Batch normalization prevents from learning good representations

similarily in IMT -> features where not normalized with DINO

intra-batch communication with BN ? (because you subtract the mean which has information on samples?)

why does shuffling the sample order affect training?

do you normally freeze BN in finetuning?

Query and positive example are from the same images, the queue has examples form different images and thats why they are negatives