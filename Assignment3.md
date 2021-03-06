# Title: Analysis of Conventional RF Method with Census Data and Innovative RF Method with High-resolution Satellite Images in Sub-Saharan Poverty Assessment

## Name: Shiyun (Sunny) Shao
## Word Count:  1865
## Introduction

Poverty is one of the most important issues in human development: the state or condition in which a person or community lacks the financial resources and essentials for a minimum standard of living so that the basic human needs cannot be met is the foundation to development. Basic freedom to satisfy basic needs like food, water, and clothing are restricted in this case so that further development on account of expanding substantive freedom would not be achieved. Poverty in Sub-Saharan Africa is particularly related to the epidemics of disease including malaria, cholera, Aids, and high infant death rates, and a lowering of the overall living standards. The long-lasting unsolved feature of the internally generated problem that involves rich interaction between a large number of adaptive agents that are co-evolving indicates the inherent and complex nature of poverty issue in Sub-Saharan Africa. 

## Problem Statement

Different poverty assessments based on different focuses, variables, and indicators would employ diverse types of models to estimate poverty, leading to various policy actions and results to social development. Random Forests is part of the Machine Learning techniques, which has been applied for predictions in a wide range of research fields; however, the employment of RF in poverty prediction is uncommon. In fact, RF overcomes the drawbacks associated with single decision trees while maintaining its benefits. Research illustrates the idea that conventional poverty assessments with the base of census data (DHS) are still fundamental and essential (Bersisa & Heshmati, 2021); innovative high-resolution satellite methods represented by improved Random Forests Approach have the useful features of better prediction accuracies, higher prediction flexibilities, and fast speed. Although the studies build comparison between conventional and innovative measures, and indicate the benefits as well as insufficiencies of both methods, none of them clarified the best respective proportion recommended to employ census-based and innovative methodologies under the respective circumstances of different regions. Therefore, the literature gap appeared in the research, leading to my research question on the methodological system to balance the application of conventional micro-census measures and innovative geospatial measures to increase accuracy and flexibility in poverty assessment not only in the Sub-Saharan African countries without census abundance, but also in other countries in different regions with census available. 


## 1.	Brief Description to the Random Forests Method

Random Forests models are an ensemble, nonparametric modeling approach that grows a “forest” of individual classification or regression trees and improves upon bagging by using the best of a random selection of predictors at each node in each tree (Stevens et al., 2015). RF consists of a number of decision trees; each tree contains a number of decision nodes. In each node of a decision tree, data are split according to how well a variable can predict poverty (Sohnesen, 2016). Leo Breiman is the first to formally introduce the random forests after the bagging method (RF draws random subsets of features for training the individual trees, while bagging provides each tree with the full set of features), which is a combination of models aiming at classification accuracy (Yiu, 2019). The ﬁnal RF predictor is formed by taking the average over all trees. The samples that are not used to grow the tree are called Out-Of-Bag (OOB) data. To estimate the model accuracy, RF gives an error of estimate called the OOB error by calculating the difference in the mean square errors between the OOB data and the data used to grow the regression trees (Horning, 2010): 

![OOB](https://user-images.githubusercontent.com/78276966/115969950-1e693c00-a572-11eb-9cc6-7877ea623335.png) (Li et al., 2018), where yi was response variables from OOB, yi_hat was predicted value of the RF model, σy^2_hat was variance of predicted values, and m is the number of OOB samples. 


### 1.1	Decision Trees with Census Based Data

Decision trees are predictive models that use a set of binary rules to calculate a target value. Two types of decision trees are classification trees and regression trees. 

![3](https://user-images.githubusercontent.com/78276966/115510181-fea3f080-a2b1-11eb-8bbe-548e82d9a495.png)
 (Okiabera, 2020)

Every tree provides a repeated partitioning of the subset of the data used to train the algorithm. Once a subset that is less heterogenous is reached, a classification is made. The predictor used in the final decision tree is one that has less heterogeneity (Okiabera, 2020). The Entropy of Heterogeneity or homogeneity in the whole classification problem, denoted by E, is measured as: 

![113](https://user-images.githubusercontent.com/78276966/115956209-14254e80-a52e-11eb-95fd-f3b3a8ae0545.png) (Okiabera, 2020), where p = the proportion of an event of interest. 


### 1.2	Decision Trees with Satellite Images 

Decision trees are used to create categorical data sets such as land cover classification and regression trees are used to create continuous data sets such as biomass and percent tree cover. The tree is a set of binary decisions and terminal nodes connected by branches. The tree continues to grow until all branches end with terminal nodes (Horning, 2010). 

![120](https://user-images.githubusercontent.com/78276966/115956263-73835e80-a52e-11eb-8a44-c17db06eeaf2.png)
Figure 1: A classification tree and the resulting land cover map (Horning, 2010)


Figure 1 shows a decision tree and the resulting land cover map using the red (band 3) and near-infrared (band 4) bands from the Landsat Enhanced Thematic Mapper Plus satellite sensor as the predictor variables. 

![121](https://user-images.githubusercontent.com/78276966/115956279-85650180-a52e-11eb-8491-240e64d758f2.png)
(Horning, 2010)

When several predictor variables are used the tree and the resulting partitioning of the feature space would be significantly more complex with many more rectangles. Using categorical data, such as soil type, as a predictor variable would also result in a more complex feature space plot. Meanwhile, when the tree grows too large with the terminal nodes representing very small subsets of the training data, the model tends to overfit (Horning, 2010). Therefore, the disadvantages of decision trees are that rectangles are rarely an effective way to partition feature space, and the overfit feature of gives poor results to application in the full data set. 


## 2.	Random Forests Algorithm in Poverty Assessment

### 2.1 Random Forests Algorithm with Census Data Base

The steps to construct the tress for the random forests could be concluded to three. First, for each b = 1, …, B, a random sample of observations, n is drawn from the training data set, and subsequent bootstrap samples for other trees are taken (Okiabera, 2020). Second, a subset of m variables much less than the total number of variables in the dataset in addition to the bootstrap samples is randomly selected. At the same time, with the use of the Gini score, the best split is determined. Third, the out-of-bag (OOB) prediction is obtained through a majority vote across trees whose observation was not included in the bootstrap sample (Thoplan, 2014). The steps for classification trees are repeated until terminal node size is reached. The final set is then assigned a class in the case of poor or rich, or in the presence of more levels of the outcome variable including poorest, poorer, middle, richer, and richest, which is based on a majority vote; the proportion which has majority of observations in that set (Okiabera, 2020).

![1](https://user-images.githubusercontent.com/78276966/115510175-fba90000-a2b1-11eb-829d-0096d4f45bc7.jpg)

![2](https://user-images.githubusercontent.com/78276966/115510177-fd72c380-a2b1-11eb-9317-810b0109b8ce.jpg)

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

In Okiabera’s article, the dataset to analyze the critical determinants of poverty is from the 2014 Demographic and Health Surveys (DHS) in Kenya. The first procedure before applying the random forests algorithm is to remove incomplete cases and eliminate unnecessary variables from the dataset to a smaller dataset (Thoplan, 2014). Variables like “age at marriage”, “employment status” and “length of service” have been removed from the new dataset due to a very high proportion of missing values. The resulting variables taken into analysis include Sex of head of household, Age of head of household, Marital Status, Highest educational level attained, Type of place of residence, Region, and Number of household members (Okiabera, 2020). After the necessary data pre-processing is applied, an indicator (outcome) variable named N_Poverty is defined to be Poor as income < 2800, and Not Poor as income >= 2800. 


### 2.2 The Random Forests Algorithm with the Use of Remote Sensing and Geospatial Data

![111](https://user-images.githubusercontent.com/78276966/115956405-1340ec80-a52f-11eb-86e2-8139bb672f47.png)
(Kouwenhoven, 2019)

In the field of poverty and population mapping, two forms of data are generally used: remote sensing data like satellite imagery, land cover, nighttime light and geospatial data like road networks, population densities, built up area (Stevens et al., 2015). The point of interest data has demonstrated promising results in recent studies, indicating that it is a valuable asset in population or poverty mapping. A POI is an item of particular interest to some individual, on a map represented by a point, which include schools, hospitals and government buildings. In Kouwenhoven’s study, land use data from MODIS was selected as the category remote sensing data, while satellite data was used indirectly, since the land use data published by MODIS is based on satellite imagery. OpenStreetMap (OSM) was used as the source of POI data, allowing any internet user around the world to add information related to familiar localities (Kouwenhoven, 2019). In the study by Stevens et al., population distribution is often highly correlated with land cover types. They incorporate land cover information using one of two thematic land cover classification data sets. The GeoCover dataset provides consistent global mapping of 13 land cover classes at a 30-meter spatial resolution. GlobCover data, which are derived from the ENVISAT satellite mission's MERIS (Medium Resolution Image Spectrometer) imagery, were used for Kenya poverty assessment. 

From the category of POI data, variables like POI_Density and Distance-to-POI are included. From the second category of spatial data, variables related to infrastructure networks, specifically the road, highway, provincial road and canal networks, are distance_to_road, distance_to_highway, distance_to_provincial_road and distance_to_canal, representing the distance from each cell centroid to the nearest element of these networks (Kouwenhoven, 2019). 

The python-based sklearn library that provides a RandomForestRegressor package builds estimation of the data and fitting of the model. In poverty assessment and prediction, a regressor is used due to the continuous nature of the dependent variable (Kouwenhoven, 2019). All variables were included initially; then the least important variable at each iteration were removed from the model. If the OOB error of the model increased, the variable is added back to the model. The process is repeated until no further improvement was observed on removal of variables (Zhao, et al., 2019).

![python code](https://user-images.githubusercontent.com/78276966/115970534-8a00d880-a575-11eb-9d10-2f720cb76abb.png)
(Kouwenhoven, 2019)

## 3.	Results
### 3.1 Research Results from Census-based RF Poverty Assessment 

The results (Okiabera, 2020) showed that variables had a very small percentage of missingness inside the model. There was elimination in error of the classifier as the trees in the classification was increased. By considering Mean Decrease in Gini, from high to low, the variables in descending order of importance are the highest education level attained, type of place of residence, region, age of household head, number of household members, marital status, and sex of the household head. The RF classification was improved on the poorest and richest classes (the extreme ends of the wealth index), while the middle, poorer and richer indices were not as accurately classified. RF builds a significant improvement among classical regression techniques: the multiclass classification issue was comprehensively considered inside the analysis, and the poverty status as the out-of-bag error is low overall when more trees are added in the forest (Thoplan, 2014). Although the model accuracy was presented as 47.73% in the first place, within the help of the confusion matrix for all classes with the calculation of Accuracy, Error rate, Specificity, and Sensitivity, researchers could then build a better understanding to the process of classification for each class (Okiabera, 2020). 

![9](https://user-images.githubusercontent.com/78276966/115512059-21cf9f80-a2b4-11eb-89d7-21928e58820d.png)
(Okiabera, 2020)

Meanwhile, restricting RF predictions to a limited set of variables also illustrates a realistic setting in which poverty is tracked with smaller surveys that only collects data on a limited number of aspects. However, there is no loss of accuracy in predicting poverty using the restricted model with smaller number of variables compared to the full model without restrictions (the variations between the full and restricted models are small). Hence, the RF approach also predicts poverty accurately using only a small model, and can therefore be a real alternative for tracking of poverty with predictions (Stevens et al., 2015). 

### 3.2 Research Results from Remote Sensing and Geospatial Data-based Poverty Assessment 

The Random Forest model performs substantially better than several other commonly used, freely available approaches for dasymetric mapping at country-level scales. An assessment of which of the ancillary data covariates are important for accurately estimating population density at the census unit level is produced by the Random Forest algorithm. For Kenya, distance to health facility is by far the most important predictor for reducing the amount of variability. This indicates that this ancillary dataset is extremely valuable, even more than the distance-to-built land cover which is typically extremely important (Stevens et al., 2015).  

![114](https://user-images.githubusercontent.com/78276966/115956464-5bf8a580-a52f-11eb-992d-29e83014b7d2.png)
(Stevens et al., 2015)

The plot that reveals the relationship between the Observed census counts plotted from the finer census administrative units and the summed grid cell values from the population map estimated using coarser administrative units for Kenya shows that the RF methodology presents comparably accurate prediction for observed census values larger than zero. However, there may still be some refinement possible to better predict when census units include low or zero counts (Stevens et al. 2015).


### 3.3 Compare and Contrast on Accuracy

The R^2 values of the traditional census-based RF model without the use of Google satellite images are 0.55, 0.58, 0.66, 0.69, and 0.75 for five countries in Africa, while the RF model with high-resolution satellite images database is 0.70, indicating that the RF model using satellite images is more efficient and accurate than the conventional census-based RF model. 


## Conclusion 

In the absence of poverty survey data from Sub-Saharan Africa, remote sensing data and road maps that can reflect some of the environmental characteristics that are associated with poverty provides reliable data for poverty estimation. By integrating multi-source data like land cover map, OSM road map, and Google satellite imagery with the RF model at 5km x 5km resolution, we are able to identify variables representing poverty dimensions of POI and geospatial categories. Following a vigorous variable selection procedure with RF algorithm, variables were selected to offer the best predictive ability, iterating the training of the RF model. With the accuracy confirmation procedure, the improved RF model presents a high overall accuracy of poverty estimation. Compared with the conventional census-based RF model with an average R^2 of 0.66, innovative RF model with high-resolution satellite images database provided higher accuracy rate to poverty assessment. 


## Reflections on the Literature Gap

Although the studies build comparison between conventional and innovative measures, and indicate the benefits as well as insufficiencies of both methods, none of them clarified the best respective proportion recommended to employ census-based and innovative methodologies under the respective circumstances of different regions. Therefore, the literature gap appeared in the research, leading to my research question on the methodological system to balance the application of conventional RF method with census data and innovative RF method with high-resolution satellite images not only in the Sub-Saharan African poverty assessment without census abundance, but also in other regions with census available.





## Reference

1.	Horning, N. (2010). Random Forests: An algorithm for image classification and generation of continuous fields data sets. Retrieved from https://www.semanticscholar.org/paper/Random-Forests-:-An-algorithm-for-image-and-of-data-Horning/9484240b4dfe10a40b80037d6869c4b035615be9

2. Kouwenhoven, L. (2019). Poverty Distribution Mapping Using a Random Forest Algorithm: A Case Study of the Mekong River Delta. Retrieved from https://spinlab.vu.nl/wp-content/uploads/2019/06/Kouwenhoven_L.pdf

3.	Li, K., Chen, Y., Li, Y. (2018). The Random Forest-Based Method of Fine-Resolution Population Spatialization by Using the International Space Station Nighttime Photography and Social Sensing Data. Remote Sens. 2018, 10(10), 1650; https://doi.org/10.3390/rs10101650

4. Okiabera, Joel O. (2020). Using random forest (RF) to identify key determinants of poverty in Kenya. -College of Biological and Physical Sciences (CBPS) [3614] http://erepository.uonbi.ac.ke/handle/11295/154190

5.	Stevens, F.R., Gaughan, A.E., Linard,C. & Tatem, A.J. (2015). Disaggregating Census Data for Population Mapping Using Random Forests with Remotely-Sensed and Ancillary Data. PLoS ONE 10 (2): e0107042. doi:10.1371/journal.pone.0107042

6.	Sohnesen, T.P. & Stender,N. (2016). Is random forest a superior methodology for predicting poverty? an empirical assessment (English). Policy Research working paper;no. WPS 7612 Washington, D.C. : World Bank Group. http://documents.worldbank.org/curated/en/777401467987858907/Is-random-forest-a-superior-methodology-for-predicting-poverty-an-empirical-assessment

7.	Thoplan, Ruben. (2014). Random Forests for Poverty Classification. International Journal of Sciences: Basic and Applied Research (IJSBAR). 17. 252-259.

8.	Yiu, T. (2019). Understanding Random Forest. Retrieved from 
https://towardsdatascience.com/understanding-random-forest-58381e0602d2

9.	Zhao, X., Yu, B., Liu, Y. & Chen, Z. (2019). Estimation of Poverty Using Random Forest Regression with Multi-Source Data: A Case Study in Bangladesh. Remote Sens. 2019, 11(4), 375; https://doi.org/10.3390/rs11040375
