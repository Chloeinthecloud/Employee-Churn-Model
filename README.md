# Employee-Churn-Model: a HR Analytics Case Study
Employee churn is a costly problem for companies, and the true cost of replacing an employee can often be quite large. This is due to the amount of time spent to interview and find a replacement, sign-on bonuses, and the loss of productivity for several months while the new employee gets accustomed to the new role.

In this project, I will attempt to solve the following problems:

* What is the likelihood of an active employee leaving the company?
* What are the key indicators of an employee leaving the company?
* What policies or strategies can be adopted based on the results to improve employee retention?

## Data Description
In this project, a HR dataset was sourced from IBM HR Analytics Employee Attrition & Performance which contains employee data for 1,470 employees with various information about the employees. I will use this dataset to predict when employees are going to quit by understanding the main drivers of employee churn.
<div align=center><img width='800' height='600' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/histogram.png'></div>
A few observations can be made based on the information and histograms for numerical features:

* Many histograms are tail-heavy; indeed several distributions are right-skewed (e.g. MonthlyIncome DistanceFromHome, YearsAtCompany). 
* Data transformation methods may be required to approach a normal distribution prior to fitting a model to the data.
* Age distribution is a slightly right-skewed normal distribution with the bulk of the staff between 25 and 45 years old.
* EmployeeCount and StandardHours are constant values for all employees. They're likely to be redundant features.
* Employee Number is likely to be a unique identifier for employees given the feature's quasi-uniform distribution.



