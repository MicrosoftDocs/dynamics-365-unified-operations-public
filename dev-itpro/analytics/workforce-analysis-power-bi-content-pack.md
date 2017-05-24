---
# required metadata

title: Workforce metrics Power BI content
description: This topic describes the Dynamics 365 for Operations - Workforce Metrics Power BI content. It explains how to access the reports that are included in the content pack, and provides information about the data model and entities that were used to build the content pack.
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 264084
ms.assetid: 8e700583-3a7d-4f5f-9ac8-58c4feed1a02
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Workforce metrics Power BI content

[!include[banner](../includes/banner.md)]


This topic describes the **Workforce metrics** Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that were used to build the content.

## Accessing the Power BI content

Embedded Power BI allows individuals in your organization to take advantage of analytics out of the box. They can quickly analyze your data using the provided reports and visuals without having to model the data or create reports. You can also provide great analytics to those who do not log into Dynamics 365 by using the content packs available on Lifecycle Services (LCS). These content packs can be modified to include other reports or visuals, then published to your Power BI.com tenant for analysis. 

### Embedded content
If you're using Dynamics 365 for Finance and Operations, Enterprise edition, the **Workforce metrics** Power BI content is displayed in the **NAME** workspace.

### Content accessible from Lifecycle Services
If you are using Dynamics 365 for Operations version 1611 or Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update, you can find the **Workforce metrics** Power BI content in the Shared assets library in LCS. For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md). To watch a demo that shows how to implement the Power BI content, see the [Power BI content from Microsoft and your partners in Dynamics Lifecycle Services](https://mix.office.com/watch/9puyb1b2xs1w) Office Mix.

Be sure to download the **Workforce metrics** content that applies to the version of Dynamics 365 that you're using.


## Reports that are included in the Power BI content
The following table lists the metrics shown on each report.

| Report                                           | Metrics                                                                                                                                                                                                            |
|--------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Headcount Analysis Company, Department, Location | Headcount by company, headcount by department, headcount by location, and total headcount                                                                                                                           |
| Headcount Analysis Job, Step, Manager            | Headcount by job, headcount by step, headcount by manager, and total headcount                                                                                                                                      |
| Headcount Trend Analysis                         | Headcount this year versus last year by company and rolling headcount for the last 12 months                                                                                                                        |
| Workforce Demographics                           | Headcount by age and gender, headcount by ethnic origin, headcount by veteran status, headcount by marital status, number of full-time students, average tenure, average age, and ratio of female to male employees |
| Position Analysis                                | Open positions by department, open-to-filled positions, active-to-inactive positions, and positions by department                                                                                                   |
| Attrition Analysis                               | Attrition this year versus last year, attrition, average tenure of people leaving, average age of people leaving, and employees leaving by reason                                                                   |
| People by department                             | Employees with a personnel number by department, position, and assignment start and end dates                                                                                                                       |
| Seniority Analysis                               | Average years of service by company and seniority list                                                                                                                                                              |
| Anniversaries and Years of Service               | Employees by years of service, and anniversaries                                                                                                                                                                    |

You can filter the charts and tiles on these reports, and pin the charts and tiles to the dashboard. For more information about how to filter and pin in Power BI, see [Create and configure a dashboard](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Understanding the data model and entities
The following table shows the entities that the content pack was based on.

| Entity                            | Contents                                                                                                   | Relationships with other entities                                                                                                                                                                                                                                                                                                |
|-----------------------------------|------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Workforce\_CalendarOffset         | Calendar offsets to slice reports                                                                          | Workforce\_PastPositionAssignment Workforce\_PositionTrend Workorce\_WorkerTrend Workforce\_TerminatedWorker                                                                                                                                                                                                                     |
| Workforce\_Company                | Companies to filter reports by                                                                             | Workforce\_CurrentCompensation Workforce\_CurrentWorker Workforce\_TerminatedWorker Workorce\_WorkerTrend                                                                                                                                                                                                                        |
| Workforce\_Compensation           | Pay rate and frequency over time                                                                           | Workforce\_CurrentCompensation Workforce\_CurrentWorker Workforce\_TerminatedWorker Workorce\_WorkerTrend                                                                                                                                                                                                                        |
| Workforce\_CurrentCompensation    | Pay rate and frequency as of the current date                                                              | Workforce\_Company Workforce\_Compensation Workforce\_Demographics Workforce\_Job Workforce\_Position                                                                                                                                                                                                                            |
| Workforce\_CurrentPosition        | Positions as of the current date, full-time equivalent (FTE), open positions, and open-to-filled positions | Workforce\_Job Workforce\_Position                                                                                                                                                                                                                                                                                               |
| Workforce\_CurrentWorker          | Workers as of the current date, age, and headcount                                                         | Workforce\_Company Workforce\_Compensation Workforce\_GeographicLocation Workforce\_Performance Workforce\_WorkerName Workforce\_ReportsToWorkerName Workforce\_WorkerTitle Workforce\_Demographics Workforce\_Job Workforce\_Employment Workforce\_Position Workforce\_WorkerBenefit                                            |
| Workforce\_Date                   | Days, weeks, months, and years                                                                             | Workforce\_PastPositionAssignment Workforce\_PositionTrend Workforce\_TerminatedWorker Workorce\_WorkerTrend                                                                                                                                                                                                                     |
| Workforce\_Demographics           | Date of birth, gender, ethnic origin, and marital status                                                   | Workforce\_CurrentWorker Workforce\_TerminatedWorker Workorce\_WorkerTrend                                                                                                                                                                                                                                                       |
| Workforce\_Employment             | Start date, end date, and transition date                                                                  | Workforce\_CurrentWorker Workforce\_TerminatedWorker Workorce\_WorkerTrend                                                                                                                                                                                                                                                       |
| Workforce\_GeographicLocation     | City, county, postal code, and state or province                                                           | Workforce\_CurrentWorker Workforce\_TerminatedWorker Workorce\_WorkerTrend                                                                                                                                                                                                                                                       |
| Workforce\_Job                    | Function, type, and title                                                                                  | Workforce\_CurrentPosition Workforce\_CurrentWorker                                                                                                                                                                                                                                                                              |
| Workforce\_JobPerferredSkill      |                                                                                                            |                                                                                                                                                                                                                                                                                                                                  |
| Workforce\_PastPositionAssignment | Assignment reason, start date, end date, and job                                                           | Workforce\_CalendarOffset Workforce\_Date Workforce\_Job Workforce\_Position                                                                                                                                                                                                                                                     |
| Workforce\_Performance            | Rating, description, and rating model                                                                      | Workforce\_CurrentWorker Workforce\_TerminatedWorker Workorce\_WorkerTrend                                                                                                                                                                                                                                                       |
| Workforce\_PersonSkill            | Level and skill                                                                                            | Workforce\_Skill                                                                                                                                                                                                                                                                                                                 |
| Workforce\_PersonSkillAnalysis    | Certified, level, and skill                                                                                | Workforce\_Skill Workforce\_WorkerName                                                                                                                                                                                                                                                                                           |
| Workforce\_Position               | Department, FTE, position, position type, and title                                                        | Workforce\_CurrentPosition Workforce\_CurrentWorker                                                                                                                                                                                                                                                                              |
| Workforce\_PositionTrend          | Positions over time, FTE, and job                                                                          | Workforce\_CalendarOffset Workforce\_Date Workforce\_Job Workforce\_Position                                                                                                                                                                                                                                                     |
| Workforce\_ReportsToWorkerName    | First name, last name, and full name                                                                       | Workforce\_CurrentWorker Workforce\_TerminatedWorker Workorce\_WorkerTrend                                                                                                                                                                                                                                                       |
| Workforce\_Skill                  | Skill, skill type, and rating                                                                              | Workforce\_PersonSkill Workforce\_PersonSkillAnalysis                                                                                                                                                                                                                                                                            |
| Workforce\_TerminatedWorker       | Terminated workers, termination date, title, position, and job                                             | Workforce\_Company Workforce\_Compensation Workforce\_GeographicLocation Workforce\_Performance Workforce\_WorkerName Workforce\_ReportsToWorkerName Workforce\_CalendarOffset Workforces\_Date Workforce\_WorkerTitle Workforce\_Demographics Workforce\_Employment Workforce\_Job Workforce\_Position Workforce\_WorkerBenefit |
| Workforce\_WorkerBenefit          | Effective date, benefit option, benefit plan, and benefit type                                             | Workforce\_CurrentWorker Workforce\_TerminatedWorker Workorce\_WorkerTrend                                                                                                                                                                                                                                                       |
| Workforce\_WorkerName             | First name, last name, and full name                                                                       | Workforce\_CurrentWorker Workforce\_TerminatedWorker Workorce\_WorkerTrend Workforce\_PersonSkillAnalysis                                                                                                                                                                                                                        |
| Workforce\_WorkerTitle            | Title and seniority date                                                                                   | Workforce\_CurrentWorker Workforce\_TerminatedWorker Workorce\_WorkerTrend                                                                                                                                                                                                                                                       |
| Workorce\_WorkerTrend             | Workers over time, headcount, company, and position                                                        | Workforce\_Company Workforce\_Compensation Workforce\_GeographicLocation Workforce\_Performance Workforce\_WorkerName Workforce\_ReportsToWorkerName Workforce\_CalendarOffset Workforces\_Date Workforce\_WorkerTitle Workforce\_Demographics Workforce\_Employment Workforce\_Job Workforce\_WorkerBenefit                     |

These entities were used to create calculated measures in the data model. These calculated measures are then used to calculate the key performance indicators (KPIs) and reports that are used in the content pack. If you want to include additional calculations on your reports and dashboard, you can download and modify the CompensationandBenefits.pbix file from LCS. This file is the default data model that was used to create the content pack. After you've made modifications, you can create an organizational content pack and dashboard that contain the information that you’ve added.

## Additional resources
Here are some helpful links that are related to entities and building Power BI content:

-   [Data entities](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/09/power-bi-integration-with-entity-store-in-dynamics-ax-7-may-update/)
-   [Creating organizational content packs](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-organizational-content-packs-introduction/)
-   [Data modeling using Power BI](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-2-1-intro-modeling-data)
-   [Adding Power BI tiles to workspaces](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/07/06/pinning-power-bi-reports-to-dynamics-ax-client/)




