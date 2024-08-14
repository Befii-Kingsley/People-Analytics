# People-Analytics

## People Analytics: Insights from Employee Data

### Data Source:
Data was gotten from Kaggle and Transformed with both Google Sheet and MS Excel.

### Tools used:
- Google Sheet and  Microsoft Excel : Data Cleaning and Entry
- PostgreSQL: Data Analysis
- Looker Data Studio and Powerbi : Data Reporting

### Introduction:
Data analytics is important in every sector, including Human Resources. 

Data analytics in Human Resources, also called People Analytics, helps us determine not only the impacts of employees on the business but also the impact the business has on its employees. 

By leveraging People Analytics, organizations can create a more resilient and sustainable corporate environment. This approach not only drives business success but also ensures that the company is a responsible and attractive employer, committed to the well-being of its employees and the broader community.

### Objectives:
The primary objective of this HR Analytics project is to provide a comprehensive understanding of the workforce dynamics, including onboarding and exit trends, employee demographics, length of service, and absenteeism. By achieving these objectives, an organization can enhance its HR strategies, promote a diverse and inclusive work environment, and improve overall employee satisfaction and retention.



### Methodology:
1. I started by loading the employee data into a PostgreSQL database. The data was then processed using a series of SQL queries to extract insights on demographics, turnover, absenteeism, diversity, and engagement. The results were visualized in Powerbi to create interactive and insightful dashboards. 
2. The next step involved utilizing data that was already in a Google Sheet, as it was a collaborative dataset. Instead of loading this data into PostgreSQL, I opted for a more straightforward approach by linking it directly to Looker Data Studio. This allowed for efficient visualization of the onboarding and exit information.
3. The insights derived from the data were then shared via a PowerPoint presentation, which included actionable points for further analysis and decision-making.

#### Data Analysis Process
##### -SQL QUERY:
PostgreSQL was used to extract insights on the Active employees in the company . The insights extracted were gender distribution, Age distribution, Length of Service, Absenteeism rate and correlation between Length of Service and Absenteeism. The insights gotten were downloaded in different sheets in an MS Excel workbook and linked to Power Bi.

``` sql
-- Created the Database using:

CREATE DATABASE hr_analytics;

-- Created Table using:

CREATE TABLE employees (
    EmployeeNumber SERIAL PRIMARY KEY,
    Surname VARCHAR(100),
    GivenName VARCHAR(100),
    FullName VARCHAR(200),
    Gender VARCHAR(1),
    City VARCHAR(100),
    JobTitle VARCHAR(100),
    Department VARCHAR(100),
    StoreLocation VARCHAR(100),
    Division VARCHAR(100),
    Age INT,
    ServiceYears INT,
    AbsentHours INT,
    BusinessUnit VARCHAR(100)
);
And loaded data from Excel file.

---Gender Distribution
SELECT Gender, COUNT(*) AS count
FROM employees
GROUP BY Gender;

--- Age Distribution by Generation

SELECT 
    CASE 
        WHEN Age BETWEEN 0 AND 26 THEN 'Gen Z'
        WHEN Age BETWEEN 27 AND 42 THEN 'Millennials'
        WHEN Age BETWEEN 43 AND 58 THEN 'Gen X'
        WHEN Age BETWEEN 59 AND 77 THEN 'Baby Boomers'
        ELSE 'Silent Generation'
    END AS generation,
    COUNT(*) AS count
FROM employees
GROUP BY generation
ORDER BY count DESC;

--- Age Distribution
SELECT Age, COUNT(*) AS count
FROM employees
GROUP BY Age;

--- Attendance and Absenteeism
SELECT Department, AVG(AbsentHours) AS avg_absent_hours
FROM employees
GROUP BY Department;

###### Full code is available on request
```
### Results
Full link to results, dashoard and report available here: https://swhytekings044.wixsite.com/datawithley/post/people-analytics-insights-from-employee-data

![Power Bi Dashboard 2](https://github.com/user-attachments/assets/5d1bee4f-62ba-4e75-a9f2-db9465b70cb7)

#### Insights:
1. The gender distribution is fairly balanced with 50.58% of the distribution and 49.42% female.
2. Majority of employees are Millennials. Most employees fall within the 25-45 age range, indicating a youthful workforce which could be beneficial for innovation and adaptability.
3. There is a fairly even distribution of genders across most job titles, although roles like Dairy Person and Produce Clerk show a higher proportion of male employees.

![Power Bi Dashboard 1](https://github.com/user-attachments/assets/1591ba63-adf0-4a3c-adee-f0a2e46bd92d)

#### Insights:
1. Mendez Linda has served the company the longest and should be rewarded in a way alongside the top 19 employees with highest service years.
2. Employees tend to leave the processing "meats, processed foods, dairy etc." departments more and may not get to move to managerial roles.
3. The Human Resources units have longer average service years compared to other departments indicating potential stability and lower turnover at the corporate level while Stores have shorter service years.

![Power Bi Dashboard 3](https://github.com/user-attachments/assets/48771e8d-257a-445f-9909-58695bda785b)

#### Insights:
1. There appears to be a negative correlation where employees with longer service years tend to have lower absenteeism, suggesting experienced employees may be more committed or have better job satisfaction compared to employees with lesser service years.
2. Dairy Manager role have high absenteeism rates with mostly lower service years, which is  point of concern. This position may have higher stress levels or other contributing factors to absenteeism and resignation.
3. The Human Resources units have longer average service years compared to other departments indicating potential stability and lower turnover at the corporate level while Stores have shorter service years.
4. Departments like 'Processed Foods' and 'Customer Service' have the highest average absent hours, which might indicate areas needing targeted wellness programs or workload assessments.

![Looker Dashboard 1](https://github.com/user-attachments/assets/56d62584-6968-4420-b4c1-e22d551c43c9)

#### Insights:
1. There is a steady onboarding trend with some fluctuations, suggesting periodic hiring drives or seasonal employment trends.
2. There was a significant drop in July 2024 with only 53 new hires, indicating a possible slowdown in recruitment.
3. A balanced gender distribution indicating a positive gender diversity within the organization, supporting inclusivity and equality.
4. The majority of onboarded employees are from Gen Z (62.7%) and Millennials (35.7%) indicates a young workforce, which can drive innovation and adapt quickly to changes.
5. Most onboarding occurred at the P0 job grade (425), indicating entry-level positions being filled. Higher job grades (P5, P6) have fewer onboardings, suggesting selective hiring for senior positions.

![Looker Dashboard 2](https://github.com/user-attachments/assets/c07d8abb-eeb9-4154-8fda-4faaedf24f2e)

#### Insights:
1. The total number of exited employees over the reviewed period is 940.The exit trend shows variability, with the highest exits in July 2024 (167). 
2. July has recorded more exit and lesser onboarding which is a point of concern with more of the attrition type being Resignation.
3. Most exits are due to resignations (154 in July 2024), with a smaller proportion due to terminations. 
4. The gender distribution of exited employees is slightly male-dominated with 53.3% male and 46.7% female. This balance suggests no significant gender bias in exits.



### Conclusion
This analysis provides a comprehensive overview of employee demographics, turnover, absenteeism, diversity, and engagement. The insights derived can help HR teams make data-driven decisions to improve employee satisfaction and organizational performance. By leveraging People Analytics, organizations can support corporate sustainability through enhanced well-being, diversity, efficient resource allocation, and strategic decision-making.

### Recommendation
1. Implement targeted retention strategies for departments with high turnover.
2. Enhance employee wellness programs to reduce absenteeism.
3. Promote diversity initiatives to maintain balanced gender representation.
4. Exit interviews for resigned employees can help address employee satisfaction and retention.



