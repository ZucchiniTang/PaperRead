# Understanding of SSD 网络
2018.07.06 现在谈一谈对ssd的理解，为什么ssd对size小物体敏感的低，性能不好。

### 话语摘录：　

  1. 针对YOLO和Faster R-CNN的各自不足与优势，WeiLiu等人提出了Single Shot MultiBox Detector，简称为SSD. https://zhuanlan.zhihu.com/p/32929487

  2. SSD网络中分为了6个stage，每个stage能学习到一个特征图，然后进行边框回归和分类. (如fig 1.) https://zhuanlan.zhihu.com/p/32929487

      1. SSD网络以VGG16的前5层卷积网络作为第1个stage (虚线框内)
    
      2. 然后将VGG16中的fc6和fc7两个全连接层转化为两个卷积层Conv6和Conv7作为网络的第2、第3个stage
    
      3. SSD网络继续增加了Conv8、Conv9、Conv10和Conv11四层网络，用来提取更高层次的语义信息 
    
![SSD Architecture](image/SSD1.jpg)
  
  3. 主流的算法主要分为两个类型:
      1. __two-stage方法__，如R-CNN系算法，其主要思路是先通过启发式方法（selective search）或者CNN网络（RPN)产生一系列稀疏的候选框，然后对这些候选框进行分类与回归，two-stage方法的优势是准确度高
      2. __one-stage方法__，如Yolo和SSD，其主要思路是均匀地在图片的不同位置进行密集抽样，抽样时可以采用不同尺度和长宽比，然后利用CNN提取特征后直接进行分类与回归，整个过程只需要一步，所以其优势是速度快，但是均匀的密集采样的一个重要缺点是训练比较困难，这主要是因为正样本与负样本（背景）极其不均衡（参见Focal Loss），导致模型准确度稍低。不同算法的性能如图1所示，可以看到两类方法在准确度和速度上的差异。

### 特征向量
  1. 特征向量的生成: 在SSD中，每个Default Box将生成C+1+4(regression　offset)维特征向量。
  
### 新增卷积网络
  1. Conv8、Conv9、Conv10 and Conv11
