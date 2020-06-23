---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (June 25, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 6/25/2020
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
ms.search.validFrom: 2020-06-25
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (June 16, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3347. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## When an enrollment is expired for a terminated employee, the leave type, balance and amount are all cleared in the leave enrollment form - (444867)

With this change, the values in the leave type, balance are maintained and not cleared upon making this selection.

## Incorrect forecasted balance when new feature (Leave accrual for a single company or a single plan) is enabled - (456553)

This scenario has been corrected to reflect the forecasted balance, when the leave accrual for a single company or single plan has been enabled.

## Entities with relations that result in duplicate navigation properties - (456486)

This weeks release corrects and issue with the navigation properties (relation) of multiple entities. Duplicate relations are detected. These scenarios have all been corrected.
 
## Cross-company comments on Performance review - (455536)

Cross company comments are now visible on performance reviews with this fix. This change corrects the view of reviewer comments that were entered in different companies for the same performance review.
 
## Compensation management data - Inconsistency in showing the data - (432562)

A consistent view of compensation data is now maintained in MSS. Depending on the way you navigate to a workers Compensation details, compensation data is now consistently shown to Managers.
 
## Fixed compensation plan's effective date is defaulted to today's date - (411994)

With this change, the compensation start date will be based on the start date of the position being assigned to the employee.

## Leave and absence form 'enable half day definition' is disabled when form opens - (452607)

With this change the enable half day definition will be enabled until new leave transactions exist. 

## Unable to publish to HcmDiscussionEntity via Excel - 'TotalRatingScore' field error - (453899)

With this change, you will now be able to update the TotalRatingScore felid using the HCMDiscussionEntity via the Excel workbook designer.

## In preview

## Database logging

The database logging feature allows you to determine which tables and fields to monitor. It also lets you determine the events that should trigger change tracking. You use database logging capabilities to see these changes over time. For more information, see [Configure and manage database logging](hr-admin-database-logging.md).

## Mandatory fields 

You are now able to make fields mandatory using the HR personalization capabilities. This feature requires **Saved views**.

## Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841). 

## Data management framework (DMF) entities for Benefits management
 
Benefits management entities are releasing. DMF entities allow you to import and export data to easily configure benefits management. A Benefits management template will be available to move data. The template exports and imports the data sequentially to respect data dependencies.

## Buy and sell leave 

Some organizations provide a benefit that allows employees to buy or sell their leave. This process is often managed manually. This feature automates managing policies and requests for the HR department. It streamlines the leave management process and helps eliminate mistakes. For more information, see:

- [Manage buy and sell leave policies](hr-leave-and-absence-manage-buy-and-sell-leave-policies.md)
- [Buy and sell leave](hr-employee-self-service-buy-sell-leave.md)

## Leave accrual for a single company or single plan

Customers can process accruals for a single company or a single leave and absence plan. This ability provides clarity into the accrual process for customers with different leave years or leave accrual policies. For more information, see [Accrue leave per company or per leave plan](hr-leave-and-absence-accrue.md#accrue-leave-per-company-or-per-leave-plan).

## Add attachments to time off requests

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

## Configure the name of Employee self-service
A new option will be available in Human Resources parameters to update the name of the Employee self service workspace to Self service.

## Checklist entities included in CDS

Checklist entities for Onboarding, Offboarding, Transfers, and Business processes will be available soon within the Common Data Service.
