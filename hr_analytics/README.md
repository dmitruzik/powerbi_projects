<img width="1170" height="690" alt="hr_analytics" src="https://github.com/user-attachments/assets/fe511b67-b577-43ac-a4cc-f07cb7514208" />


<img width="1156" height="678" alt="active" src="https://github.com/user-attachments/assets/9e7f0bb3-3204-46e7-9c09-aca6718e32c6" />

-- MODELS:

<img width="1392" height="555" alt="model" src="https://github.com/user-attachments/assets/312b94b4-944c-4c45-b527-1c0ff2574b90" />


-- DAX Calculations

Amount of exit employee: 
ExitAmount = AVERAGE('employee_data'[ExitDate])

Work Life Balance:
% Average WL Balance = AVERAGE('employee_engagement_survey_data'[Work-Life Balance])/5

Engagement:
% Average Engagement = AVERAGE(employee_engagement_survey_data[Engagement]) / 5

Satisfaction:
% AverageSatisfaction = AVERAGE(employee_engagement_survey_data[Satisfaction]) / 5

Calendar:
Calendar = CALENDAR(MIN('employee_engagement_survey_data'[Survey Date]), MAX('employee_engagement_survey_data'[Survey Date]))


-- CONCLUSIONS:

Unswers for important questions:

What is the overall level of employee engagement and satisfaction?
The overall level of engagement is 59%. And the overall level of satisfaction is also 59%.

Are there specific departments or business units where engagement and satisfaction are below the company average?

The satisfaction level in Software Engineering is below the company average.
And the engagement level in Sales is also below the average.

How has work-life balance changed over the past year?
Work-life balance has fluctuated from 52% to 65% over the year.

How many employees have we lost, and can we see their performance metrics?
We have lost 123 employees. So we can see their performance metrics.

