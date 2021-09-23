---
# required metadata

title: Organizational training Power BI content
description: This topic describes the Finance and Operations - Organizational training Power BI content.
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
ms.custom: 263874
ms.assetid: 45dbba14-aba6-4571-be0d-5d1aba3515d9
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Organizational training Power BI content

[!include [banner](../includes/banner.md)]

This topic describes the Finance and Operations - Organizational training Power BI content.

## Reports that are included in the content pack
After you've connected the content pack to your data, the reports show your organization's data. If you've never used Microsoft Power BI before, you can learn more about it on the [Guided Learning page for Power BI](https://powerbi.microsoft.com/guided-learning/?WT.mc_id=PBIService_GetData). The reports that are included in the content pack have both charts and tables that contain additional information. The following table describes the reports.

| Report          | Contents                                                                    |
|-----------------|-----------------------------------------------------------------------------|
| Course Analysis | Registration by location, course attendees by status, and registration list |
| Course Types    | Course types by skill                                                       |

You can filter the charts and tiles on these reports, and pin the charts and tiles to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure A Dashboard](https://powerbi.microsoft.com/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Understanding the data model and entities
Application data is used to populate the reports in the Organizational training content pack. The following table shows the entities that the content pack was based on.

| Entity                    | Contents                                                         | Relationships with other entities |
|---------------------------|------------------------------------------------------------------|-----------------------------------|
| Training\_CalendarOffset  | Calendar offsets to slice reports                                | Training\_CourseAgenda, Training\_CourseAttendees |
| Training\_Company         | Companies to filter reports by                                   | Training\_CourseAgenda, Training\_CourseAttendees |
| Training\_Course          | Course, description, instructor name, location, room, and status | Training\_CourseAgenda, Training\_CourseAttendees, Training\_CourseSkill |
| Training\_CourseAgenda    | Agenda, course, and start and end times                          | Training\_Company, Training\_CalendarOffset, Training\_Date, Training\_Course |
| Training\_CourseAttendees | Name, status, job, and registration date                         | Training\_Company, Training\_CalendarOffset, Training\_Date, Training\_Demographics, Training\_Employment, Training\_Course, Training\_WorkerName, Training\_WorkerTitle, Training\_Job, Training\_Position |
| Training\_CourseSkill     | Skill, skill type, and level                                     | Training\_Course |
| Training\_Date            | Days, weeks, months, and years                                   | Training\_CourseAgenda, Training\_CourseAttendees |
| Training\_Demographics    | Date of birth, gender, ethnic origin, and marital status         | Training\_CourseAgenda, Training\_CourseAttendees |
| Training\_Employment      | Start date, end date, and transition date                        | Training\_CourseAgenda, Training\_CourseAttendees |
| Training\_Job             | Function, type, and title                                        | Training\_CourseAgenda, Training\_CourseAttendees |
| Training\_Position        | Position, title, and full-time equivalent (FTE)                  | Training\_CourseAgenda, Training\_CourseAttendees |
| Training\_WorkerName      | First name, last name, and full name                             | Training\_CourseAttendees |
| Training\_WorkerTitle     | Title and seniority date                                         | Training\_CourseAttendees |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]