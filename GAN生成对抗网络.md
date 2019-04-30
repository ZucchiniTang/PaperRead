## GAN used in Classification, object detection and semantic segmentation
## Reference
1. Paper: Xiaolong Wang, Abhinav Shrivastava, Abhinav Gupta, 'A-Fast-RCNN: Hard Positive Generation via Adversary for Object Detection'

## Understanding of Paper1 : A-Fast-RCNN
__论文需要解决的问题__： 现在主流方法是使用CNN来做识别，但CNN泛化能力弱，相对于困难样本（例如：occluded, 形变等），CNN只能通过data-drive即增多训练样本来提高检测精度。
再加上现实生活中（包括主流数据集中）的场景follow a long-tail（长尾效应），需要更多训练样本才能正确被识别的困难样本的样本数过少，导致困难样本识别率过低。本文通过使用GAN
生成困难样来提升模型检测率。  ----> generate 'hard' positive examples with different occlusions and deformations instead of generating the pixels themselves.


__idea__: 基于Faster_RCNN，在ROI Pooling后加入ASDB（生成Occlusion sample）和ASTN（生成deformation sample）. 结构如图

__ASBD__: Adversarial Spatial Dropout Network

