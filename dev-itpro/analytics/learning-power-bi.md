---
# required metadata

title: Learning Power BI content
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

# Learning Power BI content

[!include[banner](../includes/banner.md)]


This topic describes the Dynamics 365 for Finance and Operations - Learning Power BI content. It explains how to access the content pack, and describes the data model and entities that were used to build the content pack.

Accessing the content pack
--------------------------

You can find the Organizational Training content pack in the Shared assets library in Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download the content pack and connect it to your Microsoft Dynamics 365 for Operations data, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md).

## Reports that are included in the content pack

After you’ve connected the content pack to your Dynamics 365 for Operations data, the reports show your organization's data. If you’ve never used Microsoft Power BI before, you can learn more about it on the [Guided Learning page for Power BI](https://powerbi.microsoft.com/en-us/guided-learning/?WT.mc_id=PBIService_GetData). The reports that are included in the content pack have both charts and tables that contain additional information. The following table describes the reports.

| Report          | Contents                                                                    |
|-----------------|-----------------------------------------------------------------------------|
| Learning Overview | Summary of other reports |
| Course Analysis   | Registration by location, attendee by status, courses by type per company, course attendance by job                                       |
| Registration Analysis | Registration list|
| Course Types    | Course types by skill                                                       |
| Instructor Analysis    | Ratio of courses to instructors, number of instructors, courses by instructor, courses per instructor, course agenda by instructor                                                       |
| Courses Offered    | List of courses|
| Courses Design    | Course agenda |

You can filter the charts and tiles on these reports, and pin the charts and tiles to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure A Dashboard](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Understanding the data model and entities

Dynamics 365 for Operations data is used to populate the reports in the Organizational Training content pack. The following table shows the entities that the content pack was based on.

| Entity                    | Contents                                                         | Relationships with other entities                                                                                                                                                                  |
|---------------------------|------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Calendar Offset  | Calendar offsets to slice reports                                | Course Agenda, Course Attendees                                                                                                                                                   |
| Company         | Companies to filter reports by                                   | Course Agenda, Course Attendees                                                                                                                                                   |
| Course          | Course, description, instructor name, location, room, and status | Course Agenda, Course Attendees, Course Skill                                                                                                                             |
| Course Agenda    | Agenda, course, and start and end times                          | Company, Calendar Offset, Date, Course                                                                                                                         |
| Course Attendees | Name, status, job, and registration date                         | Company, Calendar Offset, Date, Course, Demographics, Employment, Course, Employee Name, Employee Title, Job, Position |
| Course Skill     | Skill, skill type, and level                                     | Course                                                                                                                                                                                   |
| Date            | Days, weeks, months, and years                                   | Course Agenda, Course Attendees                                                                                                                                                   |
| Demographics    | Date of birth, gender, ethnic origin, and marital status         | Course Agenda, Course Attendees                                                                                                                                                   |
| Employment      | Start date, end date, and transition date                        | Course Agenda, Course Attendees                                                                                                                                                   |
| Job             | Function, type, and title                                        | Course Agenda, Course Attendees                                                                                                                                                   |
| Position        | Position, title, and full-time equivalent (FTE)                  | Course Agenda, Course Attendees                                                                                                                                                   |
| Employee Name      | First name, last name, and full name                             | Course Attendees                                                                                                                                                                          |
| Employee Title     | Title and seniority date                                         | Course Attendees                                                                                                                                                                          |

These entities were used to create calculated measures in the data model. These calculated measures are then used to calculate the key performance indicators (KPIs) and reports that are used in the content pack. If you want to include additional calculations on your reports and dashboard, you can download and modify the Training.pbix file from LCS. This file is the default data model that was used to create the content pack. After you've made modifications, you can create an organizational content pack and dashboard that contain the information that you’ve added.

## Additional resources
Here are some helpful links that are related to entities and building Power BI content:

-   [Data entities](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/09/power-bi-integration-with-entity-store-in-dynamics-ax-7-may-update/)
-   [Creating organizational content packs](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-organizational-content-packs-introduction/)
-   [Data modeling using Power BI](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-2-1-intro-modeling-data)
-   [Adding Power BI tiles to workspaces](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/07/06/pinning-power-bi-reports-to-dynamics-ax-client/)





