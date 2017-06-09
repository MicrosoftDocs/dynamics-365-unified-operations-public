---
# required metadata

title: Learning Power BI content
description: This topic describes the Learning Power BI content. It explains how to access the reports, and provides information about the data model and entities that were used to build the content.
author: jcart1106 
manager: AnnBe
ms.date: 06/16/2017
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

# Learning Power BI content

[!include[banner](../includes/banner.md)]

This topic describes the **Learning** Microsoft Power BI content. It explains how to access the content, and describes the data model and entities that were used to build the content.

## Accessing the Power BI content

If you're using Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update, you can find the **Learning** Power BI content in the Shared assets library in Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md). To watch a demo that shows how to implement the Power BI content, see the [Power BI content from Microsoft and your partners in Dynamics Lifecycle Services](https://mix.office.com/watch/9puyb1b2xs1w) Office Mix.

## Reports that are included in the Power BI content

The reports that are included in the **Learning** Power BI content have both charts and tables that contain additional information. The following table describes the reports.

| Report                | Contents |
|-----------------------|----------|
| Learning Overview     | Summary of other reports |
| Course Analysis       | Registration by location, attendee by status, courses by type per company, and course attendance by job |
| Registration Analysis | Registration list |
| Course Types          | Course types by skill |
| Instructor Analysis   | Ratio of courses to instructors, number of instructors, courses by instructor, courses per instructor, and course agenda by instructor |
| Courses Offered       | List of courses |
| Courses Design        | Course agenda |

You can filter the charts and tiles on these reports, and pin the charts and tiles to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure A Dashboard](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Understanding the data model and entities

The following data is used to fill the reports in the **Learning** Power BI content. This table shows the entities that the content was based on.

| Entity           | Contents                                                         | Relationships with other entities |
|------------------|------------------------------------------------------------------|-----------------------------------|
| Calendar Offset  | Calendar offsets to slice reports                                | Course Agenda, Course Attendees |
| Company          | Companies to filter reports by                                   | Course Agenda, Course Attendees |
| Course           | Course, description, instructor name, location, room, and status | Course Agenda, Course Attendees, Course Skill |
| Course Agenda    | Agenda, course, and start and end times                          | Company, Calendar Offset, Date, Course |
| Course Attendees | Name, status, job, and registration date                         | Company, Calendar Offset, Date, Course, Demographics, Employment, Course, Employee Name, Employee Title, Job, Position |
| Course Skill     | Skill, skill type, and level                                     | Course |
| Date             | Days, weeks, months, and years                                   | Course Agenda, Course Attendees |
| Demographics     | Date of birth, gender, ethnic origin, and marital status         | Course Agenda, Course Attendees |
| Employment       | Start date, end date, and transition date                        | Course Agenda, Course Attendees |
| Job              | Function, type, and title                                        | Course Agenda, Course Attendees |
| Position         | Position, title, and full-time equivalent (FTE)                  | Course Agenda, Course Attendees |
| Employee Name    | First name, last name, and full name                             | Course Attendees |
| Employee Title   | Title and seniority date                                         | Course Attendees |

These entities were used to create calculated measures in the data model. These calculated measures are then used to calculate the key performance indicators (KPIs) and reports that are used in the content. If you want to include additional calculations on your reports and dashboard, you can download and modify the .pbix file from LCS. This file is the default data model that was used to create the content. After you've made modifications, you can create an organizational content pack and dashboard that contain the information that you’ve added.
