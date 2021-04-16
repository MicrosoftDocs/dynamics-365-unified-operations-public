---
# required metadata

title: Recruiting Power BI content
description: This topic describes the Recruiting Power BI content.
author: jcart1106 
ms.date: 12/19/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmRecruitmentWorkspace
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 263934
ms.assetid: 38e6827b-0819-473c-bc47-821a1ec482b8
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Recruiting Power BI content

[!include [banner](../includes/banner.md)]

This topic describes the **Recruiting** Microsoft Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that were used to build the content.

## Accessing the Power BI content
The **Recruiting** Power BI content is shown in the **Recruitment management** workspace.

## Reports and visuals in the Recruitment management workspace
The **Recruitment management** workspace contains an **Analytics** tab. This tab contains the embedded Power BI content for recruiting. The content consists of an overview tab and additional tabs that contain details. The following table describes the reports on each tab.

| Report               | Contents |
|----------------------|----------|
| Recruitment Overview | Summarizes other reports |
| Applicant Analysis   | Total number of applicants, applicants by job, applicant sources, female to male applicants, and applicants by location |
| Applicant Status     | Applicants by type and status, and applicant status |
| Recruiting Analysis  | Net hire ratio, average days to hire, percentage of bad hires, recruiting costs, number of recruitment projects, hire to applied, and applicants versus openings by recruitment project |

## Understanding the data model and entities
You can filter the charts and tiles on these reports, and pin the charts and tiles to the dashboard. For more information about how to filter and pin in
Power BI, see [Create and Configure A Dashboard](https://powerbi.microsoft.com/guided-learning/powerbi-learning-4-2-create-configure-dashboards).

The following table shows the entities that the **Recruiting** Power BI content was based on.

| Entity               | Contents                                                         | Relationships with other entities |
|----------------------|------------------------------------------------------------------|-----------------------------------|
| Applicant            | Applicants, hired applicants, net hire ratio, and costs          | Applicant Name, Company, Calendar Offset, Date, Geographic Location, Demographics, Job, Media, Recruitment Project |
| Applicant Name       | Applicant first name, last name, and full name                   | Applicant, Employed Applicant, Terminated Applicant |
| Calendar Offset      | Calendar offsets to slice reports                                | Applicant, Employed Applicant, Terminated Applicant |
| Company              | Companies to filter reports by                                   | Applicant, Employed Applicant, Terminated Applicant |
| Date                 | Days, weeks, months, and years                                   | Applicant, Employed Applicant, Terminated Applicant |
| Demographics         | Date of birth, gender, ethnic origin, and marital status         | Applicant, Employed Applicant, Terminated Applicant |
| Employed Applicant   | Applicant, performance, start date, and applicant type           | Company, Calendar Offset, Date, Geographic Location, Applicant Name, Employment, Performance, Job, Media, Recruitment Project |
| Employment           | Start date, end date, and transition date                        | Applicant, Employed Applicant, Terminated Applicant |
| Geographic Location  | City, county, postal code, and state or province                 | Applicant, Employed Applicant, Terminated Applicant |
| Job                  | Function, type, and title                                        | Applicant, Employed Applicant, Terminated Applicant |
| Media                | Source of applicants                                             | Applicant, Employed Applicant, Terminated Applicant |
| Performance          | Rating, description, and rating model                            | Applicant, Employed Applicant, Terminated Applicant |
| Recruitment Project  | Project description, project status, and openings                | Applicant, Employed Applicant, Terminated Applicant |
| Terminated Applicant | Terminated applicants, reason, performance, and termination date | Company, Calendar Offset, Date, Geographic Location, Performance, Demographics, Employment, Media, Recruitment Project, Applicant Name |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]