<img src="images/gradhats.jpg" align='center' alt="Students in cap and gown sitting at graduation" style="width: 800px;"/>

# Technical Overview
Targeting black college graduation rates, this project seeks to answer a regression problem using only financial information from public and private four year colleges in US. Data was clean of nans by simple imputation. Methods for modeling included Muliple Linear Regression and Regression Decision Trees, using Lasso, Stepwise, and Random Forest Regression feature selection, along with GridSearchCV hyperparameter tuning. 

# Business Understanding
In [Public Act 102-0570](https://ilga.gov/legislation/publicacts/fulltext.asp?Name=102-0570), Illinois' General Assembly has commissioned the Illinois Board of Higher Education (IBHE) to offer "specific data-driven criteria and approaches to the General Assembly to adequately, equitably, and stably fund public universities in this State and to evaluate existing funding methods." This Commision on Equitable Public University Funding (CEPUF) coincides with the [A Thriving Illinois: Higher Education Paths to Equity, Sustainability, and Growth] (https://ibhestrategicplan.ibhe.org/IBHE-Strategic-Plan-2021.html) which includes providing "equitable funding so that students can receive the best educational experience and succeed at whichever institution they attend," and funding "institutions sufficiently to achieve student, institutional, and state goals."

This project targets 6-year black bachelors graduation rates for first-time, full-time students-- the typical measure for college student success-- using U.S. public and private university data from the Integrated Postsecondary Education Data System (IPEDS). This project aims to offer data-driven advice on how Illinois' universities might better leverage their financials towards black student success.

# Data Understanding
Data was accessed through [IPEDS](https://nces.ed.gov/ipeds/use-the-data/download-access-database). After downloading 10 years(2009-2020) of their Access database files (.accdb), [pyodbc module](https://pypi.org/project/pyodbc/) and SQL query were used to pull financial data (financial data (tables: DRVF, F_F1A, and F_F2) from 1681 public (587) and private (1094) universities (The IPEDS website does offer a [user-friendly query interface](https://nces.ed.gov/ipeds/datacenter/InstitutionList.aspx?goToReportId=1), but only 20 variables could be pulled at a time. The databases, private and public, were kept separate because of the differing financial categories (table and variables with F1 are from public Universities, while F2 is private not-for-profits-- f3 is private, for-profit, and was excluded from this project). Limitations with IPEDS data are discuss below.  

# Data Preparation
If the school did not have the target variable, it was excluded from the analysis. Sadly, Governors State University, a public school in Illinois, did not have any target information; therefore it was removed.School names and variable titles were merged and transposed for clarity. And columns with 40% data were dropped. Some of the financial metrics changed in 2014, so some columns are missin 40% of the data. These columns were the subcategories of Benefits, Operation and Maintenance of Plant, Depreciation, Interest, All Other for several categories. These categories post 2014 are now summarized in 'Total amount' and 'Salaries and wages' for Instruction, Research, Public service, etc. These subcategories and others missing 40% of data were dropped.

# Methods
Because the Illinois Board of Higher Education is seeking specific policy advice, this project will avoid black-box and hard-to-interpret models. The approach is simple: starting with a baseline, iterate through Linear Regressions to find the best model. Different Selection types, like Stepwise(to only pull statistically significant features), Lasso (to penalize weak features), Random Forest Regression are used A Pipeline to preprocess imputing and standardizing was also used to speed up the process.Data was normalized at point of regression, to make it more readable for the model.

# Evaluation
For both Private and Public models, the best model was the stepwise with lasso mulitple linear regression. R^2 was chosen to see how much of the variance can be explained by the model. The Root Mean Squared Error tries to reduce the mistakes the model will make in prediction, giving a better sense whether the feature will actually influence black graduations or not. 
The Private Test Linear Regression had an R^2 of 0.271 and a RMSE of 22.71
The Public Test Linear Regression had an R^2 of 0.278 and an RMSE of 17.65

# Recommendations
The recommendations for Public universities are as follows: 
1) Incentivize 5 percent increases in budget allocation towards research. This could mean expanding already well established research universities, like the University of Illinois, by offering research prizes or through appropriations.This could also mean starting research at on of the four public universities in Illinois that only allocate 1 percent to Research.
2) Offer more discounts and allowances for auxilliary services, either through grants or appropriations. The model predicts an additional \\$1,000 per student increases a percentage point in blk grs. 

# Next Steps
- To improve model performance, I would like to run similar regressions for all of IPEDS data including Admissions, Enrollment, Retention, Human Resource Information, and Institutional Characteristics.Then combine significant and impactful features for a more robust predictive model and more precise policy advice. This would bring specificity for where to apply state grants and appropriations. Only 28% of variance in the target is explained by my model, so bringing in more significant variable might help. Obviously, institutions can only do so much, but I would like to maximize this effort. Then combine significant and impactful features for a more robust predictive model and more precise policy advice. This would bring specificity for where to apply state grants and appropriations.  
- The graduation rate for IPEDS only calculates first time, full-time students This excludes transfers,  winter enrollment, and part-timers, possibly [up to 50% of students](). Expanding the target to include these students would give a more accurate protrayal of student success. 
- Finally, I am willing to further the tenets of a Thriving Illinois, by considering optimal financial aid rates for low-income and minority students.
 
 For More Information
 
 See the full analysis in the [Jupyter Notebook](https://github.com/andrewschmeck/Black-Graduation-Rates/blob/main/Black_Graduation_Rates_notebook.ipynb) or review this [presentation](https://github.com/andrewschmeck/Black-Graduation-Rates/blob/main/Black_Graduation_Rates_presentation.pdf). 
 
 For additional info, contact Andrew Schmeck at andrew.schmeck@gmail.com
 
 Repository Structure
 
├─ images
│  ├─ Concatenate.png
│  ├─ gradhats.jpg
│  ├─ gridsearch_pr.png
│  ├─ gridsearch_pub.png
│  └─ retrieval.png
├─ .gitignore
├─ Black_Graduation_Rates_presentation.pdf
├─ Black_Graduation_Rates_notebook.ipynb
└─ README.md
