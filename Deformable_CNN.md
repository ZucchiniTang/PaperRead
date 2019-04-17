## This article is the conclusion of Deformable CNN
### Reference:
  1. 知乎： 如何评价 MSRA 最新的 Deformable Convolutional Networks？ (https://www.zhihu.com/question/57493889/answer/184578752)
    1. 摘录： 
      1. 为了消除网络难以适应几何变形，研究员们对卷积核中每个采样点的位置都增加了一个offset.
      2. Deformable-CNN 中增加的offset是网络结构的一部分，通过另外一个平行的标准卷积单元计算得到，通过梯度反向传播进行端到端的学习
