## Reference: 
  1. [Beyond Accuracy: Precision and Recall](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c)
  2. [Tag: average precision](https://sanchom.wordpress.com/tag/average-precision/)
## Questions:
  1. What's the threshold for?

### Understanding of [reference 1](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c)
  1. Choosing the right matrics for your tasks  
    1. _Why is important? Here is a example:_ simply label every single person flying from a US airport as not a terrorist. Given the 800 million average passengers on US flights per year and the 19 (confirmed) terrorists who boarded US flights from 2000–2017, this model achieves an astounding accuracy of 99.9999999%! __But the US Department of the Homeland Security will not buy this model.__  
  2. __Imbalanced classification problem__: eg. The previous example. So we should focus on identifying the __positive__ case.  
  3. Precision and recall  
    1. Precision: 太高,可能会放过 真正的恐怖分子，----->响应里面有多少是对的  
      ![Precision](https://cdn-images-1.medium.com/max/2000/1*FKXzF6DYSP2mV4HUBftRgg.png)
    2. __Recall__:太高，可能会错怪 innocent individuals， but maybe it will suffer _low precision:(if we label all individuals as terrorists, then our recall goes to 1.0!)_  
      ![Recall](https://cdn-images-1.medium.com/max/2000/1*gscG4JdjnyU5QkqNDqBg_w.png)  
    3. There is a trade-off in the metrics we choose to maximize -- Precision and recall (eg. when we increase the recall, we decrease the precision)  
          <p align="center">  
         <img src="https://cdn-images-1.medium.com/max/1000/0*XEO3pwAee7tBT_D1.png" height="300" width="400">   
          </p>  
    4. Combining Precision and Recall  
      1. F1 score: the __harmonic mean__ (调和平均值)of precision and recall taking both metrics into account.     
          [Quiz: Why use the harmonic mean instead of a simple average](https://stackoverflow.com/questions/26355942/why-is-the-f-measure-a-harmonic-mean-and-not-an-arithmetic-mean-of-the-precision)  
          ![The F1 score](https://cdn-images-1.medium.com/max/1000/1*UJxVqLnbSj42eRhasKeLOA.png)  
          
  2. __Visualizing__ Precision and Recall    
    1. Confusion Matrix    
      <p align="center">  
         <img src="https://cdn-images-1.medium.com/max/1000/1*CPnO_bcdbE8FXTejQiV2dg.png" height="300" width="580"> 
          </p>    
    2. ROC (Receiver Operating Characteristic) curve    
      1. Shows how the recall and precision relationshop changes as we vary the threshold for identifying a positive sample. 我们如何定义positive sample对 precision 和 recall 的影响          
      2. An ROC curve plots __the true positive rate(TPR)(recall)__ on the y-axis versus __the false positive rate(FPR)__ on the x-axis. A typical ROC curve is shown below,  
         <p align="center">  
         <img src="https://cdn-images-1.medium.com/max/1000/0*2iHR8dFXev5GWo_f.png>   
          </p>    
        The Ramdom Classifer: Black diagonal line  
      3. AUC (Area Under the Curvegeini)  
        1. quantify a model’s ROC curve by calculating the AUC: a metric which falls between 0 and 1 with a __higher__ number indicating __better__ classification performance  
        2. A random classifier (the black line) achieves an AUC of 0.5.   
          
### Understanding of [reference 2: Average precision](https://sanchom.wordpress.com/tag/average-precision/)  
  1. Evaluation of an information retrieval system (a search engine, for example) generally focuses on two things:    
    1. How relevant are the retrieved(检索) results? (precision) -----> 响应里面有多少是对的    
    2. Did the system retrieve many of the truly relevant documents? (recall）------> 正样本有多少被响应了    
  2. 如何分辨一个好的clssifer是好是坏？  
    1. 使用precision-recall curves: A poor classifier will have to take a large hit in precision to get higher recall（提高precision时，recall下降的厉害，则classifer不好，反之亦然);   
  3. Average Precision  
    1. Rather than comparing curves, its sometimes useful to have a single number that characterizes the performance of a classifier. (与其使用曲线，不如使用一个数值来表达classifer的好坏)
      1. AP(Average Precision):strictily,the average precision is precision averaged across all values of recall between 0 and 1:(AP严格意义上来说是在recall:[0,1]范围下,precision的平均值)  
      2. IAP(Interpolated Average Precision):插值平均精度，比如the PASCAL Visual Objects Challenge使用IAP(虽然它们称为AP)
        1. [博客：Pascal VOC 数据集介绍](https://blog.csdn.net/weixin_35653315/article/details/71028523)中提到：
        <p align="center">  
         <img src=/image/presion_and_recall_matrixs_blog1.png>   
          </p> 
## BDD dataset
  tretre
## VOC dataset
  retr
## Cityscape dataset
  tergter
 
