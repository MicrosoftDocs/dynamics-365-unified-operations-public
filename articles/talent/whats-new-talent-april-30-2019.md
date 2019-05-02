---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (April 30, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
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
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-04-30
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 for Talent (April 30, 2019)

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 for Talent: Attract.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 for Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2270. Numbers in parentheses in the headings refer to support numbers in Lifecycle Services (LCS).

### Provide feedback
The option to provide feedback is located under the help menu (**?**) in Talent. This menu provides access to the following resources:

- Feedback
- Help
- Get started
- Support
- Ideas
- About

### Improvements to the user interface for duplicate employee check
With this change, duplicates are detected as you enter name fields, and a status displays the number of duplicates found. You can select the provided link to open a new page to evaluate whether to use the detected match. To avoid interrupting data entry, the duplicates form doesn't automatically open.

### Common Data Service entity support for custom fields
With this week's release, the following entities support custom fields: Employment, Benefit type, and Pay cycle.

### Error when assigning an off-boarding checklist (299877)
This change corrects an error message that displays when assigning an offboarding checklist to an employee outside of the termination process.

### Exited workers link opens to wrong worker (309939)
This changes corrects an issue when you navigate to an employee from the exited workers list when rehiring an employee from another legal entity.      

### Employee self-service compensation card doesn't display summary values when advanced security is enabled (315231)
This change corrects an issue when using advanced compensation security. When advanced security is enabled, employee self service now displays the summary compensation amounts for both employees and managers. Prior to this change, summary values displayed as zero. 

### Creating a position without a title in Common Data Service fails to create the position in Talent (314562)
This week's changes correct an issue when creating positions in Common Data Service without providing a title.

### Error message in performance journal entries in employee self service (314134)
This change corrects an issue when attaching performance goals to performance journal entries in employee self service.

## In preview

### Allow reason codes to be specified on leave types
Organizations might need additional information about time-off requests. You can now specify reason codes for leave types and enable employees to select a reason code on their time-off requests.

### Require reason codes for certain leave types on time-off requests
Organizations might require reason codes for specific leave types when employees submit time off. This might be due to company policy or regulatory requirements. You can now specify which leave types require a reason code, and you can require employees to provide a reason code for the leave type on their time-off requests.

### Provide leave and absence transaction list for HR
Tracking employee time off and understanding how time off is calculated not only helps HR answer employee questions, but also ensures accurate time-off awards for employees. HR now has a new view into the transactions (grants, accruals, adjustments, and requests) to see the reasons behind balances.

## Coming soon

### Email support for alerts
With Platform update 26, users can create alert rules that automatically send email notifications to contacts when triggered by an event.
