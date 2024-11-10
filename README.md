# Classification with ELR loss
Image classification of CIFAR100 with nosiy label. Used ELR loss.  
dataset : https://www.kaggle.com/c/cifar100-image-classification-with-noisy-labels/overview

# What is ELR loss?  
Early-learning regularization loss[1]. It prevents models from memorizing noisy labels.  
![image](https://github.com/user-attachments/assets/63667852-5861-444b-b509-ca958c3bbfdf)  

# Method
Add a regularization term to the loss function. Takes advantage of the fact that Deep Neural Networks learn clean labels first and memorize noisy labels afterwards. 
Let x_i be the i-th input data, where vector p_[i] is the score vector predicted by the model under training, and vector t_[i] is the average vector of p_[i] during the training process. 
The loss function is configured so that if the network learns t_[i] well in the beginning with a clean label, then p_[i] will follow t_[i] in the future. 
This prevents memorization late in learning.

# Results  
a. ResNet18 with cross entropy loss  
![image](https://github.com/user-attachments/assets/0acb68da-310d-41a2-851c-2f12f267c178)  
b. ResNet18 with ELR loss
![image](https://github.com/user-attachments/assets/0648a9c5-8608-48a6-93b0-bae498cf69ca)  

# Discussion  
In both a and b, the train accuracy increases continuously, but the test accuracy increases and then decreases.  
Using CE loss, the test accuracy reaches a peak of 49.69% and then decreases, stopping at 39.44%.   
Using ELR loss, the test accuracy reaches a peak of 51.25% and then decreases, stopping at 40.83%.

# Reference  
[1] Liu, Sheng, et al. "Early-learning regularization prevents memorization of noisy labels." Advances in neural information processing systems 33 (2020): 20331-20342.
