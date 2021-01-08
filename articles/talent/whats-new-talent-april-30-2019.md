---
# required metadata

title: What's new or changed in Dynamics 365 Talent (April 30, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
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
# ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-04-30
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (April 30, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

The changes that are described in this section apply to build number 8.1.2270. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### Provide feedback

The option to provide feedback is located on the **Help** menu (**?**) in Talent. This menu provides access to the following resources:

- Feedback
- Help
- Get started
- Support
- Ideas
- About

### Improvements to the user interface for duplicate employee detection

Because of this change, duplicates are now detected as you set name fields, and a status indicator shows the number of duplicates that have been detected. A link that is provided opens a page where you can evaluate whether you should use one of the duplicates. To avoid interrupting data entry, the duplicates page isn't automatically opened. You must select the link to open the page.

### Common Data Service entity support for custom fields

In this week's release, the following entities now support custom fields: Employment, Benefit type, and Pay cycle.

### An error occurs when an off-boarding checklist is assigned (299877)

This change corrects an error message that appears when you assign an offboarding checklist to an employee outside the termination process.

### The exited workers link opens the wrong worker (309939)

This change corrects an issue that occurs when you're rehiring an employee from another legal entity and try to go to the employee from the exited workers list.

### The employee self-service compensation card doesn't show summary values when advanced security is turned on (315231)

This change corrects an issue that occurs when you use advanced compensation security. When advanced security is turned on, employee self-service now shows the summary compensation amounts for both employees and managers. Before this change, summary values appeared as 0 (zero).

### If a position without a title is created in Common Data Service, no position is created in Talent (314562)

This week's changes correct an issue that occurs when you create positions in Common Data Service but don't provide a title.

### Error message in performance journal entries in employee self-service (314134)

This change corrects an issue that occurs when you attach performance goals to performance journal entries in employee self-service.

## In preview

### Allow reason codes to be specified on leave types

Organizations might require additional information about time-off requests. You can now specify reason codes for leave types and let employees select a reason code on their time-off requests.

### Require reason codes for specific leave types on time-off requests

Organizations might require reason codes for specific leave types when employees submit time-off requests. This requirement might exist because of company policy or regulatory requirements. You can now specify which leave types require a reason code, and you can require that employees provide a reason code for the leave type on their time-off requests.

### Provide a leave and absence transaction list for HR

The ability to track employee time off and understand how time off is calculated not only helps Human resources (HR) answer employee questions, but also helps guarantee accurate time-off awards for employees. HR now has a new view into the transactions (grants, accruals, adjustments, and requests), so that HR staff can view the reasons behind balances.

## Coming soon

### Email support for alerts

In platform update 26 for Finance and Operations, users can create alert rules that automatically send email notifications to contacts when notifications are triggered by an event.
