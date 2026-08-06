---
title: Learning Power BI content
description: Learn about Power BI content, including a table of reports that are included in the Power BI content and how to understand the data model and entities.
author: twheeloc
ms.author: twheeloc
ms.topic: concept-article
ms.date: 08/03/2026
ms.reviewer: twheeloc
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update
---

# Learning Power BI content

[!include [banner](../includes/banner.md)]

This article describes the **Learning** Microsoft Power BI content.

## Reports that are included in the Power BI content

The reports that are included in the **Learning** Power BI content have both charts and tables that contain additional information. The following table describes the reports.

| Report                | Contents |
|-----------------------|----------|
| Learning overview     | Summary of other reports |
| Course analysis       | Registration by location, attendee by status, courses by type per company, and course attendance by job |
| Registration analysis | Registration list |
| Course types          | Course types by skill |
| Instructor analysis   | Ratio of courses to instructors, number of instructors, courses by instructor, courses per instructor, and course agenda by instructor |
| Courses offered       | List of courses |
| Courses design        | Course agenda |

You can filter the charts and tiles on these reports, and pin the charts and tiles to the dashboard. For more information about how to filter and pin in Power BI, see [Create and Configure A Dashboard](https://powerbi.microsoft.com/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

## Understanding the data model and entities

The **Learning** Power BI content uses the following data to fill the reports. This table shows the entities that the content is based on.

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

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
