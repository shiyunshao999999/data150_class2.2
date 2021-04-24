# Title: Analysis of Traditional RF Method with Census Data and Innovative RF method with High-resolution Satellite Images in Poverty Assessment

## Name: Shiyun (Sunny) Shao
## Word Count:  
## Introduction

Poverty is one of the most important issues in human development: the state or condition in which a person or community lacks the financial resources and essentials for a minimum standard of living so that the basic human needs cannot be met is the foundation to development. Basic freedom to satisfy basic needs like food, water, and clothing are restricted in this case so that further development on account of expanding substantive freedom would not be achieved. Poverty in Sub-Saharan Africa is particularly related to the epidemics of disease including malaria, cholera, Aids, and high infant death rates, and a lowering of the overall living standards, which is partly due to the inept leadership of a number of governance institutions: the long-term running strategies suit the best interest of powerful elites, so that African American countries’ institutions are not an externally-provide factor of production like labor or capital but an internally generated result of the country’s policies. The long-lasting unsolved feature of the internally generated problem that involves rich interaction between a large number of adaptive agents that are co-evolving indicates the inherent and complex nature of poverty issue in Sub-Saharan Africa.

## Problem Statement

Research illustrates the idea that conventional uni- or multidimensional poverty assessments represented by Demographic and Health Surveys methodology with the base of census data are still fundamental and essential due to the long-term utilization and improvement (Bersisa & Heshmati, 2021); innovative high-resolution satellite methods represented by Random Forest Approach have the useful features to generate better prediction accuracies and higher prediction flexibilities within the increasing amount of available census data for single or multiple countries within a region. Although the studies build comparison between conventional and innovative measures, and indicate the benefits as well as insufficiencies of both methods, none of them clarified the best respective proportion recommended to employ census-based and innovative methodologies under the respective circumstances of different regions. Therefore, the literature gap appeared in the research, leading to my research question on the methodological system to balance the application of conventional micro-census measures and innovative geospatial measures to increase accuracy and flexibility in poverty assessment not only in the Sub-Saharan African countries without census abundance, but also in other countries in different regions with census available.

## Random Forests Classification and Regression


### 1.	Brief Description to the Random Forests Method

Random Forests models are an ensemble, nonparametric modeling approach that grows a “forest” of individual classification or regression trees and improves upon bagging by using the best of a random selection of predictors at each node in each tree (Stevens et al., 2015). RF consists of a number of decision trees; each tree contains a number of decision nodes. In each node of a decision tree, data are split according to how well a variable can predict poverty (Sohnesen, 2016). Leo Breiman is the first to formally introduce the random forests after the bagging method (RF draws random subsets of features for training the individual trees, while bagging provides each tree with the full set of features), which is a combination of models aiming at classification accuracy (Yiu, 2019). The ﬁnal RF predictor is formed by taking the average over all trees. The samples that are not used to grow the tree are called Out-Of-Bag (OOB) data. To estimate the model accuracy, RF gives an error of estimate called the OOB error by calculating the difference in the mean square errors between the OOB data and the data used to grow the regression trees (Horning, 2010). 

### 1.1	Decision Trees with Census Based Data

Decision trees are predictive models that use a set of binary rules to calculate a target value. Two types of decision trees are classification trees and regression trees. 
![3](https://user-images.githubusercontent.com/78276966/115510181-fea3f080-a2b1-11eb-8bbe-548e82d9a495.png)
 (Okiabera, 2020)

Every tree provides a repeated partitioning of the subset of the data used to train the algorithm. Once a subset that is less heterogenous is reached, a classification is made. The predictor used in the final decision tree is one that has less heterogeneity. The Entropy of Heterogeneity or homogeneity in the whole classification problem, denoted by E, is measured as: ![113](https://user-images.githubusercontent.com/78276966/115956209-14254e80-a52e-11eb-95fd-f3b3a8ae0545.png), where p = the proportion of an event of interest


### 1.2	Decision Trees with Satellite Images 

Decision trees are used to create categorical data sets such as land cover classification and regression trees are used to create continuous data sets such as biomass and percent tree cover. 
![120](https://user-images.githubusercontent.com/78276966/115956263-73835e80-a52e-11eb-8a44-c17db06eeaf2.png)
Figure 1: A classification tree and the resulting land cover map (Horning, 2010)


Figure 1 shows a decision tree and the resulting land cover map using the red (band 3) and near-infrared (band 4) bands from the Landsat Enhanced Thematic Mapper Plus satellite sensor as the predictor variables. The tree is a set of binary decisions and terminal nodes connected by branches. The top decision node (root node) evaluates the rule “is band 4 less than or equal to 46”. If it is then a terminal node is reached and that node is assigned to the class “water”. If band 4 is greater than 46 then another binary decision node is evaluated; “is band 3 less than or equal to 102”. The tree continues to grow until all branches end with terminal nodes (Horning, 2010). 

![121](https://user-images.githubusercontent.com/78276966/115956279-85650180-a52e-11eb-8491-240e64d758f2.png)
(Horning, 2010)

When several predictor variables are used the tree and the resulting partitioning of the feature space would be significantly more complex with many more rectangles. Using categorical data, such as soil type, as a predictor variable would also result in a more complex feature space plot. Meanwhile, when the tree grows too large with the terminal nodes representing very small subsets of the training data, the model tends to overfit (Horning, 2010). Therefore, the disadvantages of decision trees are that rectangles are rarely an effective way to partition feature space, and the overfit feature of gives poor results to application in the full data set. 

### 1.3 Random Forests as an advanced form of Decision Trees

RF is part of the Machine Learning techniques, which has been applied for predictions in a wide range of research fields; however, the employment of RF in poverty prediction is rare. In fact, RF overcomes the drawbacks associated with single decision trees while maintaining the benefits. The random forests model calculates a response variable (e.g., land cover, percent tree cover) by creating many (usually several hundred) different decision trees in the forest and then putting each object to be modeled down each of the decision trees as a multi-layered pixel. The response is then determined by evaluating the responses from all of the trees. RF is a powerful classification tool with many benefits: it runs fast, performs well in large feature setups, is effective for handling complex data structures without visible relationship (Okiabera, 2020), and is considered to have relatively high accuracy by providing a ranking of variable importance. In RF, each regression tree is constructed using a subset of training samples that is independently selected, with replacement from the original data set. For each node per tree, only a small subset of variables is randomly selected to determine the split. This strategy increases the diversity between trees to avoid over-ﬁtting and increases the robustness of the model (Zhao et al., 2019). In many cases the predictive performance for RF is on par with boosted regression trees but have the advantage of having fewer tuning parameters, which is an especially important feature since tuning can be automated as part of the fitting process (Sohnesen, 2016). 




### 2.	Random Forests Algorithm in poverty assessment

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


### 2.1 The Random Forests Algorithm with the Use of Remote Sensing and Geospatial Data
![111](https://user-images.githubusercontent.com/78276966/115956405-1340ec80-a52f-11eb-86e2-8139bb672f47.png)

In the field of poverty and population mapping, two forms of data are generally used: remote sensing (e.g. satellite imagery, land cover, nighttime light) data and geospatial (e.g. road networks, population densities, built up area) data (Stevens et al., 2015). The use point of interest data has demonstrated promising results in recent studies, indicating that it is a valuable asset in population or poverty mapping. A POI is an item of particular interest to some individual, on a map represented by a point. Examples of POIs include schools, hospitals and government buildings. In Kouwenhoven’s study, the category remote sensing data, land use data from MODIS was selected, while satellite data was used indirectly, since the land use data published by MODIS is based on satellite imagery. OpenStreetMap (OSM) was used as the source of POI data, allowing any internet user around the world to add information related to localities they are familiar with (Kouwenhoven, 2019). In the study by Stevens et al., population distribution is often highly correlated with land cover types. They incorporate land cover information using one of two thematic land cover classification data sets. The GeoCover dataset provides consistent global mapping of 13 land cover classes at a 30-meter spatial resolution. GlobCover data, which are derived from the ENVISAT satellite mission's MERIS (Medium Resolution Image Spectrometer) imagery, were used for Kenya poverty assessment. 

From the category of POI data, variables like POI_Density and Distance-to-POI are included. From the second category of spatial data, variables related to infrastructure networks, specifically the road, highway, provincial road and canal networks, are distance_to_road, distance_to_highway, distance_to_provincial_road and distance_to_canal, representing the distance from each cell centroid to the nearest element of these networks (Kouwenhoven, 2019). 

Fitting of the model and estimation of the data were performed using the python-based sklearn library, providing a RandomForestRegressor package. In poverty assessment and prediction, a regressor is used due to the continuous nature of the dependent variable (Kouwenhoven, 2019). We started the RFR model with all the variables and removed the least important variable at each iteration. If the OOB error of the model increased, we added this variable back to the model. We repeated this until no further improvement was observed on removal of variables (Zhao, et al., 2019).





### 3.	Results
### 3.1 Research Result from Census-based RF Poverty Assessment 

The results (Okiabera, 2020) showed that variables had a very small percentage of missingness inside the model. There was elimination in error of the classifier as the trees in the classification was increased. By considering Mean Decrease in Gini, from high to low, the variables in descending order of importance are the highest education level attained, type of place of residence, region, age of household head, number of household members, marital status, and sex of the household head. The RF classification was improved on the poorest and richest classes (the extreme ends of the wealth index), while the middle, poorer and richer indices were not as accurately classified. RF builds a significant improvement among classical regression techniques: the multiclass classification issue was comprehensively considered inside the analysis, and the poverty status as the out-of-bag error is low overall when more trees are added in the forest (Thoplan, 2014). Although the model accuracy was presented as 47.73% in the first place, within the help of the confusion matrix for all classes with the calculation of Accuracy, Error rate, Specificity, and Sensitivity, researchers could then build a better understanding to the process of classification for each class (Okiabera, 2020). 

![9](https://user-images.githubusercontent.com/78276966/115512059-21cf9f80-a2b4-11eb-89d7-21928e58820d.png)

Meanwhile, Restricting RF predictions to a limited set of variables also illustrates a realistic setting in which poverty is tracked with smaller surveys that only collects data on a limited number of aspects. However, there is no loss of accuracy in predicting poverty using the restricted model with smaller number of variables compared to the full model without restrictions (the variations between the full and restricted models are small). Hence, the RF approach also predicts poverty accurately using only a small model, and can therefore be a real alternative for tracking of poverty with predictions (Stevens et al., 2015). 

### 3.2 Research Result from Remote Sensing and Geospatial Data-based Poverty Assessment 

The Random Forest model performs substantially better than several other commonly used, freely available approaches for dasymetric mapping at country-level scales. An assessment of which of the ancillary data covariates are important for accurately estimating population density at the census unit level is produced by the Random Forest algorithm. For Kenya, distance to health facility is by far the most important predictor for reducing the amount of variability. This indicates that this ancillary dataset is extremely valuable, even more than the distance-to-built land cover which is typically extremely important (Stevens et al., 2015).  
![114](https://user-images.githubusercontent.com/78276966/115956464-5bf8a580-a52f-11eb-992d-29e83014b7d2.png)

The plot that reveals the relationship between the Observed census counts plotted from the finer census administrative units and the summed grid cell values from the population map estimated using coarser administrative units for Kenya shows that the RF methodology presents comparably accurate prediction for observed census values larger than zero. However, there may still be some refinement possible to better predict when census units include low or zero counts (Stevens et al. 2015).





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


