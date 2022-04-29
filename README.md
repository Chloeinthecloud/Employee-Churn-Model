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
<div align=center><img width='600' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Attrition%20Distribution.png'></div>
As shown on the chart above, we can see this is an imbalanced class problem. Indeed, the percentage of Current Employees in the dataset is 83.9% and the percentage of Ex-employees is: 16.1%
Machine learning algorithms typically work best when the number of instances of each classes are roughly equal. I will have to address this target feature imbalance prior to implementing Machine Learning algorithms.

### Correlation
<div align=center><img width='700' height='500' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/heatmap.png'></div>
As shown above, "Monthly Rate", "Number of Companies Worked" and "Distance From Home" are positively correlated to Attrition; while "Total Working Years", "Job Level", and "Years In Current Role" are negatively correlated to Attrition.

### EDA Conclusion:
* The dataset does not feature any missing or erroneous data values, and all features are of the correct data type.
* The strongest positive correlations with the target features are: Performance Rating, Monthly Rate, Num Companies Worked, Distance From Home.
* The strongest negative correlations with the target features are: Total Working Years, Job Level, Years In Current Role, and Monthly Income.
* The dataset is imbalanced with the majoriy of observations describing Currently Active Employees.
### Other observations:
* Single employees show the largest proportion of leavers, compared to Married and Divorced counterparts.
* About 10% of leavers left when they reach their 2-year anniversary at the company.
* Loyal employees with higher salaries and more responsbilities show lower proportion of leavers compared to their counterparts.
* People who live further away from their work show higher proportion of leavers compared to their counterparts.
* People who travel frequently show higher proportion of leavers compared to their counterparts.
* People who have to work overtime show higher proportion of leavers compared to their counterparts.
* Employee who work as Sales Representatives show a significant percentage of Leavers in the submitted dataset.
* Employees that have already worked at several companies previously (already "bounced" between workplaces) show higher proportion of leavers compared to their counterparts.

## ML Models
The algorithms considered are: Logistic Regression, Random Forest, SVM, KNN, Decision Tree Classifier, Gaussian NB.
<div align=center><img width='700' height='500' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Algorithm%20ROC%20AUC%20Comparison.png'></div>
Area under ROC Curve (or AUC for short) is a performance metric for binary classification problems.
The AUC represents a model’s ability to discriminate between positive and negative classes. An area of 1.0 represents a model that made all predictions perfectly. An area of 0.5 represents a model as good as random.
Based on our ROC AUC comparison analysis, Logistic Regression and Random Forest show the highest mean AUC scores. I will shortlist these two algorithms for further analysis.

### Logistic Regression
Confusion Matrix:
<div align=center><img width='500' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Confusion%20matrix%20-%20Logistic%20Regression.png'></div>

Classification Report:
<div align=center><img width='500' height='150' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Classification%20Report1.png'></div>

### Random Forest
Confusion Matrix:
<div align=center><img width='500' height='400' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Confusion%20matrix%20-%20Random%20Forest.png'></div>

Classification Report:
<div align=center><img width='500' height='150' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Classification%20Report2.png'></div>

Feature Importance:
<div align=center><img width='700' height='600' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/Feature%20Importance.png'></div>
Random Forest helped us identify the Top 10 most important indicators (ranked in the table).

### ROC Graph:
<div align=center><img width='700' height='500' src = 'https://github.com/Chloeinthecloud/Employee-Churn-Model/blob/main/Plots/ROC%20Graph.png'></div>
AUC - ROC curve is a performance measurement for classification problem at various thresholds settings. ROC is a probability curve and AUC represents degree or measure of separability. It tells how much model is capable of distinguishing between classes. The green line represents the ROC curve of a purely random classifier; a good classifier stays as far away from that line as possible (toward the top-left corner).
As shown above, the fine-tuned Logistic Regression model showed a higher AUC score compared to the Random Forest Classifier.

## Conclusions:
### Risk Category
As the company generates more data on its employees (on New Joiners and recent Leavers) the algorithm can be re-trained using the additional data and theoritically generate more accurate predictions to identify high-risk employees of leaving based on the probabilistic label assigned to each feature variable (i.e. employee) by the algorithm.
Employees can be assigning a "Risk Category" based on the predicted label such that:
* Low-risk for employees with label < 0.6
* Medium-risk for employees with label between 0.6 and 0.8
* High-risk for employees with label > 0.8

### Strategic Retention Plan
From the project, we can known the stronger indicators of people leaving include:
* Monthly Income: people on higher wages are less likely to leave the company. Hence, efforts should be made to gather information on industry benchmarks in the current local market to determine if the company is providing competitive wages.
* Over Time: people who work overtime are more likelty to leave the company. Hence efforts must be taken to appropriately scope projects upfront with adequate support and manpower so as to reduce the use of overtime.
* YearsWithCurrManager: A large number of leavers leave 6 months after their Current Managers. By using Line Manager details for each employee, one can determine which Manager have experienced the largest numbers of employees resigning over the past year. Several metrics can be used here to determine whether action should be taken with a Line Manager:
  * number of employees under managers showing high turnover rates: this would indicate that the organisation's structure may need to be revisit to improve efficiency
  * number of years the Line Manager has been in a particular position: this may indicate that the employees may need management training or be assigned a mentor (ideally an Executive) in the organisation
  * patterns in the employees who have resigned: this may indicate recurring patterns in employees leaving in which case action may be taken accordingly.
* Age: Employees in relatively young age bracket 25-35 are more likely to leave. Hence, efforts should be made to clearly articulate the long-term vision of the company and young employees fit in that vision, as well as provide incentives in the form of clear paths to promotion for instance.
* DistanceFromHome: Employees who live further from home are more likely to leave the company. Hence, efforts should be made to provide support in the form of company transportation for clusters of employees leaving the same area, or in the form of Transportation Allowance. Initial screening of employees based on their home location is probably not recommended as it would be regarded as a form of discrimination as long as employees make it to work on time every day.
* TotalWorkingYears: The more experienced employees are less likely to leave. Employees who have between 5-8 years of experience should be identified as potentially having a higher-risk of leaving.
* YearsAtCompany: Loyal companies are less likely to leave. Employees who hit their two-year anniversary should be identified as potentially having a higher-risk of leaving.
