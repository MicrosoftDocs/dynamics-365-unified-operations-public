---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (June 4, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 6/4/2019
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
# "What's new or changed in Dynamics 365 for Talent (June 4, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Coming soon in Attract

### Job approvals on home page

Approvals appear in an **Approvals** section on the dashboard. Approvers can review their approvals under **Assigned to you**, which displays the job ID, title, other approvers, and date assigned. Users who submit a job for approval can review their jobs under **Requested by you**, which displays the approvers who still need to approve the submitted job.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2330.

### New page to validate position hierarchy data

HR and administrators can validate the managerial hierarchy for any circular references that might have been inadvertently imported. You can access this new page from **Organizational administration > Links > Positions > Position hierarchy validation**.

### Specify reason codes on leave types

Organizations might require additional information about time-off requests. You can now specify reason codes for leave types and let employees select a reason code on their time-off requests.

### Require reason codes for specific leave types on time-off requests

Organizations might require reason codes for specific leave types when employees submit time-off requests. This requirement might exist because of company policy or regulatory requirements. You can specify which leave types require a reason code, and you can require that employees provide a reason code for the leave type on their time-off requests.

### Provide a leave and absence transaction list for HR

The ability to track employee time off and understand how time off is calculated not only helps HR answer employee questions, but also helps ensure accurate time-off awards for employees. HR now has a new view into the transactions (grants, accruals, adjustments, and requests), so that HR staff can view the reasons behind time-off balances.

### Deleting a record from Talent is does not remove the record from CDS

With this change, records removed from Core HR Talent are now also removed from CDS.

### Variable compensation plan valid from/to dates are not being honored

With this release, You will not be able to enroll an employee in a variable compensation plan with a start date that is before the plans start date or an end date that exceeds the plans end date. 

### Performance review comments are removed when user clicks cancel

This release corrects an issue where canceling changes to a review comment, removes the comments. 

## In preview

### In Preview features will only be enabled in "Sandbox" Environments.
 
Read more about how changes are published in the documentation [HERE](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/provisioning-talent).

When provisioning a new instance of Talent, you can indicate whether the instance type is **Production** or **Sandbox**, which allows for early testing of new features. All existing Talent instances will be updated to the **Production** instance type. If you want one of your existing instances to be updated to the **Sandbox** instance type, please contact [Support](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/talent-support) to initiate the change request.

### Restrict the leave types in time off requests

Organizations can offer many different types of leave to employees. Some of these leave types might not be appropriate for employees to submit time off for and are managed by Human Resources (HR) instead. With this release, you can configure which leave types employees can submit time-off requests for. 

## Coming soon in Core HR

### Ability to view extended reports performance information in manager self service

The ability to view and update performance goals, reviews and journals is key. Direct line managers today are able to assign and update goals. They can issue new reviews and co-manage the process along with employees. Performance journals can be maintained and updated by both parties to help guarantee the performance reviews and process goes smoothly. With this change, managers will now able to view and maintain performance related information for their extended reports the same as they could for their direct reports. A new option will be available to allow for viewing of direct or extended reports performance information.
.
### Print performance reviews
With this change, employees, managers and HR will now be able to print an employee’s performance review.

