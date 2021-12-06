# Technical Overview
Targeting black college graduation rates, this project seeks to answer a regression problem using only financial information from public and private four year colleges in US. Data was clean of Nans by simple imputation. Methods for modeling included Muliple Linear Regression and Regression Decision Trees, using Lasso, Stepwise, and Random Forest Regression feature selection, along with GridSearchCV hyperparameter tuning. 

# Business Understanding
In [Public Act 102-0570](https://ilga.gov/legislation/publicacts/fulltext.asp?Name=102-0570), Illinois' General Assembly has commissioned the Illinois Board of Higher Education (IBHE) to offer "specific data-driven criteria and approaches to the General Assembly to adequately, equitably, and stably fund public universities in this State and to evaluate existing funding methods." This Commision on Equitable Public University Funding (CEPUF) coincides with the [A Thriving Illinois: Higher Education Paths to Equity, Sustainability, and Growth] (https://ibhestrategicplan.ibhe.org/IBHE-Strategic-Plan-2021.html) which includes providing "equitable funding so that students can receive the best educational experience and succeed at whichever institution they attend," and funding "institutions sufficiently to achieve student, institutional, and state goals."

This project targets 6-year black bachelors graduation rates for first-time, full-time students-- the typical measure for college student success-- using U.S. public and private university data from the Integrated Postsecondary Education Data System (IPEDS). This project aims to offer data-driven advice on how Illinois' universities might better leverage their financials towards black student success.

# Data Understanding
Data was accessed through [IPEDS](https://nces.ed.gov/ipeds/use-the-data/download-access-database), using 10 years (2009-2020) of their Access database files (.accdb), pyodbc module and SQL query was used to pull financial data (financial data (tables: DRVF, F_F1A, and F_F2) from 1681 public (587) and private (1094) universities. Nans were imputed.  

# Modeling
Multiple Linear Regression, Stepwise, Lasso, and Random forest selection, Decision Tree with Random Forest selection, and obviously random forest tuning to feed features back into the more interpretable models.

# Evaluation
Private and public had different optimal models: Linear Regression with Lasso for Private; Decision Tree with random forest selection for Public. 
The Private Test Linear Regression had an R^2 of 0.312 and a RMSE of 22.07
The Public Test Tree had an R^2 of 0.345 and an RMSE of 16.82

# Recommendations
1) Focus on NIU and CSU. Because their graduation rates are so low (8% and 16%), marginal improvments will make the largest difference. For example, if given the current enrollment at NIU and successful changes to increase graduation rates to match the average of illinois (37%), an additional 600 black students would have degrees. This would in turn lead to an 11% in the states overall black student graduation rate. 
2) Incentivize discounts on sales and services of auxiliary enterprises, which may help supplement the non-tiution related costs of attending school. 
3) Encourage public schools to hire more institutional support, as it is the third most important feature for public schools. This means better management, operations, and fundraising efforts. 
4) Private schools seems to be about accumulating assets like books in libraries, art, equipment, and property. This likely is just a reflection of wealthy schools doing well, not a direct causal link.

# Next Steps
- Given more time with the data, this project would calculate the rate of change for these features and run a time series model to see if a given lag year for a student is of importance for graduating. 
- The graduation rate for IPEDS only calculates first time, full-time students, which excludes transfers,  winter enrollment, and part-timers, possibly [up to 50% of students](), so expanding the target to include these students would give a more accurate protrayal of student success. I would also like to track the 10 year default rate on loans for Illinois schools, as the debt places an already disproportional burden on minority communities. 
- Finally, I am willing to consider optimal financial aid rates, which furthers your goal towards equity and sustainability. 
