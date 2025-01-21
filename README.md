#### Problem Statement:

The purpose of this project is to **analyze the characteristics of customers who are most likely to default on their credit card payments**. By identifying key factors contributing to defaults, financial institutions can implement targeted strategies to mitigate risks and improve credit management. The data for this analysis is sourced from the UCI repository.

#### Code and Resources Used:
- **Jupyter Notebook**
- **Packages:** pandas, numpy, sklearn, matplotlib, seaborn
- **Data:** [Default of Credit Card Clients Dataset](https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients)

#### Data Structure and Preprocessing:
The dataset contains 30,000 observations and 23 features. The response variable is a binary variable:
- **Default payment (Yes = 1, No = 0).**

The 23 explanatory variables are:
- **X1:** Amount of given credit (NT dollar) - includes individual consumer credit and family (supplementary) credit.
- **X2:** Gender (1 = male; 2 = female).
- **X3:** Education (1 = graduate school; 2 = university; 3 = high school; 4 = others).
- **X4:** Marital status (1 = married; 2 = single; 3 = others).
- **X5:** Age (year).
- **X6-X11:** History of past payments (April 2005 - September 2005):
  - Measurement scale: -1 = pay duly; 1 = payment delay for one month; up to 9 = payment delay for nine months and above.
- **X12-X17:** Amount of bill statements (NT dollar) from April 2005 to September 2005.
- **X18-X23:** Amount of previous payments (NT dollar) from April 2005 to September 2005.

**Data Cleaning Steps:**
1. The **EDUCATION** column had 7 unique values; categories 0, 5, and 6 were merged with category 4.
2. The **MARRIAGE** column had 4 unique values; category 0 was merged with category 3.

#### Exploratory Data Analysis:
1. **Class Imbalance:**
   - more than 75% non-defaults, less than 25% defaults.
2. **Gender:**
   - 40% male clients; 60% female clients.
   - Default rates: 24% for males, 20% for females.
3. **Education:**
   - 47% university, 35% graduate school, 16% high school, 2% other.
   - Default rates: High school (25%), university (24%), graduate school (19%), other (7%).
4. **Marital Status:**
   - Single clients: Significant non-default proportion but default rate of 20.93%.
   - Married clients: Slightly higher default rate than singles.
   - "Others": Similar default rate to married clients.
  ![image](https://github.com/user-attachments/assets/d66168de-69d6-4a22-b257-e77dc985fa06)

5. **History of Past Payments (PAY Variables):**
   - PAY_0 shows most defaults occur at subcategory 2 (2 months payment delay).
   - For other PAY variables, subcategory 0 shows the highest default counts.
 ![image](https://github.com/user-attachments/assets/b30ce91a-7524-413e-9943-36d6eba02903)
 
6. **Limit Balance:**
   - Customers with higher balances are less likely to default.
 ![image](https://github.com/user-attachments/assets/f9e70380-1839-48f4-aac7-9717aec52daf)
 
7. **Age:**
   - Higher default proportions in age groups 60-64, 70-74, and 20-24.
 ![image](https://github.com/user-attachments/assets/47afcb98-9309-4126-a5f0-fa4d51b414be)
 
     
#### Correlation Analysis:
- **Spearman's Rank Correlation:**
  - In comparision with other features The History of past payment(PAY_0 to PAY_6) exhibit the stronger correlation with the target variable, especially PAY_0. These are likely more predictive of default status.
  - IMIT_BAL: There is a weak negative correlation between LIMIT_BAL (credit limit) and the target variable, suggesting that higher credit limits might be weakly associated with a reduced chance of default.
  - BILL_AMT and PAY_AMT Variables: The correlation between bill amounts and  default too small, which shows these features are not correlated with the target.However,  the payment amounts have a weak negative correlation. This suggests that people who make larger payments are slightly less likely to default.
  - Sex, Education, Marital Status, and Age: These categorical and demographic variables show very weak correlations with the target variable, indicating they might not be significant predictors in this context.
  - 
![image](https://github.com/user-attachments/assets/5eab3399-9522-4d2e-906d-f2225fbf1a57)

#### Conclusion:
Based on the analysis performed in the previous sections, we can conclude that:

- The **payment status variables (delays in payment) exhibit the strongest correlation with the target variable, especially PAY_0**. These are likely more predictive of default status.
- Clinets who **make larger payments are slightly less likely to default**.
-  While Sex, Education, Marital Status, and Age had week correlation with the target variable we can see that: 
-  **A male customer** is more likely to default than a female customer.
-  People with a **relationship status of other** are more likely to default than married or single people.
-  A customer whose **highest educational qualification is a high-school diploma** is more likely to default than a customer who has gone to graduate school or university.
-  A customer who is in **(60-64) age group** has a higher probability of defaulting on payments than any other age group.

This analysis highlights the key characteristics influencing default risk and emphasizes the importance of payment history and demographic factors in predicting defaults.

