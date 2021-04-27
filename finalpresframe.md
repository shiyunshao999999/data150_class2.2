## Title: Balance the Application of Conventional Census-Based Measures and Innovative High-Resolution Satellite-Based Measures to Increase Accuracy and Flexibility in Sub-Saharan African Poverty Assessment with the Use of Random Forests Method
## Present Date: 5/4


## 1. Introduction to the Poverty issue in Sub-Saharan African Countries
### Poverty 
Basic Freedom – Restricted

### Different Poverty Assessments
Various Policy Actions - Social Development


## 2. Methods
### Decision Trees

-	with census base
-	with high-resolution satellite images

### Random Forests

-	with census base

Datasets: 
•	Living Standards Measurement Study (LSMS)
•	Demographic and Health Surveys (DHS)

Explanatory Variables: 
•	Sex of head of household
•	Age of head of household
•	Marital Status
•	Highest educational level attained
•	Type of place of residence
•	Region

Response Variables: 
•	N_Poverty


-	with high-resolution satellite images

Datasets: 
•	Point of Interest GIS data (POI) - OpenStreetMap(OSM)
•	Spatial - MODIS (or Moderate Resolution Imaging Spectroradiometer)

Explanatory Variables: 
•	POI_Density 
•	Distance-to-POI

•	distance_to_road
•	distance_to_highway
•	distance_to_provincial_road

Response Variables: 
•	Wealth Index

### RF Algorithm
1. Cˆb(x): The class predicted by the bth tree
While a majority vote means that from a set of decision trees in the random forest, the mostly voted class is the final classification
2. The calculation of the regression is calculated by, which represents the average class choice and the regression choice
3. The impurity measure i(t) is the Gini index, which is used to determine the branching of the decision trees right from the root nodes to the child nodes
4. The calculation of the Mean Decrease Impurity Measure, the result of which provides a ranking of variable importance: the variable with the largest decrease in impurity will be considered as the most important variable. 

### Flowchart
### Python Code

## Research Plan
1. Literature Gap
2. Problem Statement
3. Explain the NEW Flowchart
