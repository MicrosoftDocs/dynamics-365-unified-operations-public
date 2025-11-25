--- 
# required metadata 
 
title: Expire jobs and titles (Preview)
description: This article describes how jobs and titles can be expired. 
author: ramagadu;twheeloc
ms.date: 11/25/2026
ms.topic: how-to 
 
# optional metadata 
 
ms.search.form: DefaultDashboard, HcmWorkforceWorkspace, HcmWorkerActivityChart, HcmAllWorkersListPart, HcmPosition, HcmPositionNewPosition, HcmJobLookup, HcmPositionReportsToDialog, HcmPositionLookup, FinancialDimensionDefaultTemplatesLookup, DimensionLookup, HcmPersonnelManagementWorkspace
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Expire jobs and titles (Preview)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]


> [!NOTE]
>  This feature is currently in preview. The functionality and behavior described here might change before general availability (GA).  
**This is prerelease documentation and is subject to change.**

## Overview

As organizations evolve, certain jobs and job titles may become obsolete. To help HR teams maintain clean data and reduce clutter, Dynamics 365 Human Resources lets you expire jobs and job titles. Expired items are removed from selection lists for new assignments while their historical records remain available for reporting and compliance.

### Key benefits

- **Streamlined data entry:** Expired jobs and titles no longer appear in dropdowns or selection lists when creating or updating positions.
- **Historical integrity:** Past assignments remain accessible for audits and reporting.
- **Improved data hygiene:** Keeps your catalog focused on current roles and reduces accidental assignments.

> [!IMPORTANT]
> To start to use this functionality, enable the **(Preview) Ability to expire jobs and job titles** feature in Feature management.

## Job expiry

Every job in Dynamics 365 Human Resources can be assigned an **expiration date**, which determines how long the job remains available for assignment. For example, a seasonal job might have an expiration date of **August 31, 2025**. The job is considered **active** until the expiration date is reached. After that date, the job status changes to **Expired**, and it is no longer available for new assignments.

- A job cannot be assigned to a position after its expiration date.
- A job remains active and available for assignment until the expiration date has passed.
- If there are active positions at the time of expiry, you'll see an informational message; no changes are made to existing positions.

### How to expire a job

1. Go to **Human Resources > Jobs > Active jobs**, and open the job you want to expire.
2. On the job details page, open the **Job duration** fast tab.
3. Create a **Job duration** and set the **Expiration date** to **today** or a **past date**.
4. Save your changes.

You can review or manage job durations from the action pane:

1. On the job page, select **Change timelines > Manage changes**.
2.  Go to the **Job duration** tab to view the saved durations.

### What happens after expiry

- Expired jobs are filtered from dropdowns and selection lists for new assignments.
- Historical assignments remain available for reporting and audits.
- Data exports include both active and expired jobs.


## Title expiry

Every title can be assigned an expiration date (today or in the past), which determines how long the title remains available for assignment to jobs.

- Expiring a title hides it from selection lists but does **not** change existing job or position assignments.
- If a title is still used by active jobs, you'll see a warning when you expire the title. The title will be hidden for new use, but current assignments remain unchanged.

### How to expire a title

1. Go to **Human Resources > Setup > Titles**.
2. Select the title you want to expire.
3. Set the **Expiration date** to **today** or a **past date** or click **Retire** on the action pane.
4. Save your changes.
5. The title's status updates to **Expired** and it is removed from selection lists for new assignments.

### What happens after expiry

- Expired titles are filtered out from dropdowns and selection lists.
- Historical records remain available for reporting and audits.
- Data exports include both active and expired titles.

## Best practices

- Review jobs and titles periodically to keep your catalog current.
- Expire jobs/titles as soon as they're no longer needed to prevent accidental assignments.
- Use filters (e.g., **Active jobs**, **Retired jobs**) to quickly find the right jobs when creating positions.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
