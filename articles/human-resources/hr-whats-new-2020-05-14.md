---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (May 14, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for May 14, 2020.
author: andreabichsel
ms.date: 05/14/2020
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
ms.search.validFrom: 2020-05-14
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (May 14, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This topic describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3244. The numbers in parentheses in some headings refer to Lifecycle Services (LCS) support numbers for reference.

## Platform changes

Platform changes are included in this week's release. For more information, see [Platform updates for version 10.0.10 of Finance and Operations apps (May 2020)](../fin-ops-core/dev-itpro/get-started/whats-new-platform-update-34.md). This release includes bug fixes and changes to saved views.
 
## Ensure Dataverse picklists are consistent with Leave enums (436343)

Dataverse picklists are now consistent with Leave enums.

## Allow users to configure leave request workflow based on the request amount (300044)

Users can configure leave requests workflows based on request amounts.
 
## New worker form exposes data through the View menu when advanced security is enabled (403185)

This release corrects how viewing workers across legal entities functions when advanced access is enabled and workers in other companies are accessible.

## Allow running leave accruals for a single plan or a single company (318844)

With this change, you can run accruals for a company or a plan.
 
## Show the position's full-time equivalent (FTE) in the Enrolled workers form (414658)

The FTE value from a worker's position determines a worker's accrual rate when the FTE option is enabled on the leave type. This field is now included in **Enrolled workers** form and the **Mass enrollment** dialog.

## Add leave balance expiration batch job (431266)

A new batch job is now available that runs daily. It decreases the remaining leave balance when expiration dates become current.

## Exporting personal contacts for an employee using the Worker personal contact person entity doesn't export personal contacts with the Parent relationship type (345893)

The **Worker personal contact person** data entity (**HcmPersonalContactPersonEntity** in DMF and **PersonalContactPerson** in OData) couldn't export personal contacts that have a relationship type of **Parent**. This issue is fixed for personal contacts that are created after this change. Existing personal contacts of type **Parent** will be fixed in a later release.

## Reason codes display across different scenarios when they're marked as Leave and absence and the streamlined employee form is enabled (434163)

This change restricts the reason codes to only Leave and absence codes when you enable streamlined employee entry.

## The preview feature Assign a leave plan to employees in the future displays error (433555)

This change corrects an error when a leave plan has two leave types assigned and you attempt to assign an employee.

## Getting started banner appears for all users (441731)

With this change, the Getting started banner is hidden for users that aren't System administrators or Data management administrators. 

## The Dataverse Worker Address entity works differently in terms of date time effective dates in Human Resources (425071)

This change keeps address information aligned in certain scenarios, based on the dates of the address.

## Unable to add an attachment to an approved leave request (425407)

With this week's release, you can add attachments to approved leave requests without changing the leave request.

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

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]