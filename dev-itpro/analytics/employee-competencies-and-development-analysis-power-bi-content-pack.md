---
# required metadata

title: Employee Competencies and Development Power BI content
description: This topic describes the Dynamics 365 for Operations - Employee Competencies and Development Power BI content. It explains how to access the reports that are included in the content pack, and provides information about the data model and entities that were used to build the content pack.
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 263894
ms.assetid: 7d375d8a-b2de-4bec-b575-93d1d4521b79
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Employee Competencies and Development Power BI content

This topic describes the Dynamics 365 for Operations - Employee Competencies and Development Power BI content. It explains how to access the reports that are included in the content pack, and provides information about the data model and entities that were used to build the content pack.

Accessing the content pack
--------------------------

You can find the Employee Competencies and Development content pack in the Shared assets library in Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download the content pack and connect it to your Microsoft Dynamics 365 for Operations data, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md).

## Reports that are included in the content pack
After you’ve connected the content pack to your Dynamics 365 for Operations data, the reports show your organization’s data. If you’ve never used Microsoft Power BI before, you can learn more about it on the [Guided Learning page for Power BI](https://powerbi.microsoft.com/en-us/guided-learning/?WT.mc_id=PBIService_GetData). The reports that are included in the content pack have both charts and tables that contain additional information. The following table describes the reports.

| Report                            | Contents                                               |
|-----------------------------------|--------------------------------------------------------|
| Competency & Development Analysis | Team member skill types and team member skills by type |
| Skill Profile                     | Skill profile for the selected employee                |
| Skill Analysis                    | Skills by type and rating                              |

You can filter the charts and tiles on these reports, and pin the charts and tiles to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure A Dashboard](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Understanding the data model and entities
Dynamics 365 for Operations data is used to populate the reports in the Employee Competencies and Development content pack. The following table shows the entities that the content pack was based on.

| Entity                            | Contents                                                                                                   | Relationships with other entities                                                                                                                                                                                                                                                                       |
|-----------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Workforce\_CalendarOffset         | Calendar offsets to slice reports                                                                          |                                                                                                                                                                                                                                                                                                         |
| Workforce\_Company                | Companies to filter reports by                                                                             |                                                                                                                                                                                                                                                                                                         |
| Workforce\_Compensation           | Pay rate and frequency over time                                                                           |                                                                                                                                                                                                                                                                                                         |
| Workforce\_CurrentCompensation    | Pay rate and frequency as of the current date                                                              | Workforce\_Company Workforce\_CurrentCompensation Workforce\_Demographics Workforce\_Job Workforce\_Position                                                                                                                                                                                            |
| Workforce\_CurrentPosition        | Positions as of the current date, full-time equivalent (FTE), open positions, and open-to-filled positions | Workforce\_Job Workforce\_Position                                                                                                                                                                                                                                                                      |
| Workforce\_CurrentWorker          | Workers as of the current date, age, and headcount                                                         | Workforce\_Company Workforce\_Compensation Workforce\_GeographicLocation Workforce\_Performance Workforce\_PersonSkill Workforce\_WorkerName Workforce\_ReportsToWorkerName Workforce\_WorkerTitle Workforce\_Demographics Workforce\_Job Workforce\_Employment Workforce\_Position                     |
| Workforce\_Date                   | Days, weeks, months, and years                                                                             |                                                                                                                                                                                                                                                                                                         |
| Workforce\_Demographics           | Date of birth, gender, ethnic origin, and marital status                                                   |                                                                                                                                                                                                                                                                                                         |
| Workforce\_Employment             | Start date, end date, and transition date                                                                  |                                                                                                                                                                                                                                                                                                         |
| Workforce\_GeographicLocation     | City, county, postal code, and state or province                                                           |                                                                                                                                                                                                                                                                                                         |
| Workforce\_Job                    | Function, type, and title                                                                                  |                                                                                                                                                                                                                                                                                                         |
| Workforce\_JobPreferredSkill      | Importance, rating, skill, and skill level                                                                 | Workforce\_Skill Workforce\_Job                                                                                                                                                                                                                                                                         |
| Workforce\_PastPositionAssignment | Assignment reason, start date, end date, and job                                                           | Workforce\_ClaendarOffset Workforce\_Date Workforce\_Job Workforce\_Position                                                                                                                                                                                                                            |
| Workforce\_Performance            | Rating, description, and rating model                                                                      |                                                                                                                                                                                                                                                                                                         |
| Workforce\_PersonSkill            | Level, level date, and skill                                                                               | Workforce\_Skill                                                                                                                                                                                                                                                                                        |
| Workforce\_PersonSkillAnalysis    | Certified, level, level date, and skill                                                                    | Workforce\_WorkerName Workforce\_Skill                                                                                                                                                                                                                                                                  |
| Workforce\_Position               | Department, FTE, position, position type, and title                                                        |                                                                                                                                                                                                                                                                                                         |
| Workforce\_PositionTrend          | Positions over time, FTE, and job                                                                          | Workforce\_CalendarOffset Workforce\_Date Workforce\_Job Workforce\_Position                                                                                                                                                                                                                            |
| Workforce\_ReportsToWorkerName    | First name, last name, and full name                                                                       |                                                                                                                                                                                                                                                                                                         |
| Workforce\_Skill                  | Skill, skill type, and rating                                                                              |                                                                                                                                                                                                                                                                                                         |
| Workforce\_TerminatedWorker       | Terminated workers, termination date, title, position, and job                                             | Workforce\_Company Workforce\_Compensation Workforce\_GeographicLocation Workforce\_Performance Workforce\_WorkerName Workforce\_ReportsToWorkerName Workforce\_CalendarOffset Workforces\_Date Workforce\_WorkerTitle Workforce\_Demographics Workforce\_Employment Workforce\_Job Workforce\_Position |
| Workforce\_WorkerName             | First name, last name, and full name                                                                       |                                                                                                                                                                                                                                                                                                         |
| Workforce\_WorkerTitle            | Title and seniority date                                                                                   |                                                                                                                                                                                                                                                                                                         |
| Workorce\_WorkerTrend             | Workers over time, headcount, company, and position                                                        | Workforce\_Company Workforce\_Compensation Workforce\_GeographicLocation Workforce\_Performance Workforce\_WorkerName Workforce\_ReportsToWorkerName Workforce\_CalendarOffset Workforces\_Date Workforce\_WorkerTitle Workforce\_Demographics Workforce\_Employment Workforce\_Job                     |

These entities were used to create calculated measures in the data model. These calculated measures are then used to calculate the key performance indicators (KPIs) and reports that are used in the content pack. If you want to include additional calculations on your reports and dashboard, you can download and modify the CompetenciesandDevelopment.pbix file from LCS. This file is the default data model that was used to create the content pack. After you've made modifications, you can create an organizational content pack and dashboard that contain the information that you’ve added.

## Additional resources
Here are some helpful links that are related to entities and building Power BI content:

-   [Data entities](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/09/power-bi-integration-with-entity-store-in-dynamics-ax-7-may-update/)
-   [Creating organizational content packs](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-organizational-content-packs-introduction/)
-   [Data modeling using Power BI](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-2-1-intro-modeling-data)
-   [Adding Power BI tiles to workspaces](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/07/06/pinning-power-bi-reports-to-dynamics-ax-client/)


