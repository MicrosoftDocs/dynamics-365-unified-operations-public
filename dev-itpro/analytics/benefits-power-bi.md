---
# required metadata

title: Benefits Power BI content
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: jcart1106 
manager: AnnBe
ms.date: 05/24/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer: sericks
# ms.search.scope: Operations
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



This topic describes the Dynamics 365 for Finance and Operations - Benefits Power BI content. It explains how to access the reports that are included in the content pack, and provides information about the data model and entities that were used to build the content pack.

## Accessing the Power BI content

Embedded Power BI allows individuals in your organization to take advantage of analytics out of the box. They can quickly analyze your data using the provided reports and visuals without having to model the data or create reports. You can also provide great analytics to those who do not log into Dynamics 365 by using the content packs available on Lifecycle Services (LCS). These content packs can be modified to include other reports or visuals, then published to your Power BI.com tenant for analysis. 

### Embedded content

If you're using Dynamics 365 for Finance and Operations, Enterprise edition, the **Benefits** Power BI content is displayed in the **Benefits management** workspace.

### Content accessible from Lifecycle Services

If you are using Dynamics 365 for Operations version 1611 or Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update, you can find the **Benefits** Power BI content in the Shared assets library in LCS. For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md). To watch a demo that shows how to implement the Power BI content, see the [Power BI content from Microsoft and your partners in Dynamics Lifecycle Services](https://mix.office.com/watch/9puyb1b2xs1w) Office Mix.

Be sure to download the **Benefits** content that applies to the version of Dynamics 365 that you're using.

## Reports that are included in the content pack
After you’ve connected the content pack to your Dynamics 365 for Operations data, the reports show your organization’s data. If you’ve never used Microsoft Power BI before, you can learn more about it on the [Guided Learning page for Power BI](https://powerbi.microsoft.com/en-us/guided-learning/?WT.mc_id=PBIService_GetData). The reports that are included in the content pack have both charts and tables that contain additional information. The following table describes the reports.

| Report                     | Contents                                                                                                                              |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| Benefit Enrollment Overview  | Most and least enrolled plans, enrollment by employee group, selected benefit plan options |
| Employee Benefits | Employee enrollment by selected benefit  |
                                                                                             

You can filter the charts and tiles on these reports, and pin the charts and tiles to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure A Dashboard](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Understanding the data model and entities
Dynamics 365 for Operations data is used to populate the reports in the Compensation and Benefits content pack. The following table shows the entities that the content pack was based on.

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

These entities were used to create calculated measures in the data model. These calculated measures are then used to calculate the key performance indicators (KPIs) and reports that are used in the content pack. If you want to include additional calculations on your reports and dashboard, you can download and modify the CompensationandBenefits.pbix file from LCS. This file is the default data model that was used to create the content pack. After you've made modifications, you can create an organizational content pack and dashboard that contain the information that you’ve added.

## Additional resources
Here are some helpful links that are related to entities and building Power BI content:

-   [Data entities](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/09/power-bi-integration-with-entity-store-in-dynamics-ax-7-may-update/)
-   [Creating organizational content packs](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-organizational-content-packs-introduction/)
-   [Data modeling using Power BI](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-2-1-intro-modeling-data)
-   [Adding Power BI tiles to workspaces](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/07/06/pinning-power-bi-reports-to-dynamics-ax-client/)
