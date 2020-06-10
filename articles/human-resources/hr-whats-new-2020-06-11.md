---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (June 11, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 6/11/2020
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
ms.search.validFrom: 2020-06-11
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (June 11, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3316. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Streamlined employee form causes child form close (X) buttons occasionally stop working - (442369)

A change has been made to correct the following scenario. When the new worker form is enabled, child forms will occasionally be unable to close via the system form close 'X' button. This happens very intermittently and can be reset by leaving the form and coming back (i.e. clicking a menu item on the left and navigating back to the worker form).

## The export of personal contact for an employee using the “Worker personal contact person” entity do not export the personal contact with relationship type “parent”. - (345893)

In this release, the “Worker personal contact person” entity will export all relationship types.

## HcmPositionWorkerAssignmentV2Entity should be part of the Ceridian payroll integration package by default - (448506)

With this change, the HcmPositionWorkerAssignmentV2Entity will be part of the integration package for Ceridian payroll integration. 

## In preview

## Database logging

The database logging feature allows you to determine which table and fields should be monitored. It also lets you determine the events that should trigger change tracking. Inquiry capabilities are available to see these changes over time.

## Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841). 

## Data management framework (DMF) entities for Benefits management
 
Benefits management entities are releasing. DMF entities allow importing and exporting data to easily configure benefits management. A Benefits management template will also be available to move data. The template exports and imports the data in a sequential manner to respect data dependencies.

## Buy and sell leave 

Some organizations provide a benefit that allows employees to buy or sell their leave. This process is often managed manually. This feature provides a more automated way to manage policies and requests for the HR department, and it helps eliminate mistakes while streamlining the leave management process.

## Leave accrual for a single company or single plan
With this feature, customers will be able to process accruals for a single company or a single leave and absence plan. For customers with differing leave years or leave accrual policies, having the ability to run these processes separately provides clarify into the accrual process. 

## Update time off enhancements
Adding attachments to approved leave requests has become critical in the current COVID-19 environment. Employees can now add these attachments along with have more insight into how updates are made to leave requests. 

## Add reason code to accrual suspensions 

Reason codes have been added to the accrual suspension.

## Carry forward rules 

You can specify a carry forward leave type for carry forward balances where carry forward adjustments are transferred. For example, if an employee carries forward 10 days, you can pick a different leave type for those 10 days. For more information, see [Configure leave and absence types](hr-leave-and-absence-types.md).

## Suspend leave accrual for specified leave types

In this release, HR can create a rule to suspend leave accruals for employees with leave requests entered for unpaid leave. Unpaid leave can be a type, but doesn't have to be. You can suspend any leave based on another leave type.

## DMF entity available for accrual suspensions 

A DMF entity is now available for accrual suspensions.

## Coming soon

## New platform capabilities 

- Designate fields as mandatory by using personalization. This feature requires "Saved views" be enabled.
