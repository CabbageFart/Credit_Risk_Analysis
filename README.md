# **Credit_Risk_Analysis**
![image](https://user-images.githubusercontent.com/111661058/232156344-818001b6-71fb-4a43-a63b-4bee110d63b2.png)
# Purpose
 We are trying to access the inherent risk involved in the approval of Credit applications. We are going to try and identify the algorithm that best predicts the low and high risk candidates. Whether someone is low risk or high risk involves a rather large amount of data and wouldn’t be to difficult to predic on a one by one basis. But we are going to be looking at several thousand people at a time. So our algorithms will need be as precise as possible.
# Results
  * Essentially, we have two classes we are trying to predict.
      * Low-Risk
      * High-Risk
  * We will be using 4 different methods
      * Over sampling<BR>
            We increase the size of the **smaller** class to get closer to the size of the larger class.<BR>
      * Under sampling<BR>
            We decrease the size of the **larger** class to get closer to the size of the smaller class.<BR>
      * Over and Under sampling<BR>
            This takes aspects of both. After the model over samples it then removes outliers from both classes in order to significantly remove any over lap of data                 points.<BR>
      * Ensemble Classifiers<BR>
             Techniques that aim at improving the accuracy of results in models by combining multiple models instead of using a single model.<BR>
   * From those methods we will be looking at 3 scores
      * Accuracy Score
      * Precision Score(pre)
      * Recall Score(rec)
      

## `Over Sampling`
  * ### RandomOverSampler
**Accuracy** 65%<BR>
![image](https://user-images.githubusercontent.com/111661058/232172075-14b1a008-927b-4624-92a4-54bab34f3793.png)<BR>
      * High risk precision at .1% and recall at 61%
  * ### SMOTE
**Accuracy** 62%<BR>
![image](https://user-images.githubusercontent.com/111661058/232172086-0047dca2-3f4d-4b79-ac4b-9080b89e0fda.png)<BR>
      * High risk precision at .1% and recall at 61%<BR>
    **Over sampling had very low scores when predicitng high risk**
## `Under Sampling`
  * ### ClusterCentroids
**Accuracy** 52%<BR>
![image](https://user-images.githubusercontent.com/111661058/232172040-c3ed785f-6789-444a-b210-2955b02c81bd.png)<BR>
      * High risk precision at .1% and recall at 60%<BR>
      * Low risk recall of 44%<BR>
    **Under sampling also had a very bad score for predicting high risk. As well as a worse recall score for predicining low risk**
## `Over and Under Sampling`
  * ### SMOTEENN
**Accuracy** 64%<BR>
![image](https://user-images.githubusercontent.com/111661058/232172110-b34b2216-54f3-41fe-862c-11231d64d576.png)<BR>
      * High risk precision at .1% and recall at 70%<BR>
    **A nice improvemnt on the recall score from the previous models**
## `Ensemble Classifiers`

  * ### BalancedRandomForestClassifier
**Accuracy** 79%<BR>
![image](https://user-images.githubusercontent.com/111661058/232172300-9dec9232-ff2e-4ab6-a427-14a7a355befa.png)<BR>
      * High risk precision at .3% and recall at 70%<BR>
    **For the first time we actually see some movement on the precision score. But still not good enough**
  * ### EasyEnsembleClassifier
**Accuracy** 93%<BR>
![image](https://user-images.githubusercontent.com/111661058/232172338-231c7d28-73da-43cc-9754-0cd1e744913e.png)<BR>
      * High risk precision at .9% and recall at 92%<BR>
    **Here we see some reall promise on a model to use**
# Summary
Models | HR pre |HR rec|acc                               
--- |--- | --- | ---
RandomOverSampler |  1% |   61%  |  65%    
SMOTE |  1% |   61%  |  62%                
ClusterCentroids | 1%  |   60%  |  52%    
SMOTEENN|  1%  |  70%  |  64%             
BalancedRandomForestClassifier |3%| 70%|79%
EasyEnsembleClassifier |9%| 92% |93%

As you can see the only viable model here is the EasyEnsembleClassifier. It far outperformed the other models. Yet I still would not recommend using this model as it is. With less than a 95% recall and accuracy rate you will still have more than an acceptable amount of bad loans being made. I would however try to build on this model to see if less features being considered or another feature that wasn't in the original dataset can be added.
