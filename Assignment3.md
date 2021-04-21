# Title: 

## Name: Shiyun (Sunny) Shao
## Word Count:  
## Introduction

Poverty is one of the most important issues in human development: the state or condition in which a person or community lacks the financial resources and essentials for a minimum standard of living so that the basic human needs cannot be met is the foundation to development. Basic freedom to satisfy basic needs like food, water, and clothing are restricted in this case so that further development on account of expanding substantive freedom would not be achieved. Poverty in Sub-Saharan Africa is particularly related to the epidemics of disease including malaria, cholera, Aids, and high infant death rates, and a lowering of the overall living standards, which is partly due to the inept leadership of a number of governance institutions: the long-term running strategies suit the best interest of powerful elites, so that African American countries’ institutions are not an externally-provide factor of production like labor or capital but an internally generated result of the country’s policies. The long-lasting unsolved feature of the internally generated problem that involves rich interaction between a large number of adaptive agents that are co-evolving indicates the inherent and complex nature of poverty issue in Sub-Saharan Africa.

## Problem Statement

Research illustrates the idea that conventional uni- or multidimensional poverty assessments represented by Demographic and Health Surveys methodology with the base of census data are still fundamental and essential due to the long-term utilization and improvement (Bersisa & Heshmati, 2021); innovative high-resolution satellite methods represented by Random Forest Approach have the useful features to generate better prediction accuracies and higher prediction flexibilities within the increasing amount of available census data for single or multiple countries within a region. Although the studies build comparison between conventional and innovative measures, and indicate the benefits as well as insufficiencies of both methods, none of them clarified the best respective proportion recommended to employ census-based and innovative methodologies under the respective circumstances of different regions. Therefore, the literature gap appeared in the research, leading to my research question on the methodological system to balance the application of conventional micro-census measures and innovative geospatial measures to increase accuracy and flexibility in poverty assessment not only in the Sub-Saharan African countries without census abundance, but also in other countries in different regions with census available.

## Random Forests Classification and Regression


### 1.	Brief Description to the Random Forests Method

Random Forests models are an ensemble, nonparametric modeling approach that grows a “forest” of individual classification or regression trees and improves upon bagging by using the best of a random selection of predictors at each node in each tree (Stevens et al., 2015). RF consists of a number of decision trees; each tree contains a number of decision nodes. In each node of a decision tree, data are split according to how well a variable can predict poverty (Sohnesen, 2016). Leo Breiman is the first to formally introduce the random forests after the bagging method (RF draws random subsets of features for training the individual trees, while bagging provides each tree with the full set of features), which is a combination of models aiming at classification accuracy (Yiu, 2019). RF is a powerful classification tool with many benefits: it runs fast, performs well in large feature setups, is effective for handling complex data structures without visible relationship (Okiabera, 2020), and is considered to have relatively high accuracy by providing a ranking of variable importance; Random forests do not over-fit because for large number of trees, the generalization error converges to a limiting value under the strong law of large number (Thoplan, 2014). The Random Forest method is part of the Machine Learning techniques, which has been applied for predictions in a wide range of research fields; however, the employment of RF in poverty prediction is rare. In many cases the predictive performance for Random Forests is on par with boosted regression trees but have the advantage of having fewer tuning parameters, which is an especially important feature since tuning can be automated as part of the fitting process (Sohnesen, 2016).


### 2.	Random Forests Algorithm in Poverty Assessment

The steps to construct the tress for the random forests could be concluded to three. First, for each b = 1, …, B, a random sample of observations, n is drawn from the training data set, and subsequent bootstrap samples for other trees are taken (Okiabera, 2020). Second, a subset of m variables much less than the total number of variables in the dataset in addition to the bootstrap samples is randomly selected. At the same time, with the use of the Gini score, the best split is determined. Third, the out-of-bag (OOB) prediction is obtained through a majority vote across trees whose observation was not included in the bootstrap sample (Thoplan, 2014). The steps for classification trees are repeated until terminal node size is reached. The final set is then assigned a class in the case of poor or rich, or in the presence of more levels of the outcome variable including poorest, poorer, middle, richer, and richest, which is based on a majority vote; the proportion which has majority of observations in that set (Okiabera, 2020).

![1](https://user-images.githubusercontent.com/78276966/115510175-fba90000-a2b1-11eb-829d-0096d4f45bc7.jpg)
![2](https://user-images.githubusercontent.com/78276966/115510177-fd72c380-a2b1-11eb-9317-810b0109b8ce.jpg)
![3](https://user-images.githubusercontent.com/78276966/115510181-fea3f080-a2b1-11eb-8bbe-548e82d9a495.png)

(Okiabera, 2020)

The output that the ensemble of decision trees made are denoted by TbB; the class predicted by the bth tree is denoted by Cˆb(x); the prediction is calculated by: 

![4](https://user-images.githubusercontent.com/78276966/115510184-006db400-a2b2-11eb-9330-30d951ac32ca.png)

(Okiabera, 2020), while a majority vote means that from a set of decision trees in the random forest, the mostly voted class is the final classification; 

the regression is calculated by:  

![5](https://user-images.githubusercontent.com/78276966/115510190-01064a80-a2b2-11eb-92e4-fcb10cde88ca.png)
(Okiabera, 2020), which represents the average class choice and the regression choice. 
To achieve the effect of the RF feature that provides a ranking of variable importance, evaluation of the importance of a variable should be calculated through a Mean Decrease Impurity. The variable with the largest decrease in impurity will be considered as the most important variable. This can be achieved through the Mean Decrease Gini (MDG) or the Mean Decrease Accuracy (MDA). The article Random Forests for Poverty Classification (Thoplan, 2014) mainly focused on the MDG as a measure of variable importance. The calculation of the mean decrease impurity measure is defined as: 

![6](https://user-images.githubusercontent.com/78276966/115510199-0368a480-a2b2-11eb-8035-c5bd3a9c20d0.png)

where Xm represents the mth variable, NT is the number of trees in the forest, v(St) is the variable at split St, p(t) is the proportion of records at node t out of the total number of records in the data, and ![7](https://user-images.githubusercontent.com/78276966/115510206-0499d180-a2b2-11eb-9637-be887e83a1b8.png) in which pL represents the number of records in the left child node of t out of the total number of records at node t, while the impurity measure i(t) is the Gini index, which is used to determine the branching of the decision trees right from the root nodes to the child nodes, and is represented as the following function for a node t: ![8](https://user-images.githubusercontent.com/78276966/115510212-05326800-a2b2-11eb-8c93-8bec9520d0c9.png)
with j = 1, 2 to represent poverty class. 

In Okiabera’s article, the dataset to analyze the critical determinants of poverty is from the 2014 Demographic and Health Surveys (DHS) in Kenya, while Thoplan’s study employed the dataset sourced from the Census data of Mauritius. The first procedure before applying the random forests algorithm is to remove incomplete cases and eliminate unnecessary variables from the dataset to a smaller dataset (Thoplan, 2014). Variables like “age at marriage”, “employment status” and “length of service” have been removed from the new dataset due to a very high proportion of missing values. The resulting variables taken into analysis include Sex of head of household, Age of head of household, Marital Status, Highest educational level attained, Type of place of residence, Region, and Number of household members (Okiabera, 2020). After the necessary data pre-processing is applied, an indicator (outcome) variable named N_Poverty is defined to be Poor as income < 2800, and Not Poor as income >= 2800. 


### 3.	Results

The results (Okiabera, 2020) showed that variables had a very small percentage of missingness inside the model. There was elimination in error of the classifier as the trees in the classification was increased. By considering Mean Decrease in Gini, from high to low, the variables in descending order of importance are the highest education level attained, type of place of residence, region, age of household head, number of household members, marital status, and sex of the household head. The RF classification was improved on the poorest and richest classes (the extreme ends of the wealth index), while the middle, poorer and richer indices were not as accurately classified. RF builds a significant improvement among classical regression techniques: the multiclass classification issue was comprehensively considered inside the analysis, and the poverty status as the out-of-bag error is low overall when more trees are added in the forest (Thoplan, 2014). Although the model accuracy was presented as 47.73% in the first place, within the help of the confusion matrix for all classes with the calculation of Accuracy, Error rate, Specificity, and Sensitivity, researchers could then build a better understanding to the process of classification for each class (Okiabera, 2020). 

![9](https://user-images.githubusercontent.com/78276966/115512059-21cf9f80-a2b4-11eb-89d7-21928e58820d.png)

Meanwhile, Restricting RF predictions to a limited set of variables also illustrates a realistic setting in which poverty is tracked with smaller surveys that only collects data on a limited number of aspects. However, there is no loss of accuracy in predicting poverty using the restricted model with smaller number of variables compared to the full model without restrictions (the variations between the full and restricted models are small). Hence, the RF approach also predicts poverty accurately using only a small model, and can therefore be a real alternative for tracking of poverty with predictions (Stevens et al., 2015). 

 
## Logistic Regression



## Reference

1.	Achia, T., Wangombe, A. & Khadioli, N. (2010). A Logistic Regression Model to Identify Key Determinants of Poverty Using Demographic and Health Survey Data. European Journal of Social Sciences – Volume 13, Number 1 (2010)
http://erepository.uonbi.ac.ke/handle/11295/38629

1.	Okiabera, Joel O. (2020). Using random forest (RF) to identify key determinants of poverty in Kenya. -College of Biological and Physical Sciences (CBPS) [3614] http://erepository.uonbi.ac.ke/handle/11295/154190

2.	Stevens, F.R., Gaughan, A.E., Linard,C. & Tatem, A.J. (2015). Disaggregating Census Data for Population Mapping Using Random Forests with Remotely-Sensed and Ancillary Data. PLoS ONE 10 (2): e0107042.
doi:10.1371/journal.pone.0107042

3.	Sohnesen, T.P. & Stender,N. (2016). Is random forest a superior methodology for predicting poverty? an empirical assessment (English). Policy Research working paper;no. WPS 7612 Washington, D.C. : World Bank Group. http://documents.worldbank.org/curated/en/777401467987858907/Is-random-forest-a-superior-methodology-for-predicting-poverty-an-empirical-assessment

4.	Thoplan, Ruben. (2014). Random Forests for Poverty Classification. International Journal of Sciences: Basic and Applied Research (IJSBAR). 17. 252-259.

5.	Yiu, T. (2019). Understanding Random Forest. Retrieved from
https://towardsdatascience.com/understanding-random-forest-58381e0602d2


