---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (May 28, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for May 28, 2020.
author: andreabichsel
ms.date: 05/28/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2020-05-28
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (May 28, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3287. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## LeaveRequest entity doesn't work when you enable multiple types per leave plan (447498)

With this change, the **LeaveEnrollmentV2Entity** is now available to correct the error that occurs when you enable multiple leave types.

## Batch contention reduction feature (preview) (446619)

When you enable this feature, you can expect a reduction in blocking on batch framework tables while selecting tasks and finishing jobs.

## UpdateConflict while saving worker prevents editing a record in People (427915)

This change corrects an error when adding a new worker, updating address information, and changing language preference. In this unique scenario, an error displayed indicating the record couldn't be updated. 

## Unable to add an attachment to an approved leave request to resubmit (425407)

This change now allows attachments to approved leave requests.

## User can enter compensation for an employee in a different legal entity form (409529)

This change disables compensation options to prevent inadvertent entry of compensation records for the wrong legal entity.

## Error when you transfer an employee and the Worker position assignment date is before the position duration (429402)

Error messages when transferring an employee in this scenario have been updated to better describe the changes needed to correct the problem.

## Attachments capabilities in Employee self service benefits enrollment
 
Now you can add attachments during the benefits enrollment process for each plan that the employee's enrolling in. You can then view the attachments within the **Worker enrolled benefit** form.

## In preview

## Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see [Human Resources app in Teams](./hr-admin-teams-leave-app.md). 

## Leave suspension

You can suspend leave and absence in Human Resources for an employee. Suspending leave stops the leave accruals for selected leave types. If the suspension occurs after an accrual has been processed, suspending leave creates a prorated adjustment to the employee's leave balance. For more information, see [Suspend leave](hr-leave-and-absence-suspend-leave.md).

## Update user experience to indicate that accrual is suspended (429550)

The user experience now indicates that the accrual has been suspended for a plan.

## Coming soon

## Database logging (in preview in June)

The database logging feature allows you to determine which table and fields should be monitored. It also lets you determine the events that should trigger change tracking. Inquiry capabilities are available to see these changes over time.

## Buy and sell leave (in preview June 1)

Some organizations provide a benefit that allows employees to buy or sell their leave. This process is often managed manually. This feature provides a more automated way to manage policies and requests for the HR department, and it helps eliminate mistakes while streamlining the leave management process. For more information, see:

- [Manage buy and sell leave policies](hr-leave-and-absence-manage-buy-and-sell-leave-policies.md)
- [Buy and sell leave](hr-employee-self-service-buy-sell-leave.md)

## Data management framework (DMF) entities for Benefits management
 
Benefits management entities are releasing. DMF entities allow importing and exporting data to easily configure benefits management. A Benefits management template will also be available to move data. The template exports and imports the data in a sequential manner to respect data dependencies.

## Add reason code to accrual suspensions (June 1)

Reason codes have been added to the accrual suspension.

## Carry forward rules (June 1)

You can specify a carry forward leave type for carry forward balances where carry forward adjustments are transferred. For example, if an employee carries forward 10 days, you can pick a different leave type for those 10 days. For more information, see [Configure leave and absence types](hr-leave-and-absence-types.md).

## Suspend leave accrual for specified leave types (June 1)

In this release, HR can create a rule to suspend leave accruals for employees with leave requests entered for unpaid leave. Unpaid leave can be a type, but doesn't have to be. You can suspend any leave based on another leave type.

## DMF entity available for accrual suspensions (June 1)

A DMF entity is now available for accrual suspensions.

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]