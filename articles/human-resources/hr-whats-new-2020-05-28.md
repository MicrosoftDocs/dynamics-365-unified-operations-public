---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (May 28, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 5/28/2020
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
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2020-05-28
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (May 19, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3287. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## LeaveRequest entity does not work if multiple types per leave plan feature enabled - (447498)

With this change, the LeaveEnrollmentV2Entity is now available to correct the error when multiple leave types per plan is enabled.

## Batch contention reduction feature (preview) - (446619)

Environments experiencing heavy blocking on batch framework tables while selecting tasks and finishing jobs can expect a reduction in blocking when this feature is enabled.

## UpdateConflict saving worker - Cannot edit a record in People - (427915)

This change corrects an error when adding a new worker, updating address information and changing language preference. In this unique scenario a error was displayed indicating the record could not be updated. 

## Unable to add an attachment to an approved leave request to resubmit - (425407)

This change will now allow attachments to approved leave requests.

## User can enter compensation for an employee in different Legal Entity - Streamlined Employee form - (409529)

This change disables compensation options to prevent inadvertent entry of compensation records for the wrong legal entity.

## Error when Transferring an employee and the Worker position assignment date is prior to the duration of the position - (429402)

Error messages when transferring an employee in this scenario has been updated to better describe the changes needed to correct this scenario.

## Add reason code to accrual suspensions (June 1)

Reason codes have been added to the accrual suspension.

## Carry forward rules (June 1)

You can specify a carry forward leave type for carry forward balances where carry forward adjustments are transferred. For example, if an employee carries forward 10 days, you can pick a different leave type for those 10 days. For more information, see [Configure leave and absence types](hr-leave-and-absence-types.md).

## Suspend leave accrual for specified leave types (June 1)

In this release, HR can create a rule to suspend leave accruals for employees with leave requests entered for unpaid leave. Unpaid leave can be a type, but doesn't have to be. You can suspend any leave based on another leave type.

## DMF entity available for accrual suspensions (June 1)

A DMF entity is now available for accrual suspensions.

## Attachments capabilities in Employee self-service benefits enrollment
 
With this new capability, attachments can be added during the benefits enrollment process for each plan that the employee is enrolling in.  The attachments added by employees can then be viewed within the Worker enrolled benefit form for review by the benefits assistant.

## In preview

## Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. Employees can interact with a bot to help create leave requests as well as work with the personal app to create and edit leave information. For more in formation, see [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841). 

## Leave suspension

You can suspend leave and absence in Human Resources for an employee. Suspending leave stops the leave accruals for selected leave types. If the suspension occurs after an accrual has been processed, suspending leave creates a prorated adjustment to the employee's leave balance. For more information, see [Suspend leave](hr-leave-and-absence-suspend-leave.md).

## Update user experience to indicate that accrual is suspended (429550)

The user experience now indicates that the accrual has been suspended for a plan.

## Coming soon

## Database Logging (Preview June)

The database logging feature allows you to determine which table, and fields should be monitored and the events that should trigger the change tracking. Inquiry capabilities are available to see these changes over time. 

## Buy and Sell Leave (Preview June 1)

In some organizations, a provided benefit is to allow employees to buy or sell their leave. This enables employees to get the most out of their leave benefit. Managing this process is often done manually. This feature provides a more automated way to manage the policies and requests for the human resource department, and helps eliminate mistakes while streamlining the leave management process.

## Benefits Entities - Data management framework entities for Benefits Management
 
Benefits management entities are releasing.  DMF entities allow for importing and exporting data to easily configure benefits management. A benefit management template will also be available to move data.  The template exports and imports the data in a sequential manner to respect data dependencies.
