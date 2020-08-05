---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (August 06, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 8/06/2020
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
ms.search.validFrom: 2020-08-06
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (August 06, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3444. The numbers in parentheses in some headings refer to LCS support numbers for reference.


## Claire creates a workflow for buying and selling leave requests - (446557)

In some organizations, your are allowed to buy or sell their leave. This benefit is provided to enable employees to get the most out of their leave benefit. By providing a more automated way to manage the policies and requests for the human resource department, HR will help eliminate mistakes and streamline the leave management process.

## Worker postal addresses V2 entity has access across legal entities with restricted access to users to legal entity - (459126)

With this change, the Worker postal address V2 will restrict based on the legal entity access given to the user.

## Workflow email hyperlink failing to open to relevant reviews - (437398)

When the placeholder to open a performance review is used in the review workflow. The hyperlink generated from the placeholder, in the email, will now open the selected record.

## New leave and absence: Buy/Sell Entities - (473180)

Data management framework entities are now available for the buying and selling of leave.

## Platform update 10.0.12(36) is now available.

More information is available [here](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-update-10-0-12).

## When viewing record information and using advanced filters user could gain access to other employees records - (472490)

With this change, Employee self-service users are only be able to access their records using employee self service. Viewing record information while changing the filtering option will no longer expose additional data.

## Personnel Management Analytics include exited worker records  - (382893)

With this release, personnel management analytics will now only include active workers. 
 
## Unable to process a Merit increase for an employee - (473125)

This change allows for the entry of merit increases when the effective date is changed for the new merit increase.

## Review workflow can be started more than once - (467541)

With this change, the performance review workflow can only be "started" one time. The status for the manager will no longer display the option to begin the review.

## Leave request work flow ends in error when cancelling an approved leave request. - (472063)

In this release, when an approved leave request is cancelled the state of the request will no longer remain approved and the workflow will continue.

## System suggests exited workers when creating a new review form the template - (460624)

With this change, exited workers will no longer be available when creating new reviews from a template. Reviews cannot be created for employees that are outside the dates of the their employment.

## Position hierarchy circular reference detection - (415879)

With this change, position hierarchy circular reference detection is now limited to a single point and time. Circular reference detection can be run for different dates to verify the reporting structure doesn't have any circular references.

## Data management framework (DMF) entities for Benefits management
 
Benefits management entities are releasing. DMF entities allow you to import and export data to easily configure benefits management. A Benefits management template will be available to move data. The template exports and imports the data sequentially to respect data dependencies.

## In preview

You can now make fields mandatory by using Human Resources personalization capabilities. This feature requires **Saved views**.

## Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841). 

## Buy and sell leave 

Some organizations provide a benefit that allows employees to buy or sell their leave. This process is often managed manually. This feature automates managing policies and requests for the HR department. It streamlines the leave management process and helps eliminate mistakes. For more information, see:

- [Manage buy and sell leave policies](hr-leave-and-absence-manage-buy-and-sell-leave-policies.md)
- [Buy and sell leave](hr-employee-self-service-buy-sell-leave.md)

## Leave accrual for a single company or single plan

Customers can process accruals for a single company or a single leave and absence plan. This ability provides clarity for the accrual process for customers with different leave years or leaves accrual policies. For more information, see [Accrue leave per company or per leave plan](hr-leave-and-absence-accrue.md#accrue-leave-per-company-or-per-leave-plan).

## Add attachments to time-off requests

The ability to add attachments to approved leave requests is critical in the current COVID-19 environment. Employees can now add these attachments. They also have more insight into how updates are made to leave requests. For more information, see [Add an attachment to an existing request](hr-employee-self-service-request-time-off.md#add-an-attachment-to-an-existing-request).

## Add reason code to accrual suspensions 

Reason codes have been added to the accrual suspension.

## Carry forward rules 

You can specify a carry forward leave type for carry forward balances where carry forward adjustments are transferred. For example, if an employee carries forward 10 days, you can pick a different leave type for those 10 days. For more information, see [Configure leave and absence types](hr-leave-and-absence-types.md).

## Suspend leave accrual for specified leave types

You can create a rule to suspend leave accruals for employees with leave requests entered for unpaid leave. Unpaid leave can be a type, but doesn't have to be. You can suspend any leave based on another leave type.

## DMF entity available for accrual suspensions

A DMF entity is now available for accrual suspensions.

## Coming soon

## Checklist entities included in Common Data Service

Checklist entities for Onboarding, Offboarding, Transfers, and Business processes will be available soon in Common Data Service.

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
