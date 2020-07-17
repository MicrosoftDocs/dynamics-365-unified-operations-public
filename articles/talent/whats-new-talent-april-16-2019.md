---
# required metadata

title: What's new or changed in Dynamics 365 Talent (April 16, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 04/16/2019
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
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-04-16
ms.dyn365.ops.version: Talent

---

# What's new or changed in Dynamics 365 Talent (April 16, 2019)

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

### Process auditing

You can now track the changes made to candidates, job openings, and job applications. For more information, see [Track changes in recruiting data](process-auditing.md).

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2239. Numbers in parentheses refer to support numbers in Lifecycle Services (LCS).

### Compensation region, Compensation level, Benefit option and Skill type entities in Common Data Service updated to include customer field support

With this release, these Common Data Service entities have been updated to include the ability to include custom field added through Talent: Core HR.

### PowerBI refresh issues (314342)

This change corrects an issue with PowerBI reports refreshing correctly.

### Unable to click directly through on transition tasks in employee self-service (303309)

This change enables users with the employee role to select and update transition tasks from the Talent to-do list.

### Performance feedback email message updated (309615)

With this change, a confirmation message displays when feedback is successfully submitted.

### Missing tables in Word template (308048)

With this change, when creating a Word template with employee and skill information, only the skills for the selected employee appear in the Word document.

### When applying an offboarding checklist an error is displayed. (299877)

This change corrects an issue when applying an offboarding checklist directly from the worker form.

## In preview

### Allow reason codes to be specified on leave types

Organizations might need additional information about time-off requests. You can now specify reason codes for leave types and enable employees to select a reason code on their time-off requests.

### Require reason codes for certain leave types on time-off requests

Organizations might require reason codes for specific leave types when employees submit time off. This might be due to company policy or regulatory requirements. You can now specify which leave types require a reason code, and you can require employees to provide a reason code for the leave type on their time-off requests.

### Provide leave and absence transaction list for HR

Tracking employee time off and understanding how time off is calculated not only helps HR answer employee questions, but also ensures accurate time-off awards for employees. HR now has a new view into the transactions (grants, accruals, adjustments, and requests) to see the reasons behind balances.

## Coming soon

### Improvements to the user interface for duplicate employee check

With this change, duplicates are detected as you enter name fields, and a status displays the number of duplicates found. You can select the provided link to open a new page to evaluate whether to use the detected match. To avoid interrupting data entry, the duplicates form doesn't automatically open.

### Email support for alerts

With Platform update 25 for Finance and Operations, users can create alert rules that automatically send email notifications to contacts when triggered by an event.


