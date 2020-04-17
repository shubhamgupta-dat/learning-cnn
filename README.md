# Learning-CNNs
A brief history of topics I covered to learn about CNNs

### What is CNN?
CNN is a class of Deep Learning Neural Networks, most commonly applied to analyzing visual imagery. They are also known as shift invariant or space invariant artificial neural networks. (SIANN)

### What are the applications of CNNs?
- Image and Video Recognition
- Recommender System
- Image Classification
- Medical Image Analysis
- Natural Language Processing
- Financial Time Series Analysis

## FAQs
Some important topics that need to be covered:

#### What is Hadamard Product? Where is it used?
Hadamard product is the element wise product of two matrices. It is used during kernel calculations.

#### What is convolution filter/kernel?



## Usual Problems faced while developing CNNs

### COVARIATE SHIFT

#### What is covariate shift?
Covariate shift refers to the change in the distribution of the input variables present in the training and the test data.

#### How to identify Covariate Shift?
- Preprocessing: This step involves imputing all missing values and label encoding of all categorical variables.
- Creating a random sample of your training and test data separately and adding a new feature origin which has value train or test depending on whether the observation comes from the training dataset or the test dataset.
- Now combine these random samples into a single dataset. Note that the shape of both the samples of training and test dataset should be nearly equal, otherwise it can be a case of an unbalanced dataset.
- Now create a model taking one feature at a time while having ‘origin’ as the target variable on a part of the dataset (say ~75%).
- Now predict on the rest part(~25%) of the dataset and calculate the value of AUC-ROC.
- Now if the value of AUC-ROC for a particular feature is greater than 0.80, we classify that feature as drifting.

#### How to treat Covariate Shift?
There are two ways to treat Covariate Shift in Data[[2]]:
- Dropping of drifting features
- Importance weight using Density Ratio Estimation

#### How does Internal Covariate Shift affects CNN?
During the training stage of networks, as the parameters of the preceding layers change, the distribution of inputs to the current layer changes accordingly, such that the current layer needs to constantly readjust to new distributions. This problem is especially severe for deep networks, because small changes in shallower hidden layers will be amplified as they propagate within the network, resulting in significant shift in deeper hidden layers.[[1]]

#### How to avoid Internal Covariate Shift in CNNs?
Introduce Batch Normalization to reduce these unwanted shifts to speed up training and to produce more reliable models.

#### What is Batch Normalization?

#### What are some advantages of Batch Normalization?
- Batch Normalization avoids internal covariate shifts.
- The network can use higher learning rate without vanishing or exploding gradients.
- It seems to have a regularizing effect such that the network improves its generalization properties, and it is thus unnecessary to use dropout to mitigate overfitting.
- It has been observed also that with batch norm the network becomes more robust to different initialization schemes and learning rates.

### Vanishing or Exploding Gradients

### REFERENCES:
[1]: https://en.wikipedia.org/wiki/Batch_normalization
[2]: https://www.analyticsvidhya.com/blog/2017/07/covariate-shift-the-hidden-problem-of-real-world-data-science/
