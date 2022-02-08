---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (August 20, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for August 20, 2020.
author: andreabichsel
ms.date: 08/20/2020
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
ms.search.validFrom: 2020-08-20
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (August 20, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This topic describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3478. The numbers in parentheses in some headings refer to Lifecycle Services (LCS) support numbers for reference.

## Show upcoming and pending leave of absence information to cards in People workspace

Pending and upcoming leave request options are now available on the Leave and absence cards in the **People** workspace.

## Private field isn't Yes by default for Employee role in Employee self service (477106)

The **Private** field now defaults to **Yes** when employees add new address records through the **Personal information** page in Employee self service. 

## Candidates to hire FastTab in Personnel management shows an incorrect count of candidates (470110)

The **Personnel management** page now accurately displays the number of candidates to hire. 

## Can’t enter sickness for terminated employee when accrual is set to zero (446195)

Leave transactions are now allowed for employees that have been terminated in the future and the accrual is set to zero. Leave transactions can be entered up to the termination date of the employee. 

## Adding custom fields to the new Worker form disables the fields in the action pane for Manage leave (473314)

Action pane options on the new **Worker** form in **Manage leave** will no longer be disabled if custom fields have been added to the new **Worker** form.

## Making the Leave comment field mandatory allows a leave request to be submitted when no comment is entered (473543)

Comment fields can now be mandatory, and leave requests honor this setting. Mandatory fields is a preview feature.

### DMF entity available for accrual suspensions

A DMF entity is now available for accrual suspensions.

## In preview

### Mandatory fields

You can make fields mandatory by using Human Resources personalization capabilities. This feature requires **Saved views**. For more information about saved views, see:

- [Saved views - general availability](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/saved-views--general-availability) in the Dynamics 365 2020 release wave 2 plan
- [Build forms that fully utilize saved views](../fin-ops-core/dev-itpro/user-interface/understanding-saved-views.md)

### Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see:

- [Employee leave and absence experience in Microsoft Teams](/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) in the Dynamics 365 2020 release wave 1 plan
- [Human Resources app in Teams](./hr-admin-teams-leave-app.md)

## Coming soon

### Human Resources app in Teams preview features
 
-  **Notifications**: Submitters and approvers of time-off requests will be notified in the Human Resources app in Teams. Approvers will be able to approve or deny time-off requests, and submitters will be notified if the request was approved or denied.
 
- **Manager time-off calendar**: Managers will be able to see approved and pending time off for their direct reports in a calendar view. This view provides an easy understanding of when their team members are away from work.

### Checklist entities included in Dataverse

Checklist entities for Onboarding, Offboarding, Transfers, and Business processes will be available soon in Dataverse.

## Known issues

The **Feature management** workspace may be displaying features that are disabled as preview features when they are generally available. Below is a list of generally available features that show an incorrect status. 

- Benefits management
- Case management
- Database logging (Auditing)
- Leave accrual for a single company or a single plan
- Leave and absence accrual suspension
- Balance adjustment reason code and comment
- Buy and sell leave
- Leave and absence calendar
- Leave carry-forward rules
- Leave accrual auditing
- Leave accrual deletion
- Leave accrual rounding
- Configure multiple leave types on a single leave plan
- Update time-off enhancements
- Use an employee's FTE for accruals
- Cross company compensation view
- Print performance reviews
- Leave accrual holiday corrections

### Benefit plan employee entity 

We have recently discovered two issues regarding the **BenefitsPlanEmployee** entity. When importing worker enrollments, the **Coverage code** and the **Plan type code** are being set incorrectly. This issue causes employee benefit plans to display incorrectly in the **Worker benefits plan** form and in the **Open enrollment** form in Employee self service. This issue can also impact the employee's ability to select plans in Employee self service. Currently there isn't a workaround. We're treating this as a high-priority fix and will roll out the fix with our next release.

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]