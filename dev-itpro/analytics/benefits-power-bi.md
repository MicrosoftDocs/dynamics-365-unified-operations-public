---
# required metadata

title: Benefits Power BI content
description: This topic describes the Benefits Power BI content. It explains how to access the reports that are included, and provides information about the data model and entities that were used to build the content.
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

# Benefits Power BI content

[!include[banner](../includes/banner.md)]



This topic describes the **Benefits** Power BI content. It explains how to access the reports that are included, and provides information about the data model and entities that were used to build the content.

## Accessing the Power BI content
The **Benefits** Power BI content is displayed in the **Benefits management** workspace for those using:
- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update
- Microsoft Dynamics 365 for Talent

## Reports that are included in the Power BI content pack
The reports that are included in the Power BI content have both charts and tables that contain additional information. The following table describes the reports.

| Report                     | Contents                                                                                                                              |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| Benefit Enrollment Overview  | Most and least enrolled plans, enrollment by employee group, selected benefit plan options |
| Employee Benefits | Employee enrollment by selected benefit  |
                                                                                             

You can filter the charts and tiles on these reports, and pin the charts and tiles to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure A Dashboard](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Extending the Power BI content
By using the content packs that are available in Microsoft Dynamics Lifecycle Services (LCS), you can provide great analytics to people who don't sign in to Microsoft Dynamics 365 for Operations, Enterprise edition. You can modify these content packs so that they include other reports or visuals, and then publish the content packs to your Power BI.com tenant for analysis.

You can find the **Benefits** Power BI content in the Shared assets library in LCS. For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md). To watch a demo that shows how to implement the Power BI content, see the [Power BI content from Microsoft and your partners in Dynamics Lifecycle Services](https://mix.office.com/watch/9puyb1b2xs1w) Office Mix.

## Understanding the data model and entities
The following data is used to populate the reports in the Power BI content. The following table shows the entities that the content was based on.

| Entity                            | Contents                                                                                                   | Relationships with other entities                                                                                                                                                                                                                                                                                                |
|-----------------------------------|------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Calendar Offset         | Calendar offsets to slice reports                                                                          | Past Position Assignment, Position Trend, Employee Trend, Terminated Employee                                                                                                                                                                                                                     |
| Company                | Companies to filter reports by                                                                             | Current Compensation, Current Employee, Terminated Employee, Employee Trend                                                                                                                                                                                                                        |
| Compensation           | Pay rate and frequency over time                                                                           | Current Compensation, Current Employee, Terminated Employee, Employee Trend                                                                                                                                                                                                                        |
| Current Compensation    | Pay rate and frequency as of the current date                                                              | Company, Compensation, Demographics, Job, Position                                                                                                                                                                                                                            |
| Current Position        | Positions as of the current date, full-time equivalent (FTE), open positions, and open-to-filled positions | Job, Position                                                                                                                                                                                                                                                                                               |
| Current Employee          | Workers as of the current date, age, and headcount                                                         | Company, Compensation, Geographic Location, Employee Name, Reports To, Employee Title, Demographics, Job, Employment, Position, Benefits                                            |
| Date                   | Days, weeks, months, and years                                                                             | Past Position Assignment, Position Trend, Terminated Employee, Employee Trend                                                           
| Demographics           | Date of birth, gender, ethnic origin, and marital status                                                   | Current Employee, Terminated Employee, Employee Trend                                                                                       
| Employment             | Start date, end date, and transition date                                                                  | Current Employee, Terminated Employee, Employee Trend                                                                                                                                                                                                                                                       |
| Geographic Location     | City, county, postal code, and state or province                                                           | Current Employee, Terminated Employee, Employee Trend                                                                                                                                                                                                                                                       |
| Job                    | Function, type, and title                                                                                  | Current Position, Current Employee                                                                                                                                                                                                                                                                              |
| Past Position Assignment | Assignment reason, start date, end date, and job                                                           | Calendar Offset, Date, Job, Position                                                                                                              
| Position               | Department, FTE, position, position type, and title                                                        | Current Position, Current Employee                                                                                                                                                                                                                                                                              |
| Position Trend          | Positions over time, FTE, and job                                                                          | Calendar Offset, Date, Job, Position                                                                                                                                                                                                                                                     |
| Reports To     | First name, last name, and full name                                                                       | Current Worker, Terminated Employee, Employee Trend                                                                                                                                                                                                                                                                                                                                                                              |
| Terminated Employee       | Terminated employees, termination date, title, position, and job                                             | Company, Compensation, Geographic Location,  Employee Name, Reports To, Calendar Offset, Date,  Employee Title, Demographics, Employment, Job, Position, Benefits |
| Benefits          | Effective date, benefit option, benefit plan, and benefit type                                             | Current Name, Terminated Employee, Employee Trend                                                                                                                                                                                                                                                       |
| Employee Name             | First name, last name, and full name                                                                       | Current Employee, Terminated Employee, Employee Trend                                                                                                                                                                                                                                                       |
| Employee Title            | Title and seniority date                                                                                   | Current Employee, Terminated Employee, Employee Trend                                                                                                                                                                                                                                                       |
| Employee Trend             | Workers over time, headcount, company, and position                                                        | Company, Compensation, Geographic Location, Employee Name, Reports To, Calendar Offset, Date, Employee Title, Demographics, Employment, Job, Benefits                     |

These entities were used to create calculated measures in the data model. These calculated measures are then used to calculate the key performance indicators (KPIs) and reports that are used in the content pack. If you want to include additional calculations on your reports and dashboard, you can download and modify the .pbix file from LCS. This file is the default data model that was used to create the content. After you've made modifications, you can create an organizational content pack and dashboard that contain the information that you’ve added.


