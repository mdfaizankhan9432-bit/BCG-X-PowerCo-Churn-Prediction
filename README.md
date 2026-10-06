# BCG X - PowerCo Customer Churn Prediction

A virtual work experience project from **BCG X on Forage**. I worked as a junior data scientist for a made-up energy company, **PowerCo**. The case and data came from the program. This was not a real job.

## The problem

PowerCo sells gas and electricity to small and medium businesses. Many of these customers were leaving for other providers (this is called churn). The company thought price might be the main reason. My job was to check this idea using data and build a model that can spot customers who are likely to leave.

## What I did

**Task 1: Understanding the data (EDA)**

I looked at 14,606 customers and about 193,000 monthly price records. About **9.7%** of customers had left (1,419 of 14,606). I also found that dates were stored as plain text, and that consumption and margin numbers were very uneven, with a few huge customers pulling the averages up.

**Task 2: Feature engineering**

I started with the manager's idea (the price difference between December and January) and built more on top of it: price changes for all six price columns, how long each customer has been with the company, usage and margin ratios, and log scaling for skewed numbers. I removed 23 columns that were almost copies of others. In the end I had 83 columns for each customer.

**Task 3: Random Forest model**

I trained a Random Forest model with 1,000 trees, and tested it on 3,652 customers it had never seen.
* Accuracy was 90%, but this is misleading because about 90% of customers stay anyway
* With the default settings, it found only **17 of 366** churners (recall about 5%)
* After lowering the alert threshold, flagging the riskiest ~13% of customers caught **35%** of all churners. That is about **2.6 times better** than picking customers at random

**Task 4: Executive summary**

I wrote a one-slide summary for senior leaders. My answer was: price sensitivity is **not confirmed** as the main reason for churn. Consumption and margin matter more, and no single price feature ranked at the top. The model is not strong enough yet, so I suggested a small pilot: offer discounts only to the highest-risk group, measure the saved revenue, and then scale up. I also suggested adding competitor prices and customer service data, and tuning the model to catch more churners.

## Files

* `01_EDA.ipynb`
* `02_Feature_Engineering.ipynb`
* `03_Random_Forest_Model.ipynb`
* `04_Executive_Summary.pdf`
* `05_Certificate.pdf`

## What I learned

* Accuracy can fool you when most customers belong to one group
* Recall and precision tell you what the business really needs to know
* Lowering the alert threshold can find more churners, but it also flags more customers by mistake
* A weak model is still a useful result if you explain it honestly
* Feature importance shows what the model uses, not what truly causes churn

## Note

This was a virtual program on Forage. The data was provided by the program and is not included in this repository. I added only the work I created myself.
