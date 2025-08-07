# The Influence of Climate Change Expectations and Sectoral Differences on Food Prices in Nigeria

This project explain the steps taken in carrying out the analysis on Google Colabs alongsides exploring how local perceptions of climate extremes such as droughts and floods affect food price trends across Nigerian communities. Combining **Excel**, **Power BI**, and **Python (Google Colab)**, this analysis provides an integrated view of data processing, visualization, and model insights.

---

## 🎯 Objectives

- Generate clear, Excel-style bar chart visualizations using Python.

- Investigate community perceptions and expectations regarding climate change.

- Analyze variations in food prices across regions in Nigeria based on climate expectations.

- Combine descriptive and predictive insights using multiple tools (Excel, Power BI, and Python).

---

## 📁 Tools & Workflow

| Tool        | Purpose                                  |
|-------------|------------------------------------------|
| Excel       | Data cleaning, merging of data, filtering, and pre-processing |
| Power BI    | Interactive dashboards & summary visuals |
| Google Colab| Analysis, modeling & predicting (Python) |

---

## 📦 Data Sources

- **GHS-Panel Wave 5 post harvest community (2023/2024)** :
  - Section 6b: Expectations on Climate Extremes
  - Section 8: Food Prices
  

--------------
## 📊 Analyses Performed:

-----------
### 🔹 Excel:


- Cleaned the dataset

- Power Query execution

- Merged Food price and Expectation of climate change dataset together




### 📈  Excel Power Query Dashboard
![Screenshot 687](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(687).png)





-----------

### 🔹 Power Bi:

-----------


### 📈 Power Bi Dashboard
![Power Bi Dashboard](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20%28671%29.png?raw=true)




### 📈 Power Bi Dashboard 2
![Power Bi Dashboard 2](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20%28673%29.png?raw=true)




### 📈 Power Bi Dashboard 3
![Power Bi Dashboard 3](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20%28674%29.png?raw=true)




-----------


### 🔹 Python (Google Colab):

-------------------
In this section a detailled breakdown if what was dome was indicated in the screenshot coding sheet

### 📈 Uploaded file unto Google Colab and checking for missing values

![Screenshot 675](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(675).png)





![Screenshot 676](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(676).png)





![Screenshot 677](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(677).png)





### 📈 Filtering, grouping, and sorting data based on climate expectation by sector

![Screenshot 678](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(678).png)






### 📈 Sector-wise Climate Expectation Analysis (Rural vs Urban)
![Screenshot 682](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(682).png)



**✅ Summary Interpretation:**
- Rural Areas (Sector 1): In rural areas, 33,189 respondents have indicated that they expect climate change to impact their lives. This number is significantly higher than the respondents from urban areas, which could indicate that rural populations are more concerned or more affected by climate-related issues, especially given that rural areas are often more dependent on agriculture and natural resources.


- Urban Areas (Sector 0): In urban areas, only 14,652 respondents are expecting climate change. This lower number might suggest that people in urban areas feel less directly impacted by climate change, perhaps due to better infrastructure, access to climate adaptation resources, or a lesser reliance on agriculture.




### 📈 Food Price Comparison by State and Climate Expectation
![Screenshot 693](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(693).png)







### 📈  Graphical result for Food Price Comparison by State and Climate Expectation
![Screenshot 694](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(694).png)




### 📈  Urban vs Rural Climate Expectation Count specific


where:

- 1 = Late onset of rain

- 2 = Drought

- 3 = Flood

- 4 = Very High Temperature



![Screenshot 698](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(698).png)




###  📈  Price distribution by state

![Screenshot 702](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(702).png)





![Screenshot 703](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(703).png)





### 📈  Predictive Modeling: Climate Expectation → Food Price:


- **Random Forest Classifer **


** ✅ Goal:**
To predict individuals’ expectations of experiencing future climate shocks, where the response variable (climate_exp_cd) had four categories:

-  1 = Late onset of rain

- 2 = Drought

- 3 = Flood

- 4 = Very High Temperature


![Screenshot 707](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(707).png)



**📝 Interpretation:**

| Label | Meaning                        | Support | Precision | Recall | F1-score | Interpretation                                                                 |
|-------|--------------------------------|---------|-----------|--------|----------|---------------------------------------------------------------------------------|
| **1** | Late onset of rain             | 9414    | 0.20      | 0.04   | 0.06     | The model rarely identifies this group correctly – low recall means most are missed. |
| **2** | Drought                      | 9808    | 0.21      | 0.03   | 0.05     | Similar to class 1 – the model struggles with identifying this group accurately. |
| **3** | Flood
   | 10205   | 0.26      | 0.90   | 0.41     | Model overpredicts this neutral category – catches most class 3s, but likely overfitting. |
| **4** | Very High Temperature                      | 9246    | 0.15      | 0.01   | 0.01     | Very poor prediction of people who actually expect climate shocks.              |





- **DecisionTreeRegressor**


**✅ Goal:**
To predict food prices (c2q3) based on climate expectations (climate_exp_cd), sector, state, and item type (item_cd) using a Decision Tree Regression model.



The code used is displayed below: 

from sklearn.tree import DecisionTreeRegressor
from sklearn.metrics import mean_squared_error
import numpy as np
import pandas as pd


X_tree = pd.get_dummies(data[['climate_exp_cd', 'sector', 'item_cd', 'state']], drop_first=True)
y_tree = data['c2q3']


mask = ~y_tree.isna()
X_tree = X_tree[mask]
y_tree = y_tree[mask]


tree_model = DecisionTreeRegressor(random_state=0)
tree_model.fit(X_tree, y_tree)


y_pred = tree_model.predict(X_tree)
rmse = np.sqrt(mean_squared_error(y_tree, y_pred))
print(f"Train RMSE: {rmse:.2f}")





**📊 Result:**

Train RMSE: 1036.37



**📝 Interpretation:**
The model's predicted food prices deviate by about ₦1,036 on average from the actual prices (on training data).

Since this RMSE is on the training set, it may not reflect real-world performance due to potential overfitting. A proper train-test split or cross-validation is needed for a realistic performance estimate.



- ** 📈 OLS regression output:**

**📌 Goal**
To understand how climate expectation (climate_exp_cd), sector (urban/rural), Likelihood of Climate Change (c6bq1), Reason for Expecting Climate Change (c6bq2) influence food prices (c2q3).


![Screenshot 722](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(722).png)




**📝 Interpretation**: 

| **Variable**                               | **Coefficient** | **Interpretation**                                                                                                                                                           |
|--------------------------------------------|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Intercept (const)**                      | 420.74          | When all variables are 0, the expected food price is ₦420.74.                                                                                                                 |
| **q1 (Likelihood of Climate Change)**      | 10.16           | Each unit increase in the likelihood of climate change increases food price by ₦10.16, holding other variables constant.                                                        |
| **q2 (Reason for Expecting Climate Change)**| 21.98           | Each unit increase in the reason for expecting climate change increases food price by ₦21.98. This has the strongest positive influence on food price.                         |
| **sector**                                 | -80.92          | Moving from urban (0) to rural (1) decreases food price by ₦80.92 on average.                                                                                               |
| **climate_exp_cd (Climate Expectation)**   | -2.67           | The coefficient is not statistically significant (p = 0.352), suggesting no reliable effect of climate expectations (extremely unlikely, unlikely, neither, likely) on food price. |





### 📈  State level food price Clusters:


![Screenshot 710](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(710).png)







![Screenshot 711](https://github.com/Lauren-Akhidenor/Foodprice_ClimateChange/blob/main/Screenshot%20(711).png)



--------------------------
## 📝 Conclusion:

The analysis reveals that various factors influence food prices, with significant findings in terms of climate-related perceptions, adaptation strategies, and sectoral differences. Specifically:

- **Likelihood of Climate Change:** A higher likelihood of climate change is associated with an increase in food prices by ₦10.16. This suggests that respondents who perceive climate change as more likely may experience higher food prices, potentially due to anticipated disruptions in the agricultural supply chain.

- **Reason for Expecting Climate Change:** The reason for expecting climate change plays an even stronger role, increasing food prices by ₦21.98. This highlights that when respondents have a concrete understanding or justification for climate change, it influences the food market more substantially, possibly indicating that expectations of negative climate events might drive market prices up in anticipation.

- **Sector (Urban vs Rural):** The transition from urban (0) to rural (1) areas is associated with a decrease in food prices by ₦80.92. This could reflect regional disparities in supply, transportation costs, and market accessibility, with rural areas perhaps benefiting from lower costs due to more localized production.

- **Climate Expectation (climate_exp_cd):** Despite the inclusion of climate expectations as a factor, this variable did not show statistical significance (p = 0.352), indicating that expectations regarding climate phenomena such as late onset of rains, drought, floods, or extreme temperatures do not reliably predict food prices in this dataset.

In conclusion, while climate-related variables like **Likelihood of Climate Change** and **Reason for Expecting Climate Change** significantly influence food prices, **sectoral differences (urban vs rural)** also play a crucial role. The lack of significance in **Climate Expectation** suggests that, in the context of this study, immediate responses to specific climate risks do not have as strong a direct effect on food pricing as the broader perceptions and adaptation strategies do. This underscores the complexity of the relationship between climate change, agricultural markets, and food pricing, which must be considered in future policy and economic planning related to food security.



--------------------------
## 💡 Recommendations

Based on the findings, the following recommendations can be made:

1. **Address Climate Change Perceptions:**
   Governments and policymakers should consider climate perceptions in food pricing and market policies. Public awareness and educational campaigns could be beneficial in managing the expected impacts of climate change on agricultural practices and food prices.

2. **Enhance Climate Adaptation Strategies:**
   Since the **Reason for Expecting Climate Change** is a significant factor influencing food prices, adaptation strategies focused on mitigating anticipated climate extremes (like droughts or floods) should be prioritized. Investments in climate-resilient agricultural technologies and infrastructure should be considered, especially in regions with high climate risk perceptions.

3. **Focus on Rural-Urban Disparities:**
   The observed price difference between rural and urban areas should be addressed through policies that enhance market accessibility in rural areas. Improving transportation infrastructure and supply chain efficiency could reduce food price disparities between regions.

4. **Develop Targeted Climate Response Mechanisms:**
   Although **Climate Expectation** was not significant in this study, targeted interventions in communities that are more prone to certain climate risks (e.g., floods, drought) could help to manage the market effects of climate extremes and ensure food security.

5. **Monitor and Refine Policy Interventions:**
   Continuous monitoring of food prices and climate impacts is crucial. Further research should investigate how other variables, such as actual climate events or government policies, affect food prices in different regions.

