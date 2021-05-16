# Title: Balance Conventional Census-Based Measures and Innovative High-Resolution Satellite-Based Measures in Poverty Assessment Using Random Forest Approach: A Case Study in Kenya
## Name: Shiyun (Sunny) Shao
## Word Count: 3066
 
## 1.	Introduction

Poverty is one of the most important issues in human development: the state or condition in which a person or community lacks the financial resources and essentials for a minimum standard of living so that the basic human needs cannot be met is the foundation to development. Basic freedom to satisfy basic needs like food, water, and clothing are restricted in this case so that further development on account of expanding substantive freedom would not be achieved. Poverty in Sub-Saharan Africa is particularly related to the epidemics of disease including malaria, cholera, Aids, and high infant death rates, and a lowering of the overall living standards, which is partly due to the inept leadership of a number of governance institutions: the long-term running strategies suit the best interest of powerful elites, so that African American countries’ institutions are not an externally-provide factor of production like labor or capital but an internally generated result of the country’s policies. The long-lasting unsolved feature of the internally generated problem that involves rich interaction between a large number of adaptive agents that are co-evolving indicates the inherent and complex nature of poverty in Sub-Saharan Africa.
 
### 1.1 Literature Gap
 
Different poverty assessments based on different focuses, variables, and indicators would employ diverse types of models to estimate poverty, leading to various policy actions and results to social development. Random Forests is part of the Machine Learning techniques, which has been applied for predictions in a wide range of research fields; however, the employment of RF in poverty prediction is uncommon. In fact, RF overcomes the drawbacks associated with single decision trees while maintaining its benefits. Research illustrates the idea that conventional poverty assessments with the base of census data like DHS are still fundamental and essential due to the long-term utilization and improvement (Bersisa & Heshmati, 2021); innovative high-resolution satellite methods represented by improved Random Forest Approach have the useful features of better prediction accuracies, higher prediction flexibilities, and fast speed. Current research is limited in using either census data or environmental data from different sources in isolation to estimate poverty despite the fact that poverty is a complex phenomenon that cannot be quantified either theoretically or practically by one single data type. Although the studies build comparison between conventional and innovative measures, and indicate the benefits as well as insufficiencies of both methods, none of them clarified the best respective proportion recommended to employ census-based and innovative methodologies under the respective circumstances of different regions, which is the literature gap that appeared in the research.
 
 
### 1.2 Research Question
 
With the use of Random Forests method, both conventional and improved in poverty estimation, I need to develop a research plan to balance the application of conventional census measures and innovative geospatial measures to increase accuracy and flexibility in poverty assessment not only in the Sub-Saharan African countries without census abundance, but also in other countries in different regions with census available.
 
 
### 1.3 Research Plan
 
My research plan is aimed at conducting a random forest classification and regression model to assess and estimate poverty on a 5 spatial kilometer resolution by combining features extracted from multiple data sources. The National Polar-orbiting Partnership Visible Infrared Imaging Radiometer Suite (NPP-VIIRS) Day/Night Band (DNB) and nighttime light (NTL) data, the Moderate Resolution Imaging Spectroradiometer (MODIS) land use data and land cover map, and OpenStreetMap as the source of Point-of-Interest data are multiple data sources from innovative high-resolution geospatial and POI datasets for estimated wealth index, while the household wealth index (WI) drawn from the Demographic and Health Surveys (DHS) program was used to reflect poverty level. I will train the Random Forest model using data in Kenya, running the RF Classification algorithm first to classify and select variables through the ranking of importance, and putting the selected variables in the RF Regression algorithm to obtain an estimated wealth index. I will then apply the model to both other countries in Sub-Saharan Africa including Ethiopia, Somalia, Uganda, and Rwanda, and developing countries or regions other than Sub-Saharan Africa including Bangladesh, Nepal, and the Mekong River Delta region in Vietnam to evaluate the model’s accuracy and replicability. After the cross-sectional comparison between the output of different countries to the model, time-series comparison of systematic tracking after government regulations on the change of variable inputs would be made to quantitatively analyze the influence of government policies on poverty reduction.
 
 
 
## 2.  Hypothesis
 
### 2.1  Hypothesis on Accuracy Evaluation of the Proposed RF Model
 
H0: the adjusted R^2 value between the actual and estimated WI in Kenya < 0.50
 
HA: the adjusted R^2 value between the actual and estimated WI in Kenya >= 0.50
 
 
### 2.2  Accuracy Evaluation Compared with District-Level Census Data
 
H0: the r value between the estimated WI at grid-level and the estimated WI at the district-level ∈ [-1,0]
 
HA: the r value between the estimated WI at grid-level and the estimated WI at the district-level ∈ [0,1]
 
 
### 2.3  Replicability of the Model in Different Geographical Context
 
#### 2.3.1   	Replicability of the Model in Other Countries in Sub-Saharan Africa
 
H0: the adjusted R^2 value between the actual and estimated WI with the change of variable inputs in Ethiopia, Somalia, Uganda, and Rwanda < 0.50
 
HA: the adjusted R^2 value between the actual and estimated WI with the change of variable inputs in Ethiopia, Somalia, Uganda, and Rwanda >= 0.50
 
 
#### 2.3.2   	Replicability of the Model in Countries other than Sub-Saharan Africa
 
H0: the adjusted R^2 value between the actual and estimated WI with the change of variable inputs in Bangladesh, Nepal, and the Mekong River Delta region in Vietnam < 0.50
 
HA: the adjusted R^2 value between the actual and estimated WI with the change of variable inputs in Bangladesh, Nepal, and the Mekong River Delta region in Vietnam >= 0.50
 
 
### 2.4 Systematic tracking after government regulations on the change of variable inputs
 
H0: the estimated WI after government regulations - the estimated WI before government regulations = 0
 
HA: the estimated WI after government regulations - the estimated WI before government regulations ≠ 0
 
 
 
## 3.  Materials and Methods
 
### 3.1 Data
 
Geospatial data like road networks, population densities, built up area, and remote sensing data like satellite imagery, land cover, nighttime light (Stevens et al., 2015) will be considered as major datasets in high-resolution satellite dataset selections. A Point-of-interest is an item of particular interest to some individual, on a map represented by a point, which include geospatial institutional buildings like schools, hospitals and government buildings. OpenStreetMap will be used as the source of Point-of-Interest data. Land use data from MODIS will be selected, while satellite data will be used indirectly in this case, since the land use data published by MODIS is based on satellite imagery. Dataset like WISDOM could present detailed depiction about the structure and texture features of the landscape. Explanatory Variables corresponding to Point-of-Interest data included in the model will be POI Density, Distance to POI, and the ones from spatial data category will be multiple categories of land cover from the MODIS land use data, and the variables of structure and texture features of the landscape like roads, highways, provincial roads from WISDOM.
 
Demographic and Health Surveys (DHS) and Living Standards Measurement Study data gathered by second-level administration will be used to extract the Wealth Index (WI) as the response variable of the proposed Random Forest poverty estimation model. Census data is aggregated using census household weights to construct representative district averages. WI is computed as the first major component of household’s ownership of selected assets including housing construction materials, water access and sanitation facilities, types of transportation tools, combined with variables including type of residential place and region, sex and age and marital status of head of household into consideration, which has been used as a reflection of household poverty level in conventional census-based studies. The WI value is an integer ranging from 1 to 5, indicating the lowest, second, middle, fourth, and the highest asset levels. The DHS provides WI for each household participating in the survey: it calculates and presents the average latitude and longitude of the groupings of households known as household clusters rather than specific household locations, with an addition to 5 km positional errors in each direction for the data collection that preserves the anonymity of survey respondents.
 
 
 
### 3.2 Methods


![flowchart of research plan](https://user-images.githubusercontent.com/78276966/118393403-868ed780-b671-11eb-8082-37dbc7813fb5.jpg)

First, I will select multiple high-resolution satellite image datasets corresponding to various features and the census survey dataset DHS to extract the Wealth Index as the response variable. Second, I will use the features from Satellite Image datasets as explanatory variables: other than categories of spatial and POI data, I will include the Night-time Light data and daily DNB data to extract socioeconomic variables; from the MODIS dataset and Land Cover Map representing the spatial data, I will extract structure and texture features of the Landscape as variables; and accessibility variables will be sourced from the OpenStreetMap. All these combined to be the explanatory variables input in the Variable Classification and Selection. I will then generate a 5 by 5 kilometer grid centered at each cluster location to ensure that the true location falls within the grid. This grid is then used as the basic unit of analysis of features extracted. After iterating the process of classification, the ranking of variables’ importance is presented and the less important ones are removed from the model. From the python-based library, the RandomForestRegressor package will be employed to build estimation of the data and fitting of the model. At first, all variables are included; then the least important variable at each iteration will be removed from the model. If the Out of Bag error of the model increases, the variable is added back to the model. The process is repeated until no further improvement was observed on removal of variables (Zhao, et al., 2019). During the accuracy evaluation process, the function GridSearchCV, which iterates over a range of potential values and returns those with the highest R squared score, will be employed (Kouwenhoven, 2019). By using the python random forest package and function, the Random Forests Regression model will calculate the estimated Wealth Index based on the input. The final accuracy evaluation is separated from the accuracy test of the Random Forests regression model, and the comparison of the estimated Wealth Index at grid-level and district-level. The accuracy test of the Random Forests regression model includes calculating the R-square between the estimated Wealth Index and the actual Wealth Index and the generalization of the multi-sourced Random Forests model with both census survey data and satellite data from the case study area Kenya to other countries. We could then apply the model to estimate the Wealth Index in other countries by using variables extracted from multiple data sources in those countries as model inputs.
 
 
 
## 4.  Anticipated Results
 
### 4.1 Anticipated Gains
 
First, the adjusted R^2 value between the actual and estimated WI in Kenya >= 0.50 is anticipated so that the null hypothesis on accuracy evaluation of the Proposed RF Model is rejected, indicating a strong correlation between the actual and estimated WI, and showing a good performance of the Random Forest Model. Second, the r value between the estimated WI at grid-level and the estimated WI at the district-level∈[0,1] is expected so that the null hypothesis on accuracy evaluation compared with district-level census data is rejected. Third, the adjusted R^2 value between the actual and estimated WI with the change of variable inputs in Ethiopia, Somalia, Uganda, and Rwanda >= 0.50 is anticipated so as to indicate a good generalization ability of the proposed RF model to other countries in Sub-Saharan Africa. Fourth, the adjusted R^2 value between the actual and estimated WI with the change of variable inputs in Bangladesh, Nepal, and the Mekong River Delta region in Vietnam >= 0.50 is expected so as to suggest a good generalization ability of the proposed RF model to developing countries other than Sub-Saharan Africa. Fifth, the difference between the estimated WI before and after government regulations is anticipated so as to reflect the influence of government policies targeting the presented result of my research.
 
 
 
### 4.2 Anticipated Obstacles
 
First, inaccuracy of the original data could be one of the principal obstacles inside the research. The basis of my research is to assume that the original data is accurate enough to be the potential input of the proposed model. The second potential hindrance could be the matching degree of the model. The selection of variable types from the start and the fitness of the Random Forest Regression model after the input of data and variables are two major issues inside the matching problem. The current research plan considers three types of variables or features extracted from the datasets: socioeconomic variables from NPP-VIIRS NTL and DNB, structure & texture variables of the landscape from MODIS and Land Cover Map, and accessibility variables from OpenStreetMap POI data. I need to consider both the redundancy and deficiencies of the variable types so as to achieve just the right amount of comprehensiveness. Third, the insufficiency of the available data space may not be able to accommodate the shared memory segment for running the data throughout the model so that there will be new demands for iteration on larger data space. How to construct targeting evaluations to the proposed model could be the fourth difficulty. Now that I will compare the adjusted R^2 value between the actual and estimated WI in Kenya to test the accuracy of the proposed RF model in the case study of Kenya, compare the r value between the estimated WI at grid-level and the estimated WI at the district-level, compare the adjusted R^2 value between the actual and estimated WI with the change of variable inputs in Ethiopia, Somalia, Uganda, Rwanda, and Bangladesh, Nepal, and the Mekong River Delta region in Vietnam to test the replicability of the model in different geographical context, and compare the difference between the estimated WI before and after government regulations to complete the accuracy evaluation of the model, but evaluation tests on areas other than the current comparisons would appear for iterations and improvements of the model because the existing dimensions or indicators on this may not be comprehensive enough.
 
 
 
## 5.  Budget
 
The $100,000 budget breakdown could be composed of $20,000 for Purchase of datasets, $20,000 for data preparation on cleaning and sorting, $30,000 for modeling and computing, $10,000 for display of data results, and $20,000 for model validations, alterations, and renovations. First, purchasing the datasets I need in the research would be roughly $20,000: the access to NPP-VIIRS NTL and DNB, MODIS, Land Cover Map, and OSM Road Map datasets is the important first step to complete my research plan. Second, data preparation work done by IT, BI, and data management teams are required to ensure that the raw data readied for data processing and analysis is accurate and consistent so the results of analytics applications will be valid, since different datasets often have different formats that need to be reconciled and the data is commonly created with missing values, inaccuracies and other errors. Third, constructing the proposed model is the principal part of the budget. I need professional and technical teams to build the model and expansive computer data storage to run the model with an incredibly large amount of data, which will be approximately $30,000 inside the whole budget. Data visualization is also important to present and display the results of my research, enabling local governments, NGOs or other organizations to understand the aspects they need to work on. Finally, I will leave about $20,000 on a series of model evaluations on different kinds of accuracy tests, and the followed-up tracking for government policies and actions to validate, iterate, and renovate the application of the model.
 
## 6.  Potential Benefits of the Research Plan

The goal of the research plan is to provide faster, more accurate, and more flexible poverty assessment and estimation with the lance of conventional census-based measures and innovative high-resolution satellite-based measures in the case study of Kenya, and given that the data utilized in the research plan is globally and publicly available, the methodology in this study would be applicable in other countries or regions with sufficient availability of base data to estimate the extent of poverty globally. With more accurate estimation on the influencing variables to poverty level, local governments, NGOs or other powerful organizations could provide targeting solutions and aids to the poor to influence the variable inputs so as to help construct followed-up evaluations on the effects of government policies. For instance, researchers (Stevens, et al., 2015) illustrated that one of the most important variables influencing the poverty estimation in Kenya after going through the RF classification model is medical and sanitation facilities, so that if this is also the one of the top ranked variables from my proposed RF model, government policies would more likely to respond to the results of the research and focus more on the improvement of certain important variables presented from the research including the factor of medical and sanitation facilities in Kenya. The poor in developing countries would be the groups that benefit from the poverty estimation research plan since it would provide more accurate poverty analysis and assessment corresponding to their living conditions. 

## 7.  Subsequent Research Suggestions

For subsequent research suggestions, first, micro-census data could be taken into consideration as an alternative type of data in poverty assessment. Micro-censuses are conducted in relatively short and regular intervals and include data richer than the one collected by census. The micro-census uses a single-stage stratified cluster sampling method: the households of each sampling district remain in the sample for four years, and each year, a quarter of the sampling districts are replaced by newly introduced sampling districts, while households and individuals who move away from the sampling district are not followed but rather replaced by households and individuals moving into the sampling district. As a repeated rotating panel survey, the micro-census provides an enormous sample size, which could be a more accurate original database compared with census data. Second, a series of following tests corresponding to government policies should be constructed based on the model so as to analyze the practicality of regulations and aids in time. Third, evaluation tests on aspects other than the existing comparisons would be required for further iterations and improvements of the model because the existing dimensions or indicators on accuracy evaluations may not be comprehensive enough.


## Reference

1.	Bersisa, M. & Heshmati, A. (2021). A Distributional Analysis of Uni-and Multidimensional Poverty and Inequalities in Ethiopia. Soc Indic Res (2021). https://doi.org/10.1007/s11205-021-02606-w

3.	Kouwenhoven, L. (2019). Poverty Distribution Mapping Using a Random Forest Algorithm: A Case Study of the Mekong River Delta. Retrieved from https://spinlab.vu.nl/wp-content/uploads/2019/06/Kouwenhoven_L.pdf

4.	Stevens, F.R., Gaughan, A.E., Linard,C. & Tatem, A.J. (2015). Disaggregating Census Data for Population Mapping Using Random Forests with Remotely-Sensed and Ancillary Data. PLoS ONE 10 (2): e0107042.
doi:10.1371/journal.pone.0107042

5.	Zhao, X., Yu, B., Liu, Y. & Chen, Z. (2019). Estimation of Poverty Using Random Forest Regression with Multi-Source Data: A Case Study in Bangladesh. Remote Sens. 2019, 11(4), 375; https://doi.org/10.3390/rs11040375




