# PWC Power BI Virtual work experience-Call Center Performance Analysis
![image](https://github.com/user-attachments/assets/d079d5ad-a711-4f07-97d6-e489d005dbb0)

## Project Overview
This project focuses on analyzing call center data to gain valuable insights into its overall performance. By examining key metrics and trends, I aim to uncover patterns and evaluate the effectiveness of individual agents, ultimately providing actionable recommendations for improving customer service and operational efficiency.

## Table of Contents
- [Problem Statement](#problem-statement)
- [Data source](#data-source)
- [Tools](#tools)
- [Data Cleaning](#data-cleaning)
- [Data Modelling](#data-modelling)
- [Data Analysis](#data-analysis)
- [Data Visualization](#data-visualization)
- [Insights](#insights)

## Problem Statement
In this project, the goal is to develop a Power BI dashboard for the call center manager, showcasing all relevant Key Performance Indicators (KPIs) and metrics derived from the dataset.

Key KPIs may include:

- Overall customer satisfaction
- Total calls answered vs. abandoned
- Call volume by time of day
- Average speed of answer
- Agent performance quadrant: comparing average handle time (talk duration) against the number of calls answered


## Data Source
The dataset used for this task was presented by [Pwc](https://www.pwc.ch/en/careers-with-pwc/students/virtual-case-experience.html)
- Dataset: [Call Center Dataset](https://github.com/Anuoluwapo-04/Call-Center-Performance-Analysis/blob/main/01%20Call-Center-Dataset.xlsx)

## Tools
- Excel
- Power BI

## Data Cleaning
I transformed the data using Power Query and loaded the dataset into Microsoft Power BI Desktop for modeling.
The call center dataset has 10 columns and 5000 rows.

Data Cleaning for the dataset was done in the power query editor as follows:
- Replacing 'N/Y' with 'No/Yes'.
- Removed Unnecessary rows and columns.
- Each of the columns in the table were validated to have the correct data type.
- Developed calculated columns to derive essential dimensions for in-depth analysis.

## Data Modelling
I created a table for all my measures and a calendar table.
![image](https://github.com/user-attachments/assets/929166f3-a625-426b-8f94-892b2cc46b6b)

## Data Analysis
Measures used in all visualization are:
- Total Calls = COUNT('Call center'[Call Id])
- Total Calls Answered = CALCULATE([Total Calls],'Call center'[Answered (Y/N)]="Yes")
- Total Calls Abandoned = CALCULATE([Total Calls],'Call center'[Answered (Y/N)]="No")
- Average Speed of Answer = AVERAGE('Call center'[Speed of answer in seconds])
- Positive Satisfaction rating = sum('Call center'[Positive rating])
- % Customer Satisfaction = DIVIDE([Positive Satisfaction rating],[Total Calls],0)
- Total Agent = DISTINCTCOUNT('Call center'[Agent])
- % of calls Answered = DIVIDE([Total Calls Answered],[Total Calls],0)
- % of calls Abandoned = DIVIDE([Total Calls Abandoned],[Total Calls],0)
- Total Resolved Calls = CALCULATE([Total Calls],'Call center'[Resolved] = "Yes")
- Total Unresolved Calls = CALCULATE([Total Calls],'Call center'[Resolved] = "No")

some of the calculated columns  in the call center table are:

- Extractedhours = HOUR('Call center'[Time])

- Hourly calls = SWITCH(TRUE(),
'Call center'[Extractedhours] < 12, FORMAT('Call center'[Extractedhours],"0") & " " & "AM",
'Call center'[Extractedhours] = 12, "12 PM",
'Call center'[Extractedhours] > 12, FORMAT('Call center'[Extractedhours]-12, "0") & " " & "PM")

- Min and Sec duration = FORMAT('Call center'[Minutes],"00") & ":" & FORMAT('Call center'[Seconds],"00")

- Length of call = SWITCH(TRUE(),'Call center'[Min and Sec duration] < "00:59", "Less than 1 Min",
'Call center'[Min and Sec duration] <= "03:00", "1-3 Mins",
'Call center'[Min and Sec duration] <= "05:00", "4-5 Mins",
'Call center'[Min and Sec duration] <= "07:00", "6-7 Mins")

## Data Visualization

Data visualization for the data analysis (DAX) was done in Microsoft Power BI Desktop.
- Dashboard: [View Dashboard](https://github.com/Anuoluwapo-04/Call-Center-Performance-Analysis/blob/main/Call%20center%20Analysis%20Dashboard.pbix)

   ![image](https://github.com/user-attachments/assets/3de8d59b-7024-4ce3-a073-877c293d074a)

![image](https://github.com/user-attachments/assets/a0f3db32-73c4-4c38-878d-a7a56831087c)

## Insights
- The highest satisfaction rating was 3 and 4, with1,218 and 1,180 calls respectively.
- The most common call topics were Technical Support (20.44%) and Streamin (20.44%).
- The majority of calls come in the morning, between 9 AM and 11 AM.
- The majority of the calls (around 1,267) lasted between 4-5 minutes
- Monday had the highest call volume with 770 calls.
- The average speed of answer by Joe is the highest.
- Jim has the highest number of resolved calls even though the average speed of his answers is lower compared to those of Joe, Martha and Dan. He has has the highest number of answered calls.

## Recommendations
- With an 18.92% abandonment rate, consider adding callback options and optimizing staffing during peak hours to lower wait times.
- Address the variation in agents' average speed of answer (52-58 seconds) by sharing best practices and offering performance incentives.
- Focus on improving lower satisfaction ratings (1-3) by enhancing agent training and call handling procedures.
- Investigate the 1,354 unresolved calls to identify and address root causes, improving overall service quality.
- Provide targeted training for high-volume call topics like streaming, technical support, and payments to increase efficiency.
- Develop individualized coaching for agents based on performance data to help them improve specific skills.












