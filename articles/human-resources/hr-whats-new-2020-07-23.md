---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (July 23, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 7/23/2020
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
ms.search.validFrom: 2020-07-23
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (July 23, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3416. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Deleting Financial Dimensions on a Position not working as expected.  - (445476)

With this change, removing dimensions from a position will now remove those same positions from the CDS.

## Positions not in hierarchy show inactive positions  - (397257)

Positions that are inactive (have an expired duration), will no longer be displayed in the position hierarchy as "positions not in hierarchy". 

## Validation occurring between LeaveEnrollmentEntity and HcmWorkerEntity on DMF import is causing slow data loads - (442324)

Changes have been made to increase the performance of the LeaveEnrollmentEntity.

## Unable to Personalize in Organization administration  - (447490)

With this change you are now able to personalize the links in Organizational administration.

## In preview

## Mandatory fields 

You can now make fields mandatory by using Human Resources personalization capabilities. This feature requires **Saved views**.

## Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841). 

## Data management framework (DMF) entities for Benefits management
 
Benefits management entities are releasing. DMF entities allow you to import and export data to easily configure benefits management. A Benefits management template will be available to move data. The template exports and imports the data sequentially to respect data dependencies.

## Buy and sell leave 

Some organizations provide a benefit that allows employees to buy or sell their leave. This process is often managed manually. This feature automates managing policies and requests for the HR department. It streamlines the leave management process and helps eliminate mistakes. For more information, see:

- [Manage buy and sell leave policies](hr-leave-and-absence-manage-buy-and-sell-leave-policies.md)
- [Buy and sell leave](hr-employee-self-service-buy-sell-leave.md)

## Leave accrual for a single company or single plan

Customers can process accruals for a single company or a single leave and absence plan. This ability provides clarity for the accrual process for customers with different leave years or leave accrual policies. For more information, see [Accrue leave per company or per leave plan](hr-leave-and-absence-accrue.md#accrue-leave-per-company-or-per-leave-plan).

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

## Platform changes

Platform update 10.0.12 (36)

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
