# R-FCN
2018.07.05  第一次撰写，因为怕忘记刚刚突然理解的结构 (没读论文，网上看博客，自己的领悟)

Paper: R-FCN: Object Detection viaRegion-based Fully Convolutional Networks (https://arxiv.org/pdf/1605.06409.pdf)


## 1.Overall architecture of R-FCN
![Fig 1. Overall architecture of R-FCN](image/R-FCN1.png)

首先，输入一张图片，用RPN提取得到ROIs.接下来对一张图片中每一个ROI(Region-of-Interest)进行position-sensitive score maps generation(这一步是R-fcn的key idea)得出k*k*(c+1)的map. 最后把k*k*(c+1)-->1*1*(c+1)，然后softmax得出probability最高的class为目标的class.

## 2.分步来讲每个步骤
![Fig 2. key idea of R-fcn ----> position-sensitive score maps](image/R-FCN2.png)
#### 首先搞清楚每个参数的意义:
1. k: size of position-sensitive score maps, 这里我们assume用3*3，所以本例中k=3
2. c: the number of classes. 我们用c+1做计算是因为加了一个背景类。比如我们想detect一张图片里的：人，车。则c=人+车＝2,c+1=人+车+背景＝2+1=3.
3. 为了便于理解，我们使用people作为检测目标。
#### 细讲position-sensitive score maps
首先看 Fig 1.,懂得R-CNN到Faster R-CNN的都明白RPN网络(region proposal network)，这里先不细讲。一张input image经过RPN之后，会在这张image里得到一个或者多个ROIs--->一张image里有一个或者多个人; 也可能0个ROIs,整张input image里没有人.　这里我们可以对每个一个ROIs都进行一次position-sensitive score maps的计算，但是如果这样的话，会消耗很多精力。所以R-fcn的做法是在的到ROIs之前，对图像的每个feature map再分成k*k张feature maps，本例中为3*3=9个feature maps(也就是Fig 1.and Fig 2.中９种颜色的block--->此时每块同颜色的block的厚度是c+1).

那么不同的颜色块又有什么区别呢？看图fig 1.对不同颜色block有标注(top-left, top-center, ..., bottom-right)，第一张黄色的feature map其实就是一张概率图，相对于我们检测目标(eg.用一个框在检测人时，这个框所的左上部分包含的内容)的top-left的位置，input image中越接近检测目标的top-left,则所得概率图中value越大-->表示input的图中每个区域是检测目标的top-left的概率。第二张淡黄色的feature map是检测目标的top-center的概率.第三张是最淡的黄色的那张feature map则对应top-right;绿色淡绿色最淡绿色分别对应第四第五第六张，分别对应middle-left, middle-center, middle-right；蓝色淡蓝色最淡的蓝色分别对应第七八九张，分别对应bottom-left, bottom-center, bottom-right.

