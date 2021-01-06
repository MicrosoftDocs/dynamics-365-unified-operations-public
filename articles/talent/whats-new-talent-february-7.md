---
# required metadata

title: What's new or changed in Dynamics 365 Talent (February 7, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 02/07/2019
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
# ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-02-07
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (February 7, 2019)

This topic describes features that are either new or changed in Talent.

## Changes in Attract

### Interview scheduling enhancements
Improvements have been made to the end-to-end interview scheduling experience. You
can now see the calendar availability of an internal candidate and use the
internal candidate’s calendar for schedule recommendations. For more information, see [Interview scheduling and feedback](interview-scheduling-feedback.md).

### Job posting to LinkedIn – company mismatch issue fixed
An issue has been fixed where jobs posted to LinkedIn from Attract were appearing
under the wrong company name. For more information, see [Create, approve, and post jobs in Attract](creating-jobs-attract.md).

### Career site URL displayed in Admin settings
The career site home page URL is now displayed in **Admin Settings** under **Career
Site management**.

## Changes in Core HR

**Build 8.1.2134**

### Multiple compensation levels supported on jobs
This change allows for more than one compensation level to be defined on a job, enabling employee fixed compensation ranges which may differ between plans when using the same job. 

For example: 	
*Job* - Account Manager
*Associated compensation levels:* B1 and B2 - Each level has a defined range of values. B1 = Min 50,000, Mid 60,000, Max 75,000 and B2 = Min 65,000, Mid 74,000, Max 85,000. 
When creating fixed compensation for employees, based on the eligibility rules defined, each fixed plan can now point to the same job and to different levels on the job. This allows for plans to be defined in different regions/companies and point to the same job but different ranges without duplicating jobs to account for these differences.

### Compensation level field has been added to the Employee fixed compensation entity 
With this update, the employee fixed compensation entity has been updated to include the **Compensation level** field. This addition makes it easier to update employee fixed compensation plans. 

### Update Job family when updating and creating new positions
When changing the job on a position, **Job family** will now default based on the job selected.

### Performance improvements when rendering workspaces
Analytics tabs on workspaces will now load only when accessing those pages. An indicator will display during the initial rendering of the page in the upper-left corner of the page.
