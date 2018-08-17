## This article is a summary of knowledgeabout Inception_Network
### Reference: 
   1. Medium: A Simple Guide to the Versions of the Inception Network (https://towardsdatascience.com/a-simple-guide-to-the-versions-of-the-inception-network-7fc52b863202)
   2. Inception v1 (https://arxiv.org/pdf/1409.4842v1.pdf)
   3. Inception v2 and Inception v3 (https://arxiv.org/pdf/1512.00567v3.pdf)
   4. Inception v4 and Inception-ResNet. (https://arxiv.org/pdf/1602.07261.pdf
   
   
### Inception v1 -----> GoogleNet
   1. Naive version  ![](image/Inception_v1.png)
   2. Inception module with dimension reductions  ![](image/Inception_v1_1.png)
   3. GoogleNet, has 9 such inception modules stacked linearly, It is 22 layers deep (27, including the pooling layers). It uses **global average pooling** at the end of the last inception module.
   ![](image/Inception_v1_2.png)
      1. Auxiliary loss 
         1. To prevent the middle part from 'dying out', so the authors introduced two _auxiliary classifiers_　
         2. Loss function  
            total_loss = real_loss + 0.3 * aux_loss_1 + 0.3 * aux_loss_2
         3. Auxiliary loss is purely used for training purposes, and is ignored during inference.
