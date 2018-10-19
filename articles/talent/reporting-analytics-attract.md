---
# required metadata

title: Reporting and analytics in Attract
description: This topic provides information about the reporting and analytics features in Microsoft Dynamics 365 for Talent - Attract.
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

Analytic reporting features in Microsoft Dynamics 365 for Talent: Attract provide insights about the organization's hiring process. Here are some of the features that are available:

- **Job Analytics** – View the metrics of a job's applicants on the **Analytics** tab.
- **Analytics Hub** – View aggregated metrics across all jobs by selecting **Analytics** in the left navigation pane.
- **Role-level security** – Access to reports is controlled by Attract [roles](./security-attract.md) and the job participant role.
- **Cross-filtering** – Use report visuals to view report metrics that are filtered by selected data.
- **Export to Excel** – Download a Microsoft Excel workbook of the Attract data that is included on a report.

> [!IMPORTANT]
> Currently, reports are updated every three hours. The timestamp of the most recent update is shown above the report.

The following sections provide more information about each feature.

## Job Analytics

**Job Analytics** reports give a snapshot of the hiring process for a job. Here are some of the key metrics that are included:

- Active applicants
- Applicant type (Internal versus external)
- Applications over time

## Analytics Hub

**Analytics Hub** reports aggregate job data to reveal trends in the hiring process. Here are some of the key metrics that are included:

- Open jobs by seniority level
- Rejected applicants by reason
- Applicants across all jobs by stage

## Role-level security

Attract reports are accessible to users who are assigned to the Administrator, Read-only, Recruiter, or Hiring Manager role. Unassigned users don't have access to the analytic report pages, **Job Analytics** and **Analytics Hub**.

- **Job Analytics** reports show data for the selected job. Users who are assigned to the Hiring Manager or Recruiter role can access the **Job Analytics** report page for the selected job. Users who are assigned to the Administrator or Read-only role can access the **Job Analytics** report page for *all* jobs.
- **Analytics Hub** reports aggregate data across jobs where the user is a hiring manager or a recruiter. Users who are assigned to the Administrator, Read-only, Recruiter, or Hiring Manager role can access the **Analytics Hub** report page.

To learn more about security roles, see [Security and role management in Attract](./security-attract.md).

## Cross-filtering

Users can filter a report, based on data that is shown in a visual. For example, if **Internal** is selected as an applicant type, the report is filtered down to show only internal applicants. Therefore, the **Active applicants** tile is filtered for internal active applicants, whereas the **Rejected applicants** visual is filtered for  internal rejected applicants

## Export to Excel

To view Attract data in Excel, users can select the ellipses button (**...**) on a visual, and then select **Export underlying data**.
