# Different runs of our model

## QCNN Cifar-10
Below are the results of our QCNN model, ran on the cifar-10 dataset:

### 65% 
This was the first result we got that came close to the paper. We went from 10% accuracy to this accuracy by changing the way we preprocess the data. This is done in the 
``` convert_data_for_quaternion(batch) ``` function. This was achieved with the following hyperparameters:
+ normalization
+ no data augmentation
+ 80 training epochs
+ batch size = 32

### 67% 
We increased our accuracy by adding the following data augmentation techniques (as described in the paper):
+ ```transforms.RandomAffine(degrees=0, translate=(0.1, 0.1))```
+  ```transforms.RandomHorizontalFlip()```

### 68.5%
By changing the way we preprocess the data:
+ From ```inputs.append(torch.cat([batch[i][0], grayscale(batch[i][0]).size()], 0)) ```
+ to ```inputs.append(torch.cat([batch[i][0], torch.zeros(grayscale(batch[i][0]).size())], 0))```

**Here we realised that the model from the repository linked on Arxiv: https://github.com/XYZ387/QuaternionCNN_Keras has a different architecture than the one described in the paper:**

### 73.14% paper architecture QCNN
Model without dropout, normal fullyconnected layers as proposed in the paper and no normalization: 

If we want to load the data of this model, it is called: 28_18_5_29_As_proposed_in_the_paper 

Normal fully connected layers instead of Quaternion fully connected layers are performing better.

![Loss function](./modelsParameters/29_10_29_39_QCNN.png)

### Other runs:
#### 42.2800%
Achieved using normalization of one and no filliping horizontal flipping on the test set

## CNN Cifar-10
Below are the results of our cifar-10, when ran with the CNN model:

### 60.3100% 
Normal CNN with excact as many filters as the QCNN and twice as few parameters: 

![Loss function](normalCNN.png)

# Discussion

The table that needs to be repoduced is depicted below. However our test results seem to diverge from this table. *We are wondering if it is smart to keep on trying to achieve the 0.77 for the QCNN and 0.75 CNN or that it is smart to try and move on to other criteria (larger dataset, ablation study, hyperparameters check etc.)*.

![Table 1](./Untitled.png)


We were also wondering why it seems that our CNN performs so much worse and looking at our graphs vs those in the paper down below, our loss does not match at all, and we learn slower.

![Table 1](./losses.png)
