---
# required metadata

title: Use analytic reports in Attract
description: This topic describes the analytic reports for hiring process insights in Microsoft Dynamics 365 Talent - Attract
author: fewatson
manager: AnnBe
ms.date: 04/30/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: fewatson
ms.search.validFrom: 2019-04-30
ms.dyn365.ops.version: Talent April 2019 update

---

# Use analytic reports in Attract

[!include [banner](includes/banner.md)]

Analytic reports in Microsoft Dynamics 365 Talent: Attract provide an out-of-the-box (OOTB) solution for hiring process insights. Availabe features include:

- **Job analytics:** Click the **Analytics** tab within a job for metrics on the job's applicants.
- **Analytics hub:** Click **Analytics** on the left navigation for aggregated metrics across jobs.
- **User-specific security:** Access to reports is controlled by Attract [role](security-attract.md) and job participant role.
- **Cross-filtering:** Click visuals within a report to view other metrics filtered by selected data.

>[!NOTE] 
>- This feature is currently in [preview](access-preview-feature.md). To try it, you must have the [**Comprehensive Hiring Add-On**](attract-comprehensive-hiring.md).
>- All public preview reports are displayed in English.
>- Reports refresh every 3 hours. The last refresh time (in the local timezone) is located at the top of the report. Refresh times are an approximation and vary based on data volume and resource load in your region.

## Job Analytics

Job Analytics reports are a snapshot of the hiring process for a job.  Key metrics include:

- Active applicants by stage
- Applicant source
- Applicant type (internal or external)

## Analytics Hub

Analytics Hub reports aggregate data across jobs to surface trends in the hiring process. Attract includes two OOTB reports: Pipeline Summary and Funnel Analysis.

### Pipeline Summary

The Pipeline Summary report aggregates data for open jobs. Key metrics include:

- Applicants across all jobs by stage
- Applicant source
- Open jobs by seniority level

### Funnel Analysis

The Funnel Analysis report aggregates data for jobs that have been closed as filled. Key metrics include:

- Time to hire
- Conversion metrics (on hover)
- Offer acceptance rate

Note: For the most accurate time to hire reporting, it is recommended that you use [Offer management](offer-setup.md), a feature available as part of the Comprehensive Hiring Add-On.

>[!TIP] 
>Try hovering over visuals for additional information. For example, hovering over **Active applicants** visuals will display the average days in stage. Analyzing this information can provide insights critical to reducing time to hire and enable recruiters to focus on ways to reduce the time spent in each stage.

## User-specific security

Attract reports are accessible for Admin, Read All, Recruiter, and Hiring Manager [roles](security-attract.md). Unassigned users do not have access to either of the analytic report pages (Job Analytics or Analytics Hub).

Job Analytics reports display data for the selected job. Analytics Hub reports aggregate data across all jobs a user can view. Users that can view both My jobs and All jobs on the Jobs page have the same views available in the Analytics Hub.

## Cross-filter

One of the great features of Power BI is the way all visuals on a report page are interconnected. If you select a data point on one of the visuals, all the other visuals on the page that contain that data change, based on that selection. Find out more and see an example in [How visuals cross-filter each other in a Power BI report](https://docs.microsoft.com/power-bi/consumer/end-user-interactions).

## Export to Excel

To view report data in Excel, you can click the options menu (three dots) on a visual and select **Export underlying data**. Exported data will export as filtered, respecting user permissions in Attract. For more information, see [Export data from visualizations](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-export-data).
