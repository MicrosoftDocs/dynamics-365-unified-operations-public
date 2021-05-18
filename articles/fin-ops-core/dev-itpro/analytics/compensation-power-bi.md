---
# required metadata

title: Compensation Power BI content
description: This topic describes the Compensation Power BI content. It explains how to access reports and provides information about the data model used.
author: jcart1106 
ms.date: 12/19/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  HcmCompensationWorkspace
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jcart
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: July 2017 update 
---

# Compensation Power BI content

[!include [banner](../includes/banner.md)]

This topic describes the **Compensation** Microsoft Power BI content. It explains how to access the reports, and provides information about the data model and entities that were used to build the content.

## Accessing the Power BI content
The **Compensation** Power BI content is shown in the **Compensation management** workspace if you use one of the following products:

- Finance and Operations apps
- Microsoft Dynamics 365 Human Resources

## Reports that are included in the Power BI content
The reports that are included in **Compensation** the Power BI content have both charts and tables that contain additional information. The following table describes the reports.

| Report                     | Contents |
|----------------------------|----------|
| Compensation Overview      | Summary of other reports |
| Compensation Analysis      | Hourly and salaried employees by company, total employees by compensation plan, male and female employees by compensation plan, and employee compensation by department |
| Position Pay Analysis      | Highest and lowest hourly and salary pay, positions with highest and lowest pay, and full-time and part-time positions |
| Compensation Plan Analysis | Employee enrollment by selected benefit |

You can filter the charts and tiles on these reports, and pin the charts and tiles to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure A Dashboard](https://powerbi.microsoft.com/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Understanding the data model and entities
The following data is used to fill the reports in the **Compensation** Power BI content. This table shows the entities that the content was based on.

| Entity                   | Contents                                                                                                   | Relationships with other entities |
|--------------------------|------------------------------------------------------------------------------------------------------------|-----------------------------------|
| Calendar Offset          | Calendar offsets to slice reports                                                                          | Past Position Assignment, Position Trend, Employee Trend, Terminated Employee |
| Company                  | Companies to filter reports by                                                                             | Current Compensation, Current Employee, Terminated Employee, Employee Trend |
| Compensation             | Pay rate and frequency over time                                                                           | Current Compensation, Current Employee, Terminated Employee, Employee Trend |
| Current Compensation     | Pay rate and frequency as of the current date                                                              | Company, Compensation, Demographics, Job, Position |
| Current Position         | Positions as of the current date, full-time equivalent (FTE), open positions, and open-to-filled positions | Job, Position |
| Current Employee         | Workers as of the current date, age, and headcount                                                         | Company, Compensation, Geographic Location, Employee Name, Reports To, Employee Title, Demographics, Job, Employment, Position, Benefits |
| Date                     | Days, weeks, months, and years                                                                             | Past Position Assignment, Position Trend, Terminated Employee, Employee Trend |
| Demographics             | Date of birth, gender, ethnic origin, and marital status                                                   | Current Employee, Terminated Employee, Employee Trend |
| Employment               | Start date, end date, and transition date                                                                  | Current Employee, Terminated Employee, Employee Trend |
| Geographic Location      | City, county, postal code, and state or province                                                           | Current Employee, Terminated Employee, Employee Trend |
| Job                      | Function, type, and title                                                                                  | Current Position, Current Employee |
| Past Position Assignment | Assignment reason, start date, end date, and job                                                           | Calendar Offset, Date, Job, Position |
| Position                 | Department, FTE, position, position type, and title                                                        | Current Position, Current Employee |
| Position Trend           | Positions over time, FTE, and job                                                                          | Calendar Offset, Date, Job, Position |
| Reports To               | First name, last name, and full name                                                                       | Current Worker, Terminated Employee, Employee Trend |
| Terminated Employee      | Terminated employees, termination date, title, position, and job                                           | Company, Compensation, Geographic Location, Employee Name, Reports To, Calendar Offset, Date, Employee Title, Demographics, Employment, Job, Position, Benefits |
| Benefits                 | Effective date, benefit option, benefit plan, and benefit type                                             | Current Name, Terminated Employee, Employee Trend |
| Employee Name            | First name, last name, and full name                                                                       | Current Employee, Terminated Employee, Employee Trend |
| Employee Title           | Title and seniority date                                                                                   | Current Employee, Terminated Employee, Employee Trend |
| Employee Trend           | Workers over time, headcount, company, and position                                                        | Company, Compensation, Geographic Location, Employee Name, Reports To, Calendar Offset, Date, Employee Title, Demographics, Employment, Job, Benefits |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]