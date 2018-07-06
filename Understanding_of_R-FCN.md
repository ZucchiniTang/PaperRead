# R-FCN
2018.07.05  第一次撰写，因为怕忘记刚刚突然理解的结构 (没读论文，网上看博客，自己的领悟)

Paper: R-FCN: Object Detection viaRegion-based Fully Convolutional Networks (https://arxiv.org/pdf/1605.06409.pdf)


## 1.Overall architecture of R-FCN
![Overall architecture of R-FCN](image/R-FCN1.png)

首先，输入一张图片，用RPN提取得到ROIs.接下来对一张图片中每一个ROI进行position-sensitive score maps generation(这一步是R-fcn的key idea)得出k*k*(c+1)的map. 最后把k*k*(c+1)-->1*1*(c+1)，然后softmax得出probability最高的class为目标的class.

## 2.分步来讲每个步骤
![key idea of R-fcn ----> position-sensitive score maps](image/R-FCN2.png)
#### 首先搞清楚每个参数的意义:
1. k: size of position-sensitive score maps, 这里我们assume用3*3，所以本例中k=3
2. c: the number of classes. 我们用c+1做计算是因为加了一个背景类。比如我们想detect一张图片里的：人，车。则c=人+车＝2,c+1=人+车+背景＝2+1=3.
####　
