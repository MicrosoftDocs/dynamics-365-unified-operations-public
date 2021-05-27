---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (June 11, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for June 11, 2020.
author: andreabichsel
ms.date: 06/16/2020
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
ms.search.validFrom: 2020-06-11
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (June 11, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3316. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Streamlined employee form sometimes causes child form close (X) buttons to stop working (442369)

When the new **Worker** form was enabled, the close (**X**) button occasionally didn't work on child forms. This problem was intermittent. You could close the form after leaving and coming back to it. For example, you could select a menu item on the left, and navigate back to the **Worker** form, and then close it. This week's release fixes this problem. 

## The Worker personal contact person entity doesn't export personal contacts with a parent relationship type

With this release, the **Worker personal contact person** entity exports all relationship types.

## The HcmPositionWorkerAssignmentV2Entity should be part of the Ceridian payroll integration package by default (448506)

With this change, the **HcmPositionWorkerAssignmentV2Entity** is included in the Ceridian payroll integration package.

## In preview

## Database logging

The database logging feature allows you to determine which tables and fields to monitor. It also lets you determine the events that should trigger change tracking. You use database logging capabilities to see these changes over time. For more information, see [Configure and manage database logging](hr-admin-database-logging.md).

## Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see [Human Resources app in Teams](./hr-admin-teams-leave-app.md). 

## Data management framework (DMF) entities for Benefits management
 
Benefits management entities are releasing. DMF entities allow you to import and export data to easily configure benefits management. A Benefits management template will be available to move data. The template exports and imports the data sequentially to respect data dependencies.

## Buy and sell leave 

Some organizations provide a benefit that allows employees to buy or sell their leave. This process is often managed manually. This feature automates managing policies and requests for the HR department. It streamlines the leave management process and helps eliminate mistakes. For more information, see:

- [Manage buy and sell leave policies](hr-leave-and-absence-manage-buy-and-sell-leave-policies.md)
- [Buy and sell leave](hr-employee-self-service-buy-sell-leave.md)

## Leave accrual for a single company or single plan

Customers can process accruals for a single company or a single leave and absence plan. This ability provides clarity into the accrual process for customers with different leave years or leave accrual policies. For more information, see [Accrue leave per company or per leave plan](hr-leave-and-absence-accrue.md).

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

## New platform capabilities 

You'll be able to make fields mandatory by using personalization. This feature will require you to enable **Saved views**.

## Configure the name of Employee self-service

A new option will be available in Human Resources parameters to update the name of the Employee self service workspace to Self service. 

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]