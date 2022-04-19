---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (August 06, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for August 06, 2020.
author: andreabichsel
ms.date: 08/06/2020
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
ms.search.validFrom: 2020-08-06
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (August 06, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This topic describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3444. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Platform update 10.0.12(36) is now available

For more information, see [Platform updates for version 10.0.12 of Finance and Operations apps (August 2020)](../fin-ops-core/dev-itpro/get-started/whats-new-platform-update-10-0-12.md).

## Data management framework (DMF) entities for Benefits management
 
Benefits management entities are releasing. DMF entities allow you to import and export data to easily configure benefits management. A Benefits management template will be available to move data. The template exports and imports the data sequentially to respect data dependencies. For more information, see:

- [DMF entity support](/dynamics365-release-plan/2020wave1/dynamics365-human-resources/dmf-entity-support) in the Dynamics 365 2020 release wave 1 plan
- [Data management overview](../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md)


## Claire creates a workflow for buying and selling leave requests (446557)

For more information, see:

- [Allow employees to buy and sell leave](/dynamics365-release-plan/2020wave1/dynamics365-human-resources/allow-employees-buy-sell-leave) in the Dynamics 365 2020 release wave 2 plan
- [Manage buy and sell leave policies](./hr-leave-and-absence-manage-buy-and-sell-leave-policies.md)
- [Buy and sell leave](./hr-employee-self-service-buy-sell-leave.md)


## Worker postal addresses V2 entity has access across legal entities with restricted access (459126)

With this change, the **Worker postal address V2** entity will restrict based on the legal entity access given to the user.

## Workflow email hyperlink fails to open relevant reviews (437398)

When you use the placeholder to open a performance review in the review workflow, the hyperlink generated in the email now opens the selected record.

## New entities for buying and selling leave (473180)

Data management framework entities are now available for buying and selling leave. For more information, see [Data management overview](../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

## When viewing record information and using advanced filters, a user could gain access to other employees' records (472490)

With this change, Employee self-service users can only access their own records while using employee self service. Viewing record information while changing the filtering option no longer exposes additional data.

## Personnel management analytics include exited worker records (382893)

With this release, personnel management analytics now only include active workers. 
 
## Unable to process a merit increase for an employee (473125)

This change allows you to enter merit increases when you change the effective date for the new merit increase.

## Review workflow can be started more than once (467541)

With this change, you can only start the performance review workflow once. The status for the manager no longer displays the option to begin the review.

## Leave request work flow ends in error when canceling an approved leave request (472063)

In this release, when you cancel an approved leave request, the state of the request no longer remains approved, and the workflow will continue.

## System suggests exited workers when creating a new review form the template (460624)

With this change, exited workers are longer available when creating new reviews from a template. You can't create reviews for employees who are outside the dates of their employment.

## Position hierarchy circular reference detection (415879)

With this change, position hierarchy circular reference detection is limited to a single point in time. You can run circular reference detection for different dates to verify the reporting structure doesn't have any circular references.

## Buy and sell leave 

Some organizations provide a benefit that allows employees to buy or sell their leave. This process is often managed manually. This feature automates managing policies and requests for the HR department. It streamlines the leave management process and helps eliminate mistakes. For more information, see:

- [Allow employees to buy and sell leave](/dynamics365-release-plan/2020wave1/dynamics365-human-resources/allow-employees-buy-sell-leave) in the Dynamics 365 2020 release wave 2 plan
- [Manage buy and sell leave policies](./hr-leave-and-absence-manage-buy-and-sell-leave-policies.md)
- [Buy and sell leave](./hr-employee-self-service-buy-sell-leave.md)

## Leave accrual for a single company or single plan

Customers can process accruals for a single company or a single leave and absence plan. This ability provides clarity for the accrual process for customers with different leave years or leaves accrual policies. For more information, see [Accrue leave per company or per leave plan](hr-leave-and-absence-accrue.md).

## Add attachments to time-off requests

The ability to add attachments to approved leave requests is critical in the current COVID-19 environment. Employees can now add these attachments. They also have more insight into how updates are made to leave requests. For more information, see [Add an attachment to an existing request](hr-employee-self-service-request-time-off.md#add-an-attachment-to-an-existing-request).

## Add reason code to accrual suspensions 

Reason codes have been added to the accrual suspension.

## Carry forward rules 

You can specify a carry forward leave type for carry forward balances where carry forward adjustments are transferred. For example, if an employee carries forward 10 days, you can pick a different leave type for those 10 days. For more information, see [Configure leave and absence types](hr-leave-and-absence-types.md).

## Suspend leave accrual for specified leave types

You can create a rule to suspend leave accruals for employees with leave requests entered for unpaid leave. Unpaid leave can be a type, but doesn't have to be. You can suspend any leave based on another leave type.

## In preview

### Mandatory fields

You can make fields mandatory by using Human Resources personalization capabilities. This feature requires **Saved views**. For more information about saved views, see:

- [Saved views - general availability](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/saved-views--general-availability) in the Dynamics 365 2020 release wave 2 plan
- [Build forms that fully utilize saved views](../fin-ops-core/dev-itpro/user-interface/understanding-saved-views.md)

### Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see:

- [Employee leave and absence experience in Microsoft Teams](/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) in the Dynamics 365 2020 release wave 1 plan
- [Human Resources app in Teams](./hr-admin-teams-leave-app.md)

### DMF entity available for accrual suspensions

A DMF entity is now available for accrual suspensions.

## Coming soon

## Checklist entities included in Dataverse

Checklist entities for Onboarding, Offboarding, Transfers, and Business processes will be available soon in Dataverse.

## Known issues

The **Feature management** workspace may be displaying features that are disabled as preview features when they are generally available. Below is a list of generally available features that show an incorrect status. 

1.	Benefits management
2.	Case management
3.	Database logging (Auditing)
4.	Leave accrual for a single company or a single plan
5.	Leave and absence accrual suspension
6.	Balance adjustment reason code and comment
7.	Buy and sell leave
8.	Leave and absence calendar
9.	Leave carry-forward rules
10.	Leave accrual auditing
11.	Leave accrual deletion
12.	Leave accrual rounding
13.	Configure multiple leave types on a single leave plan
14.	Update time-off enhancements
15.	Use an employee's FTE for accruals
16.	Cross company compensation view
17.	Print performance reviews
18.	Leave accrual holiday corrections

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]