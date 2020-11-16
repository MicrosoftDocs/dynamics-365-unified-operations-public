---
# required metadata

title: What's new or changed in Dynamics 365 Talent (June 4, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365  Talent.
author: Darinkramer
manager: AnnBe
ms.date: 06/04/2019
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
ms.search.validFrom: 2019-06-04
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (June 4, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Coming soon in Attract

### Job approvals on the home page

Approvals appear in an **Approvals** section on the dashboard. Approvers can review their approvals under **Assigned to you**. This section shows the job ID, title, other approvers, and the date when the job was assigned. Users who submit a job for approval can review their jobs under **Requested by you**. This section shows the approvers who must still approve the submitted job.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

The changes that are described in this section apply to build number 8.1.2330.

### New page to validate position hierarchy data

Human resources (HR) staff and admins can validate the managerial hierarchy for any circular references that were inadvertently imported. You can access this new page at **Organizational administration \> Links \> Positions \> Position hierarchy validation**.

### Specify reason codes on leave types

Organizations might require additional information about time-off requests. You can now specify reason codes for leave types and let employees select a reason code on their time-off requests.

### Require reason codes for specific leave types on time-off requests

Organizations might require reason codes for specific leave types when employees submit time-off requests. This requirement might exist because of company policy or regulatory requirements. You can specify which leave types require a reason code, and you can require that employees provide a reason code for the leave type on their time-off requests.

### Provide a leave and absence transaction list for HR

The ability to track employee time off and understand how time off is calculated not only helps HR answer employee questions but also helps guarantee accurate time-off awards for employees. HR now has a new view into the transactions (grants, accruals, adjustments, and requests), so that HR staff can view the reasons behind time-off balances.

### Deleting a record from Talent doesn't remove the record from Common Data Service

Records that are removed from Talent: Core HR are now also removed from Common Data Service.

### Variable compensation plan valid from/to dates aren't being honored

In this release, you can't enroll an employee in a variable compensation plan if the start date is before the plan's start date or the end date is after the plan's end date. 

### Performance review comments are removed when users select Cancel

This release corrects an issue where review comments are removed if a user starts to change a comment but then selects **Cancel**. 

## In preview

### Preview features are enabled only in sandbox instances

When you provision a new instance of Talent, you can specify whether the instance type is **Production** or **Sandbox**. Instances of the **Sandbox** type allow for early testing of new features. All existing Talent instances will be updated to the **Production** instance type. If you want one of your existing instances to be updated to the **Sandbox** instance type, contact [Support](https://docs.microsoft.com/dynamics365/unified-operations/talent/talent-support) to initiate the change request.

For more information about how changes are published, see [Provision Talent](https://docs.microsoft.com/dynamics365/unified-operations/talent/provisioning-talent).

### Restrict leave types in time-off requests

Organizations can offer many different types of leave to employees. However, it might not be appropriate for employees to submit time-off requests for some leave types. Those leave types might be managed by HR instead. In this release, you can configure which leave types employees can submit time-off requests for. 

## Coming soon in Core HR

### View extended information for performance in manager self-service

A new option will let managers view the performance of both their direct reports and their extended reports. Currently, line managers can assign and update performance goals and issue new reviews, which their employees co-manage. In addition, direct managers and their employees can maintain and update performance journals to help guarantee that the performance review process goes smoothly. When this change is implemented, managers will be able to view and maintain performance-related information for their extended reports in addition to their direct reports. 

### Print performance reviews

Employees, managers, and HR will be able to print an employee's performance review.
