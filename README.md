# An Analysis of Engineering Salary Correlation to Skill Level and Tenure Length

The purpose of this analysis was to examine if tenure length or skill level affected salary for engineers, and if so, which had a stronger effect on salary. The general findings of this multiple linear regression analysis were that position/title related to skill level were more likely to have an impact on salary for engineers. This could have implications for engnineers working for the city who are looking to earn higher salaries, as well as for the City Department of Human Resources if they are looking to attract the best talent. 

## How Do Position and Tenure Length Affect Salary for Engineers in Baltimore?

For any organization looking to hire the most qualified people for a job and have the best outputs, it is important to ensure the best talent isn't overlooked or driven away by not being properly compensated. 

The strategy of rewarding more qualified workers with higher salaries is also a more effective and efficient approach of using company funds instead of rewarding people who have worked in the organization for longer. This method rewards quality of work and acts as investment in the advancement of workers who show potential as opposed to rewarding workers who simply have been there longer and may be satisifed in their position and have no motivation to progress and increase their value to the company. A related [study conducted in the UK](https://www-sciencedirect-com.proxy1.library.jhu.edu/science/article/pii/S0927537108001048) explored the realities and implications of increasing wages depending on seniority versus experience level. These results may also be pertinent to engineers such as myself searching for jobs, as they would prefer to work somewhere where the value they generate for the company is compensated over their length of employment by the organization. 

## Using Job Title, Hire Date, and Salary to Assess Correlation

Data was downloaded from the [Baltimore City open salary data website](https://data.baltimorecity.gov/widgets/6xv6-e66h) for Fiscal Year 2019 (FY2019). The data categories specifically used for analysis were job title, to reflect skill level, hire date, to reflect length of tenure, and gross and annual salary. Data was additionally filtered to only inlude numbers for people with "engineering" in the job title to allow for more specific results. 

"Job Levels" were artificilly determined by ordering all the different engineering job titles by their assumed importance and the assumed progression of positions in an organization, since it was not specified which positions were actually higher than others. Data analysis would have been more significant had progression throughout the entire pomotional hierarchy been available. Once ordering of the relative order of positions (entry, mid, and high) was determined, these positions translated into analyzable data by assigning numbers to every title based on order in the list. 

Hire date was translated into tenure length by calculating the number of days between the end of FY2019 and the hire date, and therefore provide the amount of time worked by that person in the organization. 

Gross and annual salary were not modified in any way, but analysis was conducted with both values to see if there were any meaningful differences. 

## Results Show that Job Level and Salary Have a Strong Correlation

|Coefficients|	Standard Error|	t Stat	|P-value|
| ---|---|---|---|
|Intercept	|27102.27767	|4839.874351	|5.59978952|	8.47226E-08|
|Eng_Job_Level|6067.256762	|466.6969461|	13.00042096|	2.84914E-27|
|Tenure_Length|	1.032291983|	0.227202355	|4.543491571	|1.04557E-05|
|DEPTID	|0.059149079|	0.079802057|	0.741197425	0.459596375|


•	What were the results of your data analysis and how did this contribute to your final solution?


