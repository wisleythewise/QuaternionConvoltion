# Accuracy obtained with no addiotinal tunen (aka benchmark): 50.9000%


## Hyperparameters that were tuned but did not result in an increase in the accuracy

- lr:             0.00001
- weight-decay:   1e-7


## To investigate

### Normalization of one and no filliping horizontal flipping int test set: 42.2800%

### Model without dropout, normal fullyconnected layers ad proposed in the paper and no normalization: 73.14% 
If we want to load the data of this model, it is called: 28_18_5_29_As_proposed_in_the_paper fot the model cnn

It seems while running that the normal fully connected layers are performing better. We are retrieving a loss of 1.7 instead of 2.1 on average. The weird thing is that is does not converge, which migt indicate that there is something wrong with the data loading. 

![Loss function](like_the_paper.png)

We have observed that we are not plotting the correct losses, it will have no impact on the implementation

### Normal CNN with excact as many filters as the QCNN and twice as few parameters: 60.3100%

We have tried to plot the correct losses now

![Loss function](normalCNN.png)

### Check how the weight initialization is done, and kept between the appropiate values 

### Look for other convolutional libraries



