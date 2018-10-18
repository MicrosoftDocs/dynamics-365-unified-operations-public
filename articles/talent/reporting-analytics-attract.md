---
# required metadata

title: Reporting and analytics in Attract
description: This topic provides information about the reporting and analytics features in MicrosoftDynamics 365 for Talent - Attract.
author: 
manager: AnnBe
ms.date: 10/18/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Reporting and analytics in Attract

[!include[banner](../includes/banner.md)]

Analytic reporting features in Attract provide insights about the organization's hiring process. Available features include:

-   **Job Analytics:** - View the metrics of a job's applicants on the **Analytics** tab.
-   **Analytics Hub:** - View aggregated metrics across all jobs by clicking **Analystics** on the left navigation pane.
-   **Role-level security:** - Access to reports is controlled by Attract [Roles](./security-attract.md) and the job participant role.
-   **Cross-filtering:** Use report visuals to view report metrics that are filtered by selected data.
-   **Export to Excel:** Download a Microsoft Excel sheet of the Attract data included in the report.
    
>[!IMPORTANT]
>Reports currently refresh every three hours. The timestamp of the most recent refresh is displayed above the report.

## Job Analytics

**Job analytics** reports are a snapshot of the hiring process for job. Key metrics include:

-   Active applicants
-   Applicant type (Internal vs External)
-   Applications over time

## Analytics hub

**Analytics Hub** reports aggregate job data to surface trends in the hiring process. Key metrics include:

-   Open jobs by seniority level
-   Rejected applicants by reason
-   Applicants across all jobs by stage

## Role-level security

Attract reports are accessible for Admin, Read-only, Recruiter, and Hiring manager roles. Unassigned users do not have access to the analyticreport pages, **Job Analytics** and **Analytics Hub**.

- **Job Analytics** reports display data for the selected job. Users with hiring manager and recruiter participant roles can access **Job Analytics** for the selected job. Admin and Read-only users can access **Job Analytics** for all jobs.
- **Analytics Hub** reports aggregate data across jobs where the user is a hiring manager or recruiter participant. Admin, Read-only, Recruiter, and Hiring manager roles can access the **Analytics Hub**.

To learn more about security roles, see [Security in Attract](./security-attract.md) topic.

## Cross-filter

Users can filter a report based on data selected in a visual. For example, clicking **Internal** in an applicant type visual filters the report for internal applicants. Tiles such as **Active applicants** will be filtered for internal, active applicants, and other visuals such as **Rejected applicants**, will highlight the portion corresponding to internal, rejected applicants.

## Export to Excel

To view **Attract data Excel**, users can click the ellipses on a visual and select **Export underlying data**.
