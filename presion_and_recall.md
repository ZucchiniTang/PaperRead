## reference: 
  1 .[Beyond Accuracy: Precision and Recall](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c)

### Understanding of [reference 1](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c)
  1. Choosing the right matrics for your tasks
      1. _Why is important? Here is a example:_ simply label every single person flying from a US airport as not a terrorist. Given the 800 million average passengers on US flights per year and the 19 (confirmed) terrorists who boarded US flights from 2000–2017, this model achieves an astounding accuracy of 99.9999999%! __But the US Department of the Homeland Security will not buy this model.__
      2. __Imbalanced classification problem__: eg. The previous example. So we should focus on identifying the __positive__ case.
      3. Precision and recall
          1. Precision:  太高，可能会错怪 innocent individuals
      ![Precision](https://cdn-images-1.medium.com/max/2000/1*FKXzF6DYSP2mV4HUBftRgg.png)
          2. __Recall__:太高,可能会放过 真正的恐怖分子， but maybe it will suffer _low precision:(if we label all individuals as terrorists, then our recall goes to 1.0!)_
      ![Recall](https://cdn-images-1.medium.com/max/2000/1*gscG4JdjnyU5QkqNDqBg_w.png)
          3. There is a trade-off in the metrics we choose to maximize -- Precision and recall (eg. when we increase the recall, we decrease the precision)
          <p align="center">
         <img src="https://cdn-images-1.medium.com/max/1000/0*XEO3pwAee7tBT_D1.png" height="300" width="400"> 
          </p>
      4. Combining Precision and Recall
 
