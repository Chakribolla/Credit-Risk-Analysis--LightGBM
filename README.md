# Credit-Risk-Analysis
<p align="center"> 
  <img src="https://i.ytimg.com/vi/RvqrzvY3Sm8/maxresdefault.jpg">
  
# Hi Guys! Today, I have chosen an important problem statement to work upon. Let me break it down into simple words, and you will soon understand its importance.
- Financial institutions invest a ton of money for constructing credit risk analysis models to determine the probability of default of a potential borrower. The models provide information on the level of a borrower's credit risk at any particular time.
- Some of you might be wondering what "credit" is. Well here's come the definition:

-  "Credit is the ability to borrow money or access goods or services with the understanding that you'll pay later." 
- "Creditworthiness is how a lender determines that you will default on your debt obligations, or how worthy you are to receive new credit. Your creditworthiness is what creditors look at before they approve any new credit to you." 
Credit risks are a commonly observed phenomenon in areas of finance that relate to mortgages, credit cards, and other kinds of loans. There is always a probability that the borrower may not get back with the amount. Traditionally, it refers to the risk that a lender may not receive the owed principal and interest, which results in an interruption of cash flows and increased costs for collection.
Hence properly assessing and managing credit risk can lessen the severity of a loss.
# Contents
1. About Dataset - Source , What it Contains, How it will be Useful.
2. Importing Libraries / APIs / Datasets
3. Segregating Dataset
4. Preliminary Investigation of Data
5. About Target Variable
6. Domain Knowledge
7. About Categorical Variables
8. Descriptive Statistics
9. Missing Values
10. Duplicate Values
11. Imbalanced - ness of Target Variable
12. Distribution, Skewness, Kurtosis
13. Variance / Standard Deviation
14. Outliers & Anomalies
15. "Credit risk Preediction Using LGBM" 
16. Detailed Insights (Variable - wise)
17. Important Insights
18. Data Pre - Processing Checklist
---------------------------------------------------------------------------------------------------------
# About Dataset - Source, Features
Quick Feature Description
Feature - 1 ---> Age (in years)

Feature - 2 ---> Annual Income (In INR)

Feature - 3 ---> Home ownership (Nominal Categorical)

Feature - 4 ---> Employment length (in years)

Feature - 5 ---> Loan intention (Purpose of Loan)

Feature - 6 ---> Loan grade (Ordinal Categorical)

Feature - 7 ---> Loan amount (in INR)

Feature - 8 ---> Interest rate (in percentage)

Feature - 9 ---> Loan status (0 is non default 1 is default) ---> Target ---> Binary Classification
Feature - 10 ---> Loan - Percent income (Debt - Equity Ratio) (in percentage)

Feature - 11 ---> History of default (Nominal Categorical)

Feature - 12 ---> Credit history length (in years)

# Detailed Insights (variable - wise)

# Age
Age is numerical variable. 
There are no Missing values. 
Age variable ranges from 20 to 144 which definitely creates suspicion about the accuracy of data.  
Mean age of 27.74 indicates data is highly right skewed.  skew = 2.58.
As per box – plot proximity rule, there are 1494 Outliers. (4.58%)
All outliers are on higher side. 
As per Box-plot, Outliers ranges from 41 to 144. 
Most Outliers lie between age 41 to 70.
As per Scatter plot, the variable Age has non – linear correlation with all other numerical variables except Credit         history length. There is no fixed pattern.

# Annual Income
Annual Income is again a numerical variable. 
The problem statement is silent about the currency. We assume the currency as INR. 
There are no Missing values.
Income Variable ranges from 4000 to 6000000. Huge range and must be Standardized. Annual Income of Rs. 4000 must not be     eligible for any type of loan.
The distribution of Annual Income is highly right skewed. 
Mean Annual Income is Rs. 66075 and Standard Deviation is 61983. This seems to be a great variation.
As per box – plot proximity rule, there are 1484 Outliers (4.55%).
All outliers are on higher side. 
As per Box-plot, Outliers ranges from   to 
As per Scatter plot, the variable Annual Income has non – linear correlation with all other numerical variables. There     is no fixed pattern.

# Home ownership
Home Ownership is a Nominal Categorical Variable.
There are 4 unique values in it namely,
RENT - 50.48% MORTGAGE - 41.26% OWN - 7.93% OTHER- 0.33%
The category Other is not defined and is very rare and is safe to ignore.
There are no Missing Values in the Variable Home Ownership.
From Bank’s perspective, the borrower with Own House are considered to be less risky. However, it should not be the         sole consideration.
Analyse the above categories with Target Variable i.e. Loan Status.

# Employment length (in years)
No. of years of employment is a numerical variable.
This variable has Missing values. The magnitude of missing is around 2.75%.
It seems the missing values are not because of any error.
It’s a classic case of Structurally Missing Data. It is missing because it should not exist. The reason for missingness     is perhaps some borrowers have their Own business and is not employed.
Considering the reason of missingness and magnitude of missing data, the suggested course of action is List – wise         deletion of missing values.
The maximum employment length is 123 years, an indication of error.
The distribution of years of employment is again right skewed. 
As per IQR proximity rule, there are 853 Outliers. (2.70%)
# Loan Intention
Loan intention is a Nominal Categorical Variable.
There are 6 unique values in it namely,
EDUCATION - 19.81% MEDICAL - 18.63% VENTURE - 17.55% PERSONAL - 16.94% DEBT CONSOLIDATION - 16.00% HOME IMPROVEMENT - 11.06%
As per my experience, the default rate in Personal and Debt Consolidation is highest.
There are no Missing values in Loan intention variable.
Loan Grade
prima facie, this variable is Ordinal Categorical Variable.
There are no details given about this Variable like on what criteria grades are allotted. Here, we are assuming, higher     the grade, lower is the chances of Default. Going by that logic, borrowers categorized as Grade – A must have low           probability of getting Default and vice – versa. We will check the percentage of Default for every grade.
There are no Missing Values.
There are 7 unique values in it namely,
A - 33.08% B - 32.08% C - 19.82% D - 11.13% E - 2.96% F - 0.74% G - 0.20%
Loan Amount
Loan amount is a Numerical Variable.
There are no Missing Values.
Loan amount ranges from Rs. 500 to Rs. 35000.
Loan amount of Rs. 500 is too low to believe on genuineness of data.
Loan amount distribution is asymmetrical and skewed.
As per IQR Proximity Rule, there are 1689 Outliers in the variable Loan Amount. (5.18%).
As per Box – Plot, most of the Outliers are between 23,000 to 27,000.
As per Scatter Plot, Loan amount is in non – linear relation with other variables.
Interest rate
Interest rate is a Numerical Variable.
Though explicitly not mentioned anywhere about the Unit but it is in terms of percentage (%).
Interest rates ranges from 5.42% to 23.2%.
Technically, this variable should be Categorical with fewer no. of interest rates, if it belongs to One Bank or FI.
There are 29465 values and 348 unique values.
There are too many Missing values 3116 (9.56%).
There are mere 6 Outliers in Intr. rate variable.
Nature of Variable and Magnitude of Missing values makes this variable a tricky one.
As per my Domain Knowledge and Dendrogram, this variable is important and have high predictive power.
So, dropping the variable is not an option.
As per Dendrogram, this variable is highly co - related to variable Employment length and variable Past Default History.
Suggested course of action is –
i. Drop Outliers ii. Impute Missing values iii. Filter top 10 or 20 high frequency int. rate iv. Analyse the above with Target Variable.
Loan - Income Percent
Loan to Income is a Numerical Variable.
It is in relative term. (In terms of ratio).
In finance jargon, it is called as "Debt to Income ratio". (DTI).
Good / Ideal DTI ratio ---> The percentage of DTI ratio may vary from lender to lender. However, in general, a DTI         ratio of up to 40% may be considered suitable for getting a loan approved. DTI of 21% - 35% is considered as very good.
Lesser the ratio, lesser are the chances of Default and vice – versa.
There are no Missing values.
The ratio ranges from 0 to 0.83.
The distribution is asymmetrical and skewed.
As per IQR proximity rules, there are 651 Outliers (2%).
There are just 77 unique values. Technically, it is Categorical and must analyse that way only.
By analysing, the loan status with DTI ratio, it supports the above rationale. As the DTI increases, the rate of           default also increases and vice – versa.
History of Default
History of Default is Nominal Categorical Variable.
There are no Missing values.
There are only 2 unique values namely,
Yes – 17.63%
No - 82.37%
Analysing this variable w.r.t. Loan Status variable will give some vital insights.
Credit history length
Credit history length is Numerical variable.
There are no Missing values.
The variable ranges from 2 years to 30 years.
Longer the history, more knowledge about the Borrower which means more transparency and ultimately more reliable.
So, based on Domain knowledge, Person's Credit History length variable is positively correlated with Target Variable.
There are mere 29 categorical values.
16. Important Insights
It’s a Binary Classification problem consist of Target Variable “Loan Status” - 
* 0 --> Not Default
* 1 --> Default
There are records of **32,581** borrowers evaluated on 12 parameters (columns).
Target Variable is highly **Imbalanced**. The ratio of Target Variables is 21.82: 78.18 (0:1) (Majority class is twice      of Minority class).
Mainly, there are 4 Categorical Variables (dtype = Object). The details of which as hereunder:
 * Binary – History of Default
 * Nominal – Home Ownership, Loan Intention
 * Ordinal – Loan Grade
 
There are only 2 Variables which have Missing Values:
  * Interest rate -       **9.56%** 
  * Employment length -   **2.75%**
There are total 4011 missing values in a given dataset.
There are **165** duplicate values.
Except Int. rate variable, all variables are Asymmetric and are Skewed.
There are neither Zero – Variance (constant) variables nor near Zero – Variance (Quasi-Constant) variables. (Threshold      = 0.10).
Below are the Variable – wise Outliers computed on the basis of IQR Proximity Rules:
* Age = 1494
* Income = 1484 
* Employment length = 853
*	Loan amount = 1689
* Interest rate = 6
* Debt to Income ratio = 651 
* Credit History length = 1142
As per Heatmap, the following pair of variables are highly correlated:
Age & Credit History length - 0.86
17. Data Pre - Processing Checklist
Import Scikit learn library.
Handling Missing Values - Drop / Impute
Handling Outliers - Drop
Handling Imbalance of Target Variable - Resampling
Remove Duplicate values
Feature Scaling of High range Variables like Income variable
Categorical Encoding of Categorical features
Feature Selection based on multi-collinearity, zero or low variance.
Splitting the data into train - test.
​
