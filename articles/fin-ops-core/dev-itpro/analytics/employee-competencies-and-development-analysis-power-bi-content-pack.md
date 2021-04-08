---
# required metadata

title: Employee competencies and development Power BI content
description: This topic describes the Employee competencies and development Power BI content. 
author: jcart1106
ms.date: 12/19/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 263894
ms.assetid: 7d375d8a-b2de-4bec-b575-93d1d4521b79
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Employee competencies and development Power BI content

[!include [banner](../includes/banner.md)]

This topic describes the Employee competencies and development Power BI content. 

## Reports that are included in the content pack
After you've connected the content pack to your data, the reports show your organization's data. If you've never used Microsoft Power BI before, you can learn more about it on the [Guided Learning page for Power BI](https://powerbi.microsoft.com/guided-learning/?WT.mc_id=PBIService_GetData). The reports that are included in the content pack have both charts and tables that contain additional information. The following table describes the reports.

| Report                            | Contents                                               |
|-----------------------------------|--------------------------------------------------------|
| Competency & Development Analysis | Team member skill types and team member skills by type |
| Skill Profile                     | Skill profile for the selected employee                |
| Skill Analysis                    | Skills by type and rating                              |

You can filter the charts and tiles on these reports, and pin the charts and tiles to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure A Dashboard](https://powerbi.microsoft.com/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Understanding the data model and entities
Application data is used to populate the reports in the Employee competencies and development content pack. The following table shows the entities that the content pack was based on.

| Entity                            | Contents                                                                                                   | Relationships with other entities |
|-----------------------------------|------------------------------------------------------------------------------------------------------------|-----------------------------------|
| Workforce\_CalendarOffset         | Calendar offsets to slice reports                                                                          | |
| Workforce\_Company                | Companies to filter reports by                                                                             | |
| Workforce\_Compensation           | Pay rate and frequency over time                                                                           | |
| Workforce\_CurrentCompensation    | Pay rate and frequency as of the current date                                                              | Workforce\_Company, Workforce\_CurrentCompensation, Workforce\_Demographics, Workforce\_Job, Workforce\_Position |
| Workforce\_CurrentPosition        | Positions as of the current date, full-time equivalent (FTE), open positions, and open-to-filled positions | Workforce\_Job Workforce\_Position |
| Workforce\_CurrentWorker          | Workers as of the current date, age, and headcount                                                         | Workforce\_Company Workforce\_Compensation, Workforce\_GeographicLocation, Workforce\_Performance, Workforce\_PersonSkill, Workforce\_WorkerName, Workforce\_ReportsToWorkerName, Workforce\_WorkerTitle, Workforce\_Demographics, Workforce\_Job, Workforce\_Employment, Workforce\_Position |
| Workforce\_Date                   | Days, weeks, months, and years                                                                             | |
| Workforce\_Demographics           | Date of birth, gender, ethnic origin, and marital status                                                   | |
| Workforce\_Employment             | Start date, end date, and transition date                                                                  | |
| Workforce\_GeographicLocation     | City, county, postal code, and state or province                                                           | |
| Workforce\_Job                    | Function, type, and title                                                                                  | |
| Workforce\_JobPreferredSkill      | Importance, rating, skill, and skill level                                                                 | Workforce\_Skill, Workforce\_Job |
| Workforce\_PastPositionAssignment | Assignment reason, start date, end date, and job                                                           | Workforce\_CalendarOffset, Workforce\_Date, Workforce\_Job, Workforce\_Position |
| Workforce\_Performance            | Rating, description, and rating model                                                                      | |
| Workforce\_PersonSkill            | Level, level date, and skill                                                                               | Workforce\_Skill |
| Workforce\_PersonSkillAnalysis    | Certified, level, level date, and skill                                                                    | Workforce\_WorkerName, Workforce\_Skill |
| Workforce\_Position               | Department, FTE, position, position type, and title                                                        | |
| Workforce\_PositionTrend          | Positions over time, FTE, and job                                                                          | Workforce\_CalendarOffset, Workforce\_Date, Workforce\_Job, Workforce\_Position |
| Workforce\_ReportsToWorkerName    | First name, last name, and full name                                                                       | |
| Workforce\_Skill                  | Skill, skill type, and rating                                                                              | |
| Workforce\_TerminatedWorker       | Terminated workers, termination date, title, position, and job                                             | Workforce\_Company, Workforce\_Compensation, Workforce\_GeographicLocation, Workforce\_Performance, Workforce\_WorkerName, Workforce\_ReportsToWorkerName, Workforce\_CalendarOffset, Workforces\_Date, Workforce\_WorkerTitle, Workforce\_Demographics, Workforce\_Employment, Workforce\_Job, Workforce\_Position |
| Workforce\_WorkerName             | First name, last name, and full name                                                                       | |
| Workforce\_WorkerTitle            | Title and seniority date                                                                                   | |
| Workorce\_WorkerTrend             | Workers over time, headcount, company, and position                                                        | Workforce\_Company, Workforce\_Compensation, Workforce\_GeographicLocation, Workforce\_Performance, Workforce\_WorkerName, Workforce\_ReportsToWorkerName, Workforce\_CalendarOffset, Workforces\_Date, Workforce\_WorkerTitle, Workforce\_Demographics, Workforce\_Employment, Workforce\_Job |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]