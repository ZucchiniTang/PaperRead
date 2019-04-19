## Reference
  1. 知乎：轻量化网络ShuffleNet MobileNet v1/v2 解析（https://zhuanlan.zhihu.com/p/35405071）
  
## 摘录
  1. 在实际应用中CNN应用受限于硬件与存储, 如不能在无人机上挂几张Nvidia Titan Xp. (Ref 1)

## 细说 (MobileNet V1 -> ShuffleNet v1 -> MobileNet v2 -> ShuffleNet v2)
### Group convolution
1. What is Group Convolution?
### MobileNet V1
1. 用Depthwish+Pointwise代替传统卷积，输出维度相同，计算量减少。
2. 传统卷积 
<p align="center">
         <img src="image/CNN_kernel.jpg" height="250" width="480"> 
      </p>
3. Depthwise
<p align="center">
         <img src="image/MobileNet_depthwise.jpg" height="250" width="480"> 
      </p>
4. Pointwise
<p align="center">
         <img src="image/MobileNet_pointwise.jpg" height="260" width="480"> 
      </p>
5. 维度、参数计算
### ShuffleNet V1
