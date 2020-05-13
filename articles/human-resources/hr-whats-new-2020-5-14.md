---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (May 14, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 5/14/2020
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
ms.search.validFrom: 2020-05-14
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (May 14, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3244. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Platform changes
Platform changes are included in this week's release. For more information documentation is provided [HERE](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-update-34). This release includes changes to saved views, and a number of bug fixes.
 
## Ensure CDS picklists are consistent with Leave enums - (436343)## FV: Allow users to configure leave request workflow based on the request amount - (300044)
This was requested by 
 
## New worker form exposes data through the View menu when advanced security is enabled. - (403185)

A change has been made to correct how viewing workers across legal entities functions when advanced access is also enabled. This change will correct the scenario where workers in other companies are accessible.

## Allow running leave accruals for a single plan or a single company - (318844)

With this change customers are now able to "run" accruals for a company or a plan.
 
## Show the position's Full-time equivalent in the Enrolled workers form - (414658)

The Full-time equivalent value from a worker's position is used to determine a worker's accrual rate when the FTE option is enabled on the leave type.  This field is now included in the grids in the Enrolled workers form and mass enrollment dialog.

## Add leave balance expiration batch job - (431266)

A new batch job is now available that will run daily that will decrease remaining leave balance when expiration dates become current.

## Exporting personal contact for an employee using the “Worker personal contact person” entity does export the personal contact with relationship type “parent” - (345893)

With this change, ‘Worker personal contact person’ data entity (DMF: HcmPersonalContactPersonEntity; OData: PersonalContactPerson) was not able to export personal contacts that have a relationship type of ‘Parent’. This has been fixed for personal contacts that are created going forward.  However, existing personal contacts of type ‘Parent’ will be fixed in a subsequent release.

## Reason codes are showing across different scenarios when they marked up as Leave and Absence when the streamlined employee form is enabled - (434163)

Change have been made to restrict the reason codes to only Leave and Absence codes when the new feature Streamlined employee entry is activated.

## Assign a leave plan to employees in the future displays error - preview feature - (433555)

This change corrects an error when a Leave plan has two Leave types assigned and you attempt to Assign an employee.

## Getting Started "Banner"  appears for all users - (441731)

With this change, the getting started banner will be hidden for users that are not System Administrators or Data management administrators. 

## CDS Worker Address entity works differently in terms of date time effective dates in HR - (425071)

A change has been made to keep address information aligned, in certain scenarios, based on the dates of the address.

## Unable to add an attachment to an approved leave request - (425407)

In this week's release, attachments can be added to approved leave requests with out making a change to the leave request.

## In preview

## Leave suspension

You can suspend leave and absence in Human Resources for an employee. Suspending leave stops the leave accruals for selected leave types. If the suspension occurs after an accrual has been processed, suspending leave creates a prorated adjustment to the employee's leave balance. For more information, see [Suspend leave](hr-leave-and-absence-suspend-leave.md).

## Update user experience to indicate that accrual is suspended (429550)

The user experience now indicates that the accrual has been suspended for a plan.

## Suspend leave accrual for specified leave types (272447)

In this release, HR can create a rule to suspend leave accruals for employees with leave requests entered for unpaid leave. Unpaid leave can be a type, but doesn't have to be. You can suspend any leave based on another leave type.

## DMF entity available for accrual suspensions (429549)

A DMF entity is now available for accrual suspensions.

## Add reason code to accrual suspensions (429547)

Reason codes have been added to the accrual suspension.

## Begin transitioning from Human Resources parameters to leave and absence parameters

This release starts to combine Human Resources parameters with Leave and absence parameters.

## Carry forward rules

You can specify a carry forward leave type for carry forward balances where carry forward adjustments are transferred. For example, if an employee carries forward 10 days, you can pick a different leave type for those 10 days. For more information, see [Configure leave and absence types](hr-leave-and-absence-types.md).
