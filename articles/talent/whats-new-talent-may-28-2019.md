---
# required metadata

title: What's new or changed in Dynamics 365 Talent (May 28, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 05/28/2019
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
ms.search.validFrom: 2019-05-28
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (May 28, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Coming soon in Attract

### Job approvals on home page

Approvals appear in an **Approvals** section on the dashboard. Approvers can review their approvals under **Assigned to you**, which displays the job ID, title, other approvers, and date assigned. Users who submit a job for approval can review their jobs under **Requested by you**, which displays the approvers who still need to approve the submitted job.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2319.

### Common Data Service entity support for custom fields

In this release, the following Common Data Service entities now support custom fields: Benefit calc rate detail, Work calendar holiday line, and Employment.

### Copy position now includes payroll details
When you use **Copy position** and select all of the options, the payroll details information is now included in the copy information. 

## In preview in Core HR

### Restrict the leave types in time off requests

Organizations can offer many different types of leave to employees. Some of these leave types might not be appropriate for employees to submit time off for and are managed by Human Resources (HR) instead. With this release, you can configure which leave types employees can submit time-off requests for. 

### New page to validate position hierarchy data

HR and administrators can validate the managerial hierarchy for any circular references that might have been inadvertently imported. You can access this new page from **Organizational administration > Links > Positions > Position hierarchy validation**.

### Specify reason codes on leave types

Organizations might require additional information about time-off requests. You can now specify reason codes for leave types and let employees select a reason code on their time-off requests.

### Require reason codes for specific leave types on time-off requests

Organizations might require reason codes for specific leave types when employees submit time-off requests. This requirement might exist because of company policy or regulatory requirements. You can specify which leave types require a reason code, and you can require that employees provide a reason code for the leave type on their time-off requests.

### Provide a leave and absence transaction list for HR

The ability to track employee time off and understand how time off is calculated not only helps HR answer employee questions, but also helps ensure accurate time-off awards for employees. HR now has a new view into the transactions (grants, accruals, adjustments, and requests), so that HR staff can view the reasons behind time-off balances.
