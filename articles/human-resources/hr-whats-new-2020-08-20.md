---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (August 20, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 8/20/2020
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
ms.search.validFrom: 2020-08-20
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (August 20, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3478. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Show upcoming and pending leave of absence information to cards in People workspace

Pending and upcoming leave request options are now available on the leave and absence cards of the people workspace.

## Private field is not yes by default for Employee role in Employee Self Service - (477106)

In this release, the private flag will now default to yes when employees add new address records through the personal information page in Employee self-service. 

## Candidates to hire FastTab in personnel management shows an incorrect count of candidates - (470110)

With this release, the personnel management page has been updated to accurately reflect the number of candidates to hire. 

## Can’t enter sickness for terminated employee when accrual is set to zero - (446195)

Leave transactions are now allowed for employees that have been terminated in the future and the accrual is set to "zero".Leave transactions can be entered up to the termination date of the employee. 

## Adding custom fields to the new worker form is disabling the fields in the action pane for Manage Leave - (473314)

Action pane options on the new worker form for Manage leave will no longer be disabled if custom fields have been added to the new worker form.

## Making the leave comment field mandatory allows a leave request to be submitted when no comment is entered - (473543)

Comment fields can now be mandatory and leave request will honor this setting. Mandatory fields is a preview feature.

### DMF entity available for accrual suspensions

A DMF entity is now available for accrual suspensions.

## In preview

### Mandatory fields

You can make fields mandatory by using Human Resources personalization capabilities. This feature requires **Saved views**. For more information about saved views, see:

- [Saved views - general availability](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/saved-views--general-availability) in the Dynamics 365 2020 release wave 2 plan
- [Build forms that fully utilize saved views](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/user-interface/understanding-saved-views)

### Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see:

- [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) in the Dynamics 365 2020 release wave 1 plan
- [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841)

## Coming soon

## Checklist entities included in Common Data Service

Checklist entities for Onboarding, Offboarding, Transfers, and Business processes will be available soon in Common Data Service.

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

## Benefit plan employee entity 

We have recently discovered two issues regarding the BenefitsPlanEmployee entity. When importing worker enrollments, the Coverage Code and the Plan Type Code are being set incorrectly.  This will cause the employees benefit plans to be displayed incorrectly in the Worker Benefits Plan form and in the Open enrollment form of Employee self-service. This can also impact the employees’ ability to select plans in ESS.  Currently there is not a work around.  The team is treating this as a high priority fix and will be rolling the fix out with our next release.

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
