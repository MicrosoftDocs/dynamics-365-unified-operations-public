---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (July 08, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 7/08/2020
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
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (July 8, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3382. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Database logging

Database logging allows you to determine which tables and fields to monitor. It also lets you determine the events that should trigger change tracking. You use database logging capabilities to see these changes over time. For more information, see [Configure and manage database logging](hr-admin-database-logging.md).

## Configure the name of Employee self-service

A new option is now available in **Human Resources parameters** to update the name of the Employee self service workspace to Self service.

## Benefits management open enrollment access outside of period

A bug existed where employees could access benefits open enrollment outside of the enrollment period or without a life event.  This bug is fixed, however, if you would like to demo open enrollment in ESS you will need to adjust the open enrollment dates to today (or before) to make it accessible.  You can do this under Benefits management Rules and options periods.

## Email employee enrollment confirmation

Emails can now be sent to employees after they have completed their benefits selection.  You have the option to send a default message or use an organization email template.   These settings can be found under Human resource parameters > Benefits Management.

## Cancelled leave still appears in upcoming time off on people workspace  - (441358)

Cancelled leave will no longer display as upcoming time off on the leave cards in the people workspace.

## Unable to use the department entity property in the PositionV2 entity - (456486)

To correct this issue, a changes has been made to allow adding of department without creating a duplicate relation.

## PayrollWorkerEnrolledBenefitDetailEntity should only use calculated field for retirement plans - (459779)

When exporting the PayrollWorkerEnrolledBenefitDetailEntity entity it determines if it should utilize a calculated field based on a rate table or utilize the ContributionAmountCur field on the backing table. The logic used by the data entity utilizes the rate table in situations where the application normally would not, which is causing the entity exports to return a zero value for this column since there is no calculation rate table and the product does not allow the customer to specify one.
 
## Confusing translations in Czech language in Personnel Management and Employee Self-Service - (400276)

Corrections have been made for translations for Company directory, Next registered course, Job and Position.
 
## WorkCalendarEmployment table does not have the Create and Modified System Fields enabled - (460171)

Created and Modified system fields have been enabled on the WorkCalendarEmployment table in Human Resources.
 
## Null reference exception when doing "Hire and add details" for future employee - (455475)

A change has been made to correct an error (Null Reference) when using streamlined employee entry feature, and you hire an employee using the option to "hire and add details.

## Changes made in CDS worker entity do not reflect in D365 HR - Works from home, Seniority date, Anniversary date and Original hire date - (455652)

Changes made to: Works from home, Seniority date, Anniversary date and Original hire date will now be reflected in HR when changes have been made in CDS.

## Correct compensation level not defaulting based on the Job assigned to the position. - (394136)

With this change, the correct compensation level will default based on the date effective records for the position details and the start date of the compensation plan assignment.

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

## Checklist entities included in Common Data Service

Checklist entities for Onboarding, Offboarding, Transfers, and Business processes will be available soon within Common Data Service.
