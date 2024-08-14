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

### Conclusion
This analysis provides a comprehensive overview of employee demographics, turnover, absenteeism, diversity, and engagement. The insights derived can help HR teams make data-driven decisions to improve employee satisfaction and organizational performance. By leveraging People Analytics, organizations can support corporate sustainability through enhanced well-being, diversity, efficient resource allocation, and strategic decision-making.

### Recommendation
1. Implement targeted retention strategies for departments with high turnover.
2. Enhance employee wellness programs to reduce absenteeism.
3. Promote diversity initiatives to maintain balanced gender representation.
4. Exit interviews for resigned employees can help address employee satisfaction and retention.



