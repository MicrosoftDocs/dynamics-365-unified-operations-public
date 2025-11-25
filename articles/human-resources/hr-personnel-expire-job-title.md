--- 
# required metadata 
 
title: Expire jobs and titles (preview)
description: This article describes how jobs and titles can be expired. 
author: ramagadu
ms.date: 11/25/2025
ms.topic: how-to 
 
# optional metadata 
 
ms.search.form: DefaultDashboard, HcmWorkforceWorkspace, HcmWorkerActivityChart, HcmAllWorkersListPart, HcmPosition, HcmPositionNewPosition, HcmJobLookup, HcmPositionReportsToDialog, HcmPositionLookup, FinancialDimensionDefaultTemplatesLookup, DimensionLookup, HcmPersonnelManagementWorkspace
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: ramagadu
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

# Expire jobs and titles (preview)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

## Overview

As organizations evolve, certain jobs and job titles may become obsolete. To help HR teams maintain clean data and reduce clutter, Dynamics 365 Human Resources lets you expire jobs and job titles. Expired items are removed from selection lists for new assignments while their historical records remain available for reporting and compliance.
To expire jobs and job titles, enable the **Ability to expire jobs, and job titles (preview)** feature in Feature management.  

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

### Key benefits

- Streamlined data entry - Expired jobs and titles no longer appear in dropdowns or selection lists when creating or updating positions.
- Historical integrity - Past assignments remain accessible for audits and reporting.
- Improved data hygiene - Keeps your catalog focused on current roles and reduces accidental assignments.

### Job expiry

Every job in Dynamics 365 Human Resources can be assigned an expiration date, which determines how long the job remains available for assignment. For example, a seasonal job might have an expiration date of August 31, 2025. The job is considered active until the expiration date is reached. After that date, the job status changes to **Expired**, and is no longer available for new assignments.

- A job can't be assigned to a position after its expiration date.
- A job remains active and available for assignment until the expiration date has passed.
- If there are active positions at the time of expiry, an informational message is displayed. No changes are made to existing positions.

### How to expire a job

To expire a job, follow these steps:
1. Go to **Human Resources > Jobs > Active jobs**, and open the job you want to expire.
2. On the job details page, open the **Job duration** FastTab.
3. In the **Job duration** field, set the **Expiration date** to **Today** or a **Past date**.
4. Save your changes.

To review or manage job durations from the action pane:
1. On the job page, select **Change timelines > Manage changes**.
2.  Go to the **Job duration** tab to view the saved durations.

After a job expires:
- Expired jobs are filtered from dropdowns and selection lists for new assignments.
- Historical assignments remain available for reporting and audits.
- Data exports include both active and expired jobs.


### Title expiry

Every title can be assigned an expiration date (today or in the past), which determines how long the title remains available for assignment to jobs.

- Expiring a title hides it from selection lists but doesn't change existing job or position assignments.
- If a title is still used by active jobs, you see a warning when you expire the title. The title is hidden for new jobs, but current assignments remain unchanged.

### How to expire a title

To expire a title, follow these steps:
1. Go to **Human Resources > Setup > Titles**.
2. Select the title to expire.
3. Set the **Expiration date** to **today** or a **past date** or click **Retire** on the action pane.
4. Save your changes.
5. The title's status changes to **Expired** and is removed from selection lists for new assignments.

After a title expires:
- Expired titles are filtered out from dropdowns and selection lists.
- Historical records remain available for reporting and audits.
- Data exports include both active and expired titles.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
