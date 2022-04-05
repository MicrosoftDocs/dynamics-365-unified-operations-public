---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (July 08, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for July 8, 2020.
author: andreabichsel
ms.date: 07/08/2020
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
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (July 8, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This topic describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3382. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Database logging

Database logging allows you to determine which tables and fields to monitor. It also lets you determine the events that should trigger change tracking. You use database logging capabilities to see these changes over time. For more information, see [Configure and manage database logging](hr-admin-database-logging.md).

## Configure the name of Employee self service

In **Human Resources parameters**, you can now change the name of the **Employee self service** workspace to **Self service**. For more information, see [Change Employee self service workspace name](hr-employee-self-service-workspace-name.md)

## Benefits management open enrollment access outside of period

This release fixes a bug where employees could access benefits open enrollment outside of the enrollment period or without a life event. As a result, if you need to demo open enrollment in Employee self service, you must adjust the open enrollment dates to today (or earlier) to make it accessible. You can change this setting under **Benefits management > Rules and options periods**.

## Email employee enrollment confirmation

You can now send emails to employees after they complete their benefits selection. You can either send a default message or use an organization email template. These settings are under **Human resource parameters > Benefits management**.

## Canceled leave still appears in upcoming time off on People workspace (441358)

Canceled leave no longer displays as upcoming time off on the leave cards in the **People** workspace.

## Unable to use the department entity property in the PositionV2 entity (456486)

You can now add a department without creating a duplicate relation.

## PayrollWorkerEnrolledBenefitDetailEntity should only use calculated field for retirement plans (459779)

When exporting the **PayrollWorkerEnrolledBenefitDetailEntity** entity, the export determines whether it should use a calculated field based on a rate table or use the **ContributionAmountCur** field on the backing table. The logic used by the data entity uses the rate table in situations where the application normally doesn't. This logic causes the entity exports to return a zero value for this column, because there's no calculation rate table and the product doesn't allow the customer to specify one.
 
## Confusing translations in Czech language in Personnel management and Employee self service (400276)

This release corrects the translations for **Company directory**, **Next registered course**, **Job**, and **Position**.
 
## The WorkCalendarEmployment table doesn't have the created and modified system fields enabled (460171)

Created and modified system fields are now enabled on the **WorkCalendarEmployment** table in Human Resources.
 
## Null reference exception for Hire and add details for future employee (455475)

This release corrects an error (null reference) in streamlined employee entry when you hire an employee using the option to **Hire and add details**.

## Changes made in the Dataverse Worker entity don't reflect in Human Resources (455652)

Changes made to the following fields in the **Worker** entity in Dataverse will now show up in Human Resources:

- **Works from home**
- **Seniority date**
- **Anniversary date**
- **Original hire date**

## Correct compensation level doesn't default based on the job assigned to the position (394136)

With this change, the correct compensation level defaults based on the **Date effective** records for the **Position details** and the **Start date** of the **Compensation plan assignment**.

## In preview

## Mandatory fields 

You can now make fields mandatory by using Human Resources personalization capabilities. This feature requires **Saved views**.

## Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see [Human Resources app in Teams](./hr-admin-teams-leave-app.md). 

## Data management framework (DMF) entities for Benefits management
 
Benefits management entities are releasing. DMF entities allow you to import and export data to easily configure benefits management. A Benefits management template will be available to move data. The template exports and imports the data sequentially to respect data dependencies.

## Buy and sell leave 

Some organizations provide a benefit that allows employees to buy or sell their leave. This process is often managed manually. This feature automates managing policies and requests for the HR department. It streamlines the leave management process and helps eliminate mistakes. For more information, see:

- [Manage buy and sell leave policies](hr-leave-and-absence-manage-buy-and-sell-leave-policies.md)
- [Buy and sell leave](hr-employee-self-service-buy-sell-leave.md)

## Leave accrual for a single company or single plan

Customers can process accruals for a single company or a single leave and absence plan. This ability provides clarity for the accrual process for customers with different leave years or leave accrual policies. For more information, see [Accrue leave per company or per leave plan](hr-leave-and-absence-accrue.md).

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

## Checklist entities included in Dataverse

Checklist entities for Onboarding, Offboarding, Transfers, and Business processes will be available soon in Dataverse.

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]