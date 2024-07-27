# Empower HR: Unveling the secrets of Attrition and Trainig Efficancy
## Description
The HR department has initiated an analytics project to delve into the workforce data and uncover actionable insights that will contribute to enhanced employee engagement and optimized operational practices.
## Objective
-Identify Factors Influencing Employee Attrition
•	Objective: To pinpoint the underlying causes of employee turnover and propose data-backed strategies to bolster retention.

-Optimize Employee Training Programs
•	Objective: To suggest necessary changes those are to be made in training programs.

## Data preparation & Cleaning
The intial dataset contained several missing values and discerpancies. Data cleaning invoved:
- For the gender & position column, the values were updated to a more concise formate for easier handling in the future analyses. Specifically the transformation were:
  - 'Female' was replaced with 'F'
  - 'Male' was replaced with 'M'
  - 'DataScientist' was replaced with 'Data Scientist'
  - 'Marketinganalyst' was replaced with 'Marketing Analyst'
-For the purpose of more detailed analysis, the Age and Salary columns were categorized into different groups. These categorization were designed to facilitate subgroup analysis, enabling the identification of patterns or trends that might not be obvious when considering the entire data set
  - Age categories:
    - Less than or equal to 30 years
    - Greater than 30 years
  - Salary Categories:
    - 50k - 60k
    - 60k - 70k
    - 70k - 80k
    - 80k - 90k
    - 90k - 100k
- Converting the Last Promotion Date to standard date format.
## Analysis and Insights
#### Employee Attritation Analysis:
1) Diploma holders tend to go for higher education or better opportunities after earning on filed experience in companies. We can see that 59% of diploma holders have left the jobs.
2) Bachelor’s with higher experience tend to switch for better salary and higher position after gaining expertise in the field. Bachelors with 15+ years’ experience have left the company at 63% rate.
3) Employees who have done PHD and Masters seen leaving companies for better position and better salary hikes. Also, after certain points salary increment got saturated in the company.
![image](https://github.com/VishwasDevtale4/Empower-HR/assets/169833748/d9c237c7-ae49-4342-a448-ac2dcf9a30c0)


•	We have seen that there was no significant salary difference between 10-15 and 15+ years’ Experience Category   
![image](https://github.com/VishwasDevtale4/Empower-HR/assets/169833748/26e05728-4dad-4e24-9a19-8a47855e6ec7)


4) Attrition rates are higher when not promoted
   
![image](https://github.com/VishwasDevtale4/Empower-HR/assets/169833748/66ae0aae-9a91-4138-addb-2294f8d8ba78)

6) Department based attrition
   
![image](https://github.com/VishwasDevtale4/Empower-HR/assets/169833748/15352c73-5771-45f3-8bf7-216937886c63)

•	Sales department has the highest attrition of 57% followed by HR department.
•	Finance and IT has the lowest attrition rate.

6) Attrition based on position.

![image](https://github.com/VishwasDevtale4/Empower-HR/assets/169833748/9718dd5a-4150-4343-8bc0-742433263415)

•	We have observed highest attrition in software engineers (83%) and content creators (70%). 
•	Data scientist and data analyst have the lowest attrition rate.

7) Attrition based on training hours completed.

![image](https://github.com/VishwasDevtale4/Empower-HR/assets/169833748/e5f0dfba-8ee2-45d6-831d-eceb22fb3e7c)

•	Employees who have completed around 30-40 hours of training show the highest attrition rate.
•	One thing to note here is that average salary plays an important role in attrition of employees.
•	Point to observe here is that when employees got to salary what they dserve after giving time in training hours they were ready to serve for the company.

## Suggestions:-
  - Employees with higher experience are leaving the company at higher rates, this could be because of the promotion they are expecting Is not given to them. 
  - Sales department has the highest attrition of 57% followed by HR department. Need to examine the internal issue in these two particular departments which is affecting the attrition.
  - Training hours is not directly impacting the attrition as avg salary given plays a crucial role in this. Those who have done more hours and got certification might be expecting salary hike after devoting time in up skilling.
  - Employees who have done PHD and Masters seen leaving companies for better position and better salary hikes. Also, after certain points salary increment got saturated in the company.one to one communication with experienced and valuable resources should be conducted to understand the root cause of their resignation. 
  - We have observed highest attrition in software engineers (83%) and content creators (70%). These departments should be given free hand to show their creativity and innovation. This could be a prime reason for their attrition. 
