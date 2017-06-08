---
# required metadata

title: Employee development Power BI content
description: This topic describes the Employee development Power BI content. It explains how to access the reports that are included , and provides information about the data model and entities that were used to build the content.
author: jcart1106 
manager: AnnBe
ms.date: 05/24/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User, IT Pro
# ms.devlang: 
# ms.reviewer: sericks
# ms.search.scope: Operations, Talent, Core
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: JCart
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Enterprise edition, July 2017 update 
---

# Employee development Power BI content

[!include[banner](../includes/banner.md)]

This topic describes the **Employee development** Power BI content. It explains how to access the reports that are included in the content, and provides information about the data model and entities that were used to build the content.

Accessing the content pack
--------------------------

If you're using Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update, you can find the **Employee development** content pack in the Shared assets library in Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download the content pack and connect it to your Microsoft Dynamics 365 for Operations data, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md).

## Reports that are included in the Power BI content
The reports that are included in the Power BI content have both charts and tables that contain additional information. The following table describes the reports.


| Report                            | Contents                                               |
|-----------------------------------|--------------------------------------------------------|
| Employee Development Overview     | Summary of other reports |
| Employee Skill Analysis           | Employee skill types and employee skills by type                |
| Employee Skill Level Analysis     | Employee skill levels by department, employees by skill level and skill type, lowest and highest levels per skill                |
| Skill Profile                     | Skill profile for the selected employee                |
| Skill Analysis                    | Skills by type and rating                              |
| Performance Rating Analysis       | Employees by lowest and highest rating by job, employee ratings by department, employees by rating and position type, highest and lowest ratings by position                              |
| Employee Performance Analysis     | Employee ratings for selected rating by manager                             |

You can filter the charts and tiles on these reports, and pin the charts and tiles to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure A Dashboard](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Understanding the data model and entities
| Entity                            | Contents                                                                                                   | Relationships with other entities                                                                                                                                                                                                                                                                                                |
|-----------------------------------|------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Calendar Offset         | Calendar offsets to slice reports                                                                          | Past Position Assignment, Position Trend, Employee Trend, Terminated Employee 
| Company                | Companies to filter reports by                                                                             | Current Employee, Terminated Employee, Employee Trend                                                                                     | Current Position                | Positions as of the current date, full-time equivalent (FTE), open positions, and open-to-filled positions                                                                             | Job, Position                                     
| Current Employee          | Workers as of the current date, age, and headcount                                                         | Company, Geographic Location,  Employee Name, Reports To, Employee Title, Demographics, Job, Employment, Position                             | Date                   | Days, weeks, months, and years                                                                             | Past Position Assignment Position Trend Terminated Employee Employee Trend                                                               | Demographics           | Date of birth, gender, ethnic origin, and marital status                                                   | Current Employee, Terminated, Employee, Employee Trend                                                                                      | Employment             | Start date, end date, and transition date                                                                  | Current Employee, Terminated Employee, Employee Trend                                                                                                                                                                                                                                                       |
| Geographic Location     | City, county, postal code, and state or province                                                           | Current Employee, Terminated Employee, Employee Trend                                                                                      | Job                    | Function, type, and title                                                                                  | Current Position, Current Employee                                                                                                                                                                                                                                                                              |
| Past Position Assignment | Assignment reason, start date, end date, and job                                                           | Calendar Offset, Date, Job, Position                                                                                                                                                                                           
| Position               | Department, FTE, position, position type, and title                                                        | Current Position, Current Employee                                                                                                                                                                                                                                                                              |
| Position Trend          | Positions over time, FTE, and job                                                                          | Calendar Offset, Date, Job, Position                                                                                                                                                                                                                                                     |
| Reports To     | First name, last name, and full name                                                                       | Current Employee, Terminated, Employee Employee Trend                                                               
| Terminated Employee       | Terminated workers, termination date, title, position, and job                                             | Company, Geographic Location, Employee Name, Reports To, Calendar Offset, Date, Employee Title, Demographics, Employment, Job, Position  |
| Employee Name            | First name, last name, and full name                                                                       | Current Worker, Terminated Employee, Employee Trend                                                                                                                                                                                                                        |
| Employee Title           | Title and seniority date                                                                                   | Current Employee, Terminated Employee, Employee Trend                                                                                                                                                                                                                                                       |
| Employee Trend          | Workers over time, headcount, company, and position                                                        | Company, Geographic Location, Employee Name, Reports To, Calendar Offset, Date, Employee Title, Demographics, Employment, Job                 |
| Job          | Function, type, title                                                       | Current Employee, Current Position, Employee Trend,  Job Preferred Skill, Past Position Assignment, Position Trend,  Terminated Employee              |
| Job Preferred Skill          |   Importance, rating, skill, and skill level                                                     | Job                 |                                                                                                                         
| Employee Skill Analysis          |   Certified, level, level date, and skill                                                     | Employee Name, Skill                  |  
| Performance          | Rating, description, and rating model                                                       | Current Employee, Current Position, Employee Trend,  Job Preferred Skill, Past Position Assignment, Position Trend,  Terminated Employee              |
|  Skill          |   Skill, skill type, and rating                                                     | Employee Skill Analysis, Job Preferred Skill                  |                                                                                                                        


These entities were used to create calculated measures in the data model. These calculated measures are then used to calculate the key performance indicators (KPIs) and reports that are used in the Power BI content. If you want to include additional calculations on your reports and dashboard, you can download and modify the .pbix file from LCS. This file is the default data model that was used to create the Power BI content pack. After you've made modifications, you can create an organizational content pack and dashboard that contain the information that you’ve added.


