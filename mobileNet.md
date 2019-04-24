## Reference  
此文章为reference中原文加上+个人看法
  1. 知乎：轻量化网络ShuffleNet MobileNet v1/v2 解析（https://zhuanlan.zhihu.com/p/35405071）
  
## 摘录
  1. 在实际应用中CNN应用受限于硬件与存储, 如不能在无人机上挂几张Nvidia Titan Xp. (Ref 1)

## 细说 (MobileNet V1 -> ShuffleNet v1 -> MobileNet v2 -> ShuffleNet v2)
### Group convolution
1. What is Group Convolution?
### MobileNet V1
1. Contribution: 用Depthwish+Pointwise代替传统卷积，输出维度相同，计算量减少。
2. 传统卷积  
假设input size: N×H×W×C, kernel: 3×3×k (注：N:batch_size, H: image height, W: image weight, C: channel, k: the numbers of kernel .). If padding = 'SAME', output size: N×H×W×k
<p align="center">
         <img src="image/CNN_kernel.jpg" height="250" width="480"> 
      </p>
3. Depthwise  
和传统卷积同样，input size: N×H×W×C， kernel:3×3×m (下图group = C组，所以下图m=1, m由group决定)，实际意义是为了对每个channel c单独做卷积。If padding = 'SAME', output size: N×H×W×C
<p align="center">
         <img src="image/MobileNet_depthwise.jpg" height="250" width="480"> 
      </p>
4. Pointwise  
和传统卷积同样，input size: N×H×W×C， kernel:1×1×k。If padding = 'SAME', 且 stride=1，实际意义是为了对input中channel c中同一位置的pixel做卷积，所以叫pointwise。 output: N×H×W×k
<p align="center">
         <img src="image/MobileNet_pointwise.jpg" height="260" width="480"> 
      </p>
5. 维度、参数计算  
  1. 下图为传统和MobileNet的结构对比。 MobileNet：input先经过Depthwise再经过1×1 conv(pointwise)，其output维度变化是 N×H×W×C-> N×H×W×C ->N×H×W×k，与传统一样。
<p align="center">
         <img src="image/mobilenet_v1.jpg" height="260" width="480"> 
      </p>
  2. 乘法次数(不是需计算的参数数量）对比,N=1时: 
    1. 传统： H×W×C×3×3×k
    2. MobileNet: Depthwise+Pointwise = H×W×C×(3×3+k)  (Depthwise: H×W×C×3×3; Pointwise: H×W×C×1×1×k) 
    3. MobileNet:传统 = (3×3+k): 3×3×k = (9+k)/9k

### ShuffleNet v1
1. Contribution: 
    
     



### ShuffleNet V1
