# An Analysis of Engineering Salary Correlation to Skill Level and Tenure Length

The purpose of this analysis was to examine if tenure length or skill level affected salary for engineers, and if so, which had a stronger effect on salary. The general findings of this multiple linear regression analysis were that position/title related to skill level were more likely to have an impact on salary for engineers. This could have implications for engnineers working for the city who are looking to earn higher salaries, as well as for the City Department of Human Resources if they are looking to attract the best talent. 

## How Do Position and Tenure Length Affect Salary for Engineers in Baltimore?

For any organization looking to hire the most qualified people for a job and have the best outputs, it is important to ensure the best talent isn't overlooked or driven away by not being properly compensated. 

The strategy of rewarding more qualified workers with higher salaries is also a more effective and efficient approach of using company funds instead of rewarding people who have worked in the organization for longer. This method rewards quality of work and acts as investment in the advancement of workers who show potential as opposed to rewarding workers who simply have been there longer and may be satisifed in their position and have no motivation to progress and increase their value to the company. A related [study conducted in the UK](https://www-sciencedirect-com.proxy1.library.jhu.edu/science/article/pii/S0927537108001048) explored the realities and implications of increasing wages depending on seniority versus experience level. These results may also be pertinent to engineers such as myself searching for jobs, as they would prefer to work somewhere where the value they generate for the company is compensated over their length of employment by the organization. 

## Using Job Title, Hire Date, and Salary to Assess Correlation

[Raw data] (LINK)  was downloaded from the [Baltimore City open salary data website](https://data.baltimorecity.gov/widgets/6xv6-e66h) for Fiscal Year 2019 (FY2019). The data categories specifically used for analysis were job title, to reflect skill level, hire date, to reflect length of tenure, and gross and annual salary. Data was additionally filtered to only inlude numbers for people with "engineering" in the job title to allow for more specific results. 

"Job Levels" were artificilly determined by ordering all the different engineering job titles by their assumed importance and the assumed progression of positions in an organization, since it was not specified which positions were actually higher than others. Data analysis would have been more significant had progression throughout the entire pomotional hierarchy been available. Once ordering of the relative order of positions (entry, mid, and high) was determined, these positions translated into analyzable data by assigning numbers to every title based on order in the list. Department ID was used in the analysis to see if any relationship existed, but no logical relationship was found as the numbers for each department do not provide any actual numerical information. 

Hire date was translated into tenure length by calculating the number of days between the end of FY2019 and the hire date, and therefore provide the amount of time worked by that person in the organization. 

Gross and annual salary were not modified in any way, but analysis was conducted with both values to see if there were any meaningful differences. 

## Results Show that Job Level and Salary Have a Strong Correlation

Multiple linear regression was performed on the [raw data] (LINK) from [Open Baltimore] (LINK) comparing salary, job level, and time working for Baltimore City. The steps to perform this analysis are listed below:

1. Download Baltimore Open City Salary [Data](https://data.baltimorecity.gov/widgets/6xv6-e66h) for FY 2019
2. Create a new [document for analysis] (LINK) and tranfer the data into it so as to not affect the raw data file
3. Filter out the data for positions that are not for engineers
  * Created a column to the right of the data titled “Eng_Job_Title” and entered and equation, for example: `=IF(ISNUMBER(SEARCH("engineer",B2)),B2,0)` that would enter the job title if it had "engineering" somewhere in the JOBTITLE column and will return a value of 0 if the job title is not related to engineering
  * Used a filter on the new column Eng_Job_Title to hide all the columns that had "0" entered, as those were the non-engineering jobs
4. Job titles were then assigned their corresponding "Job Levels" using the following system
  * 1. Engineering Draft Tech 
  * 2. Engineering Associate I
  * 3. Engineering Associate II
  * 4. Engineering Associate III
  * 5. Engineer I
  * 6. Network Engineer
  * 7. Engineer II
  * 8. Operations Engineer
  * 9. Marine Engineer
  * 10. Supervising Enigneer
  * 11. Project Engineer
  * 12. Chief of Engineering
5. In a new column titled "Eng_Job_Level" each job title was assigned its numeric job level using the following code:
```
=IF(H404="Civil Engineering Draft Tech",1,IF(H404="Engineering Associate I",2, IF(H404="Engineering Associate II",3,IF(H404="Engineering Associate III",4, IF(H404="Engineer I",5,IF(ISNUMBER(SEARCH("Network",H404)),6,IF(H404="Engineer II",7,IF(ISNUMBER(SEARCH("Operations",H404)),8,IF(ISNUMBER(SEARCH("Marine",H404)),9,IF(ISNUMBER(SEARCH("Supervi",H404)),10,IF(ISNUMBER(SEARCH("Project",H404)),11,IF(ISNUMBER(SEARCH("Chief",H404)),12,0))))))))))))
```
6. The table was sorted by acesnding job level
7. The length of tenure for each person at their job from their hire date to the end of FY2019 (September 30, 2019) was caluclated in a new column labeled Tenure_Length
  *  A column was created with 09/30/2019 entered for each row to indicate the end of FY2019. The difference in time between HIRE_DT and FY2019_End was then calulcated using a simple subtraction equation between the two columns: `=F404-E404`
8. Multiple regression was then performed to see which variables are strong predictors of annual and gross salary
  * All variables that were to be analyzed were moved next to the salary column, and all values were ensured to be in number format to allow for analysis
  * The regression tool in the data analysis toolpak was used to perform the regression
  * Annual RT was selected as the input Y range (dependent variable)
  * All the data under DEPTID, Eng_Job_Level and Tenure_Length were selected as the input X range (independent variables)
  * The regression provided the following table of variables and coefficients as part of the output:
  
  | |Coefficients|	Standard Error|	t Stat	|P-value|
| :---:|:---:|:---:|:---:|:---:|
|**Intercept**	|37240.17581	|2154.893708	|17.28167644|	2.80555E-39|
|**Eng_Job_Level**|5388.331928	|207.7909961|	25.93149862|	5.64435E-61|
|**Tenure_Length**|	0.136162083|	0.101159015	|1.346020245	|0.180088199|
|**DEPTID**	|0.076274556|	0.035530871|	2.146712241	|0.033233813|
  
9. Multiple regression was repeated for Gross Salary to analyze any differences, and the regression provided the following table of variables and coefficients as part of the output:

| |Coefficients|	Standard Error|	t Stat	|P-value|
| ---|---|---|---|---|
|**Intercept**	|27102.27767	|4839.874351	|5.59978952|	8.47226E-08|
|**Eng_Job_Level**|6067.256762	|466.6969461|	13.00042096|	2.84914E-27|
|**Tenure_Length**|	1.032291983|	0.227202355	|4.543491571	|1.04557E-05|
|**DEPTID**	|0.059149079|	0.079802057|	0.741197425|	0.459596375|

10. For each independent variable (Job level, tenure, deptID) two scatter plots were made with the independent variable as the x-axis and the y-axis set to either Annual RT or Gross income, to see if there were any differences
  * Trendlines, equations, and r^2 values were added to the graphs
  * Chart title and axis titles were added
  








•	What were the results of your data analysis and how did this contribute to your final solution?


