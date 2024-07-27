-- DROP TABLE IF EXISTS hr_data;
DROP TABLE IF EXISTS hr_data;
CREATE TABLE hr_data AS
SELECT
	Employee_ID,
    Employee_Name,
    Age,
    CASE 
        WHEN Age BETWEEN 20 AND 30 THEN '20-30'
        WHEN Age BETWEEN 31 AND 40 THEN '31-40'
        WHEN Age BETWEEN 41 AND 50 THEN '41-50'
        ELSE 'Other'
    END AS Age_Group,
    Years_of_Service,
    CASE 
        WHEN Years_of_Service BETWEEN 0 AND 2 THEN '0-2 Years'
        WHEN Years_of_Service > 2 AND Years_of_Service <= 5 THEN '2-5 Years'
        WHEN Years_of_Service > 5 AND Years_of_Service <= 10 THEN '5-10 Years'
        WHEN Years_of_Service > 10 AND Years_of_Service <= 15 THEN '10-15 Years'
        ELSE '15+ Years'
    END AS Experience_Category,
    CASE 
        WHEN Position IN ('DataAnalyst', 'Analyst') THEN 'Data Analyst'
        WHEN Position IN ('AccountExecutive', 'AccountExec.', 'Account Exec.') THEN 'Account Executive'
        ELSE Position 
    END AS Position,
    CASE 
        WHEN Gender = 'Female' THEN 'F'
        WHEN Gender = 'Male' THEN 'M'
        ELSE Gender 
    END AS Gender,
    Department,	
    Salary,	
    CASE 
        WHEN Salary BETWEEN 0 AND 100000 THEN '0-1 Lac'
        WHEN Salary BETWEEN 100001 AND 1000000 THEN '1-10 Lacs'
        WHEN Salary BETWEEN 1000001 AND 2000000 THEN '10-20 Lacs'
        WHEN Salary BETWEEN 2000001 AND 3000000 THEN '20-30 Lacs'
        WHEN Salary BETWEEN 3000001 AND 4000000 THEN '30-40 Lacs'
        WHEN Salary BETWEEN 4000001 AND 5000000 THEN '40-50 Lacs'
        WHEN Salary BETWEEN 5000001 AND 6000000 THEN '50-60 Lacs'
        WHEN Salary BETWEEN 6000001 AND 7000000 THEN '60-70 Lacs'
        WHEN Salary BETWEEN 7000001 AND 8000000 THEN '70-80 Lacs'
        WHEN Salary BETWEEN 8000001 AND 9000000 THEN '80-90 Lacs'
        WHEN Salary >= 9000001 THEN '90 Lacs-1 Cr'
        ELSE 'Above 1 Cr'
    END AS Income_Group,
    Performance_Rating,
    Work_Hours,
	Attrition,
	Promotion,
	Training_Hours,
    CASE 
        WHEN Training_Hours BETWEEN 0 AND 10 THEN '0-10 Hours'
        WHEN Training_Hours BETWEEN 11 AND 20 THEN '11-20 Hours'
        WHEN Training_Hours BETWEEN 21 AND 30 THEN '21-30 Hours'
        WHEN Training_Hours BETWEEN 31 AND 40 THEN '31-40 Hours'
        ELSE '40+ Hours'
    END AS Training_Hours_Category,
	Satisfaction_Score AS Employer_Satisfaction_Score,
	Education_Level,
	Employee_Engagement_Score,
	Absenteeism,
    CASE 
        WHEN Absenteeism BETWEEN 0 AND 5 THEN '0-5 Days'
        WHEN Absenteeism BETWEEN 6 AND 10 THEN '6-10 Days'
        WHEN Absenteeism BETWEEN 11 AND 15 THEN '11-15 Days'
        ELSE '15+ Days'
    END AS Absenteeism_Category,
	Distance_from_Work,
    CASE 
        WHEN Distance_from_Work BETWEEN 0 AND 10 THEN '0-10 kms'
        WHEN Distance_from_Work BETWEEN 11 AND 20 THEN '11-20 kms'
        WHEN Distance_from_Work BETWEEN 21 AND 30 THEN '21-30 kms'
        WHEN Distance_from_Work BETWEEN 31 AND 40 THEN '31-40 kms'
        ELSE '40+ kms'
    END AS Distance_from_Work_Category,
	JobSatisfaction_PeerRelationship,
	JobSatisfaction_WorkLifeBalance,
	JobSatisfaction_Compensation,
	JobSatisfaction_Management,
	JobSatisfaction_JobSecurity,
    (JobSatisfaction_PeerRelationship + 
	JobSatisfaction_WorkLifeBalance +
	JobSatisfaction_Compensation +
	JobSatisfaction_Management + 
	JobSatisfaction_JobSecurity) /5*100 AS Employee_Satisfaction_Score,
	EmployeeBenefit_HealthInsurance,
	EmployeeBenefit_PaidLeave,
	EmployeeBenefit_RetirementPlan,
	EmployeeBenefit_GymMembership,
	EmployeeBenefit_ChildCare,
    (EmployeeBenefit_HealthInsurance +
	EmployeeBenefit_PaidLeave +
	EmployeeBenefit_RetirementPlan +
	EmployeeBenefit_GymMembership +
	EmployeeBenefit_ChildCare)/5*100 AS EmployeeBenefitScore
FROM hr_analytics_dataset_adviti
WHERE Position != 'Intern' and Position NOT IN ('CEO', 'COO')
;

SELECT *
FROM hr_data
WHERE Position IN ('CEO', 'COO')
;

SELECT Position, Count(*)
FROM hr_analytics_dataset_adviti
GROUP BY Position;
-- 
SELECT Employee_Name, Position, Salary, Age, Years_of_Service, Age - Years_of_Service AS Diff FROM hr_analytics_dataset_adviti;

-- Hypothesis: Whether an Intern was hired or not
SELECT Employee_Name, Age, COUNT(*) AS Total
FROM hr_data
GROUP BY Employee_Name, Age
HAVING COUNT(*) > 1;
-- Conclusion: We can remove the interns data. 
-- SUMMARY
SELECT Attrition, COUNT(Employee_ID) AS Total_Attrition
FROM hr_data
GROUP BY Attrition;

SELECT 
	COUNT(Employee_ID) AS Total_Employees, 
    COUNT(CASE WHEN Attrition = 'Yes' THEN 1 ELSE NULL END) AS Attrition_count,
    ROUND(COUNT(CASE WHEN Attrition = 'Yes' THEN 1 ELSE NULL END)/COUNT(Employee_ID)*100,2) AS Attrition_rate,
    COUNT(CASE WHEN Attrition = 'No' THEN 1 ELSE NULL END) AS Total_Active_Employees,
    FORMAT(AVG(Salary),2) AS AvgSalary,
    ROUND(AVG(Employee_Satisfaction_Score))  AS AvgEmployeeSatisfactionScore
FROM hr_data;

SELECT 
	Attrition, 
    FORMAT(AVG(Salary),2) AS AvgSalary,
    ROUND(AVG(Performance_Rating)) AS AvgPerformanceRating,
    ROUND(AVG(Work_Hours)) AS AvgWorkHours,
    ROUND(AVG(Training_Hours)) AS AvgTrainingHours,
    ROUND(AVG(Employer_Satisfaction_Score))  AS AvgEmployerSatisfactionScore,
    ROUND(AVG(Employee_Engagement_Score))  AS AvgEmployeeEngagementScore,
    ROUND(AVG(Absenteeism))  AS AvgAbsenteeism,
    ROUND(AVG(Distance_from_Work))  AS AvgDistanceFromWork,
    ROUND(AVG(Employee_Satisfaction_Score))  AS AvgEmployeeSatisfactionScore,
    ROUND(AVG(EmployeeBenefitScore))  AS AvgEmployeeBenefitScore    
FROM hr_data
WHERE Attrition = 'Yes'
GROUP BY Attrition

UNION ALL

SELECT 
	Attrition, 
    FORMAT(AVG(Salary),2) AS AvgSalary,
    ROUND(AVG(Performance_Rating)) AS AvgPerformanceRating,
    ROUND(AVG(Work_Hours)) AS AvgWorkHours,
    ROUND(AVG(Training_Hours)) AS AvgTrainingHours,
    ROUND(AVG(Employer_Satisfaction_Score))  AS AvgEmployerSatisfactionScore,
    ROUND(AVG(Employee_Engagement_Score))  AS AvgEmployeeEngagementScore,
    ROUND(AVG(Absenteeism))  AS AvgAbsenteeism,
    ROUND(AVG(Distance_from_Work))  AS AvgDistanceFromWork,
    ROUND(AVG(Employee_Satisfaction_Score))  AS AvgEmployeeSatisfactionScore,
    ROUND(AVG(EmployeeBenefitScore))  AS AvgEmployeeBenefitScore    
FROM hr_data
WHERE Attrition = 'No'
GROUP BY Attrition
;

-- PROMOTION
SELECT 
	Promotion,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Yes,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS Attrition_No,
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %",
    ROUND((SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition No %"
FROM hr_data
GROUP BY promotion
;
-- Distance from work 
SELECT 
	Distance_from_Work_Category,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Yes,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS Attrition_No,
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %",
    ROUND((SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition No %"
FROM hr_data
GROUP BY Distance_from_Work_Category
;

-- department
SELECT 
	Department,
    COUNT(Employee_ID) AS TotalEmployees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Yes,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS Attrition_No,
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %",
    ROUND((SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition No %"
FROM hr_data
GROUP BY Department
;

-- Position
SELECT 
	Position,
    COUNT(Employee_ID) AS TotalEmployees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Yes,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS Attrition_No,
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %",
    ROUND((SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition No %"
FROM hr_data
GROUP BY Position
;
-- Gender
SELECT 
	Gender,
    COUNT(Employee_ID) AS TotalEmployees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Yes,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS Attrition_No,
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %",
    ROUND((SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition No %"
FROM hr_data
GROUP BY Gender
;

SELECT 
    COUNT(*) AS TotalEmployees,
    FORMAT(AVG(Salary),2) AS AvgSalary,
    ROUND(AVG(Performance_Rating)) AS AvgPerformanceRating,
    ROUND(AVG(Work_Hours)) AS AvgWorkHours,
    ROUND(AVG(Training_Hours)) AS AvgTrainingHours,
    ROUND(AVG(Employer_Satisfaction_Score))  AS AvgEmployerSatisfactionScore,
    ROUND(AVG(Employee_Engagement_Score))  AS AvgEmployeeEngagementScore,
    ROUND(AVG(Absenteeism))  AS AvgAbsenteeism,
    ROUND(AVG(Distance_from_Work))  AS AvgDistanceFromWork,
    ROUND(AVG(Employee_Satisfaction_Score))  AS AvgEmployeeSatisfactionScore,
    ROUND(AVG(EmployeeBenefitScore))  AS AvgEmployeeBenefitScore    
FROM hr_data
;


SELECT
    Department,
    Position,
    Gender,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS 'No',
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS 'Yes',
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %",
    COUNT(Employee_ID) AS 'Grand Total'
FROM
    hr_data
GROUP BY
    Department,
    Position,
    Gender
ORDER BY
    Department,
    Position,
    Gender;
--
SELECT
  Income_Group,
  SUM(CASE WHEN Gender = 'F' AND Attrition = 'No' THEN 1 ELSE 0 END) AS 'F_No',
  SUM(CASE WHEN Gender = 'F' AND Attrition = 'Yes' THEN 1 ELSE 0 END) AS 'F_Yes',
  SUM(CASE WHEN Gender = 'M' AND Attrition = 'No' THEN 1 ELSE 0 END) AS 'M_No',
  SUM(CASE WHEN Gender = 'M' AND Attrition = 'Yes' THEN 1 ELSE 0 END) AS 'M_Yes',
  COUNT(Employee_ID) AS 'Grand Total'
FROM
  hr_data
GROUP BY
  Income_Group
;

-- 

SELECT 
	Age_Group,
    COUNT(Employee_ID) AS TotalEmployees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Yes,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS Attrition_No,
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %",
    ROUND((SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition No %"
FROM hr_data
GROUP BY Age_Group
;

-- Employer satisfaction score v/s attrition
SELECT 
	EmployeeBenefit_RetirementPlan, Age_Group,
    COUNT(Employee_ID) AS TotalEmployees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Yes,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS Attrition_No,
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %"
FROM hr_data
GROUP BY EmployeeBenefit_RetirementPlan, Age_Group
;

-- Engagement score vs employee satisfaction score

SELECT 
	Employee_Engagement_Score, Round(Employee_Satisfaction_Score),
    COUNT(Employee_ID) AS TotalEmployees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Yes,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS Attrition_No,
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %"
FROM hr_data
GROUP BY Employee_Engagement_Score, Employee_Satisfaction_Score
;

-- jobpeer relation

SELECT 
	JobSatisfaction_PeerRelationship,
    COUNT(Employee_ID) AS TotalEmployees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Yes,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS Attrition_No,
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %"
FROM hr_data
GROUP BY JobSatisfaction_PeerRelationship
;

-- jobsecurity vs age group
SELECT 
	JobSatisfaction_JobSecurity,Age_Group,
    COUNT(Employee_ID) AS TotalEmployees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Yes,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS Attrition_No,
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %"
FROM hr_data
GROUP BY JobSatisfaction_JobSecurity,Age_Group
;

-- paid leave and attirition 
SELECT 
	EmployeeBenefit_PaidLeave,
    COUNT(Employee_ID) AS TotalEmployees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Yes,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS Attrition_No,
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %"
FROM hr_data
GROUP BY EmployeeBenefit_PaidLeave
;

-- education level experience positon comparision

SELECT 
	Experience_Category,
    COUNT(Employee_ID) AS TotalEmployees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Yes,
    SUM(CASE WHEN Attrition = 'No' THEN 1 ELSE 0 END) AS Attrition_No,
    ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*))*100) AS "Attrition Yes %"
FROM hr_data
GROUP BY Experience_Category
;

--

select * from hr_datA
