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

### Marital Status:
<div align=center><img width='600' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Marital%20Status.png'></div>
The dataset features three marital status: Married (673 employees), Single (470 employees), Divorced (327 employees).
Single employees show the largest proportion of leavers at 25%.

### Overtime:
<div align=center><img width='600' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Overtime.png'></div>
Some employees have overtime commitments. According to the chart, people who have to work overtime show higher proportion of leavers compared to their counterparts.

### Business Travel:
<div align=center><img width='600' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Business%20Travel.png'></div>
A preliminary look at the relationship between Business Travel frequency and Attrition Status shows that there is a largest normalized proportion of Leavers for employees that travel "frequently". Travel metrics associated with Business Travel status were not disclosed (i.e. how many hours of Travel is considered "Frequent").

### Number of Companies worked:
<div align=center><img width='600' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Num%20companies%20worked.png'></div>
There is a feature for the number of companies the employee has worked at. 0 likely indicates that according to records, the employee has only worked at this company.
Employees that have already worked at several companies previously (already "bounced" between workplaces) show higher proportion of leavers compared to their counterparts.

### Job Role:
<div align=center><img width='600' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Job%20Role.png'></div>
Employee who work as Sales Representatives show a significant percentage of Leavers in the submitted dataset.

### Pay/Salary & Job Involvement Information:
<div align=center><img width='600' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Monthly%20Income.png'></div>
Employee Monthly Income varies from $1009 to $19999.

<div align=center><img width='600' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Percent%20Salary.png'></div>
Percentage Salary Hikes varies from 11% to 25%.

<div align=center><img width='600' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Job%20Involvement.png'></div>
Loyal employees with higher salaries and more responsbilities show lower proportion of leavers compared to their counterparts.

### Years at company:
<div align=center><img width='600' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Years%20At%20Company.png'></div>
Number of Years at the company varies from 0 to 40 years.
<div align=center><img width='600' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Years%20in%20Current%20Role.png'></div>
Number of Years in the current role varies from 0 to 18 years. About 10% of leavers left when they reach their 2-year anniversary at the company.

### Target Variable: Attrition

