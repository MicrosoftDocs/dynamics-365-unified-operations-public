---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (September 03, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for September 3, 2020.
author: andreabichsel
ms.date: 09/03/2020
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
ms.search.validFrom: 2020-09-03
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (September 3, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This topic describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3504. The numbers in parentheses in some headings refer to Lifecycle Services (LCS) support numbers for reference.

For more information about upcoming features in Human Resources, see [Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/). For more information about the update process for Human Resources, see [Update process](hr-admin-setup-update-process.md).

## In this release

### New default financial dimensions grid and dialog pattern throughout Human Resources (469495)

The new pattern for financial dimensions is now available in the following areas:

- Position actions  (Form: **HcmPositionActionDetail**)
- Payroll earning codes  (Form: **PayrollEarningCode**)

### Entries don't appear in company leave calendar if Leave and absence calendar enhancements aren't enabled (484406)

This release corrects an issue where leave entries aren't displayed in the company leave calendar. This issue only occurs when the Feature management option **Leave and absence calendar enhancements** isn't enabled.

### BenefitPlanEmployeeEntity issue (467597)

This release corrects an issue with the **BenefitsPlanEmployee** entity. When importing worker enrollments, the **Coverage code** and the **Plan type code** are now set correctly. This issue caused employee benefit plans to display incorrectly in the **Worker benefits plan** and **Open enrollment** forms in Employee self service.

### Electronic file 1094-C output missing letter in XML (435190)

This change corrects an issue with the 1094-C output file missing a character needed when submitting to the IRS.

### Employee variable compensation table mapped to fixed compensation form (476117)

This change aligns the fixed compensation fields with the fixed compensation form. Variable compensation fields are now only available with the variable compensation form.

### Leave requests allowed before enrollment if that leave type has a negative minimum balance (469917)

This change prohibits entering leave requests before being enrolled in the plan, even if the enrollment has a negative minimum balance. You can only enter or submit requests when the plan is active.

### Document templates don't download (457279)

With this change, you can now download all document templates. 

### Data displays as column headers instead of rows for the Pay rate field in the compensation plan report (476077)

The analytics report now displays the correct information for **Pay rate**.

## In preview

### Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see:

- [Employee leave and absence experience in Microsoft Teams](/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) in the Dynamics 365 2020 release wave 1 plan
- [Human Resources app in Teams](./hr-admin-teams-leave-app.md) in Human Resources documentation

### Human Resources app in Teams preview features
 
-  **Notifications**: Submitters and approvers of time-off requests will be notified in the Human Resources app in Teams. Approvers will be able to approve or deny time-off requests. Submitters will be notified if the request was approved or denied. For more information, see:
   - [Employee leave and absence experience in Microsoft Teams](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/employee-leave-absence-experience-teams) in the Dynamics 365 2020 release wave 2 plan
   - [Enable notifications for the Human Resources app in Teams](./hr-admin-teams-leave-app.md#enable-notifications-for-the-human-resources-app-in-teams) in Human Resources documentation
   - [Turn Teams notifications on or off for individual users](./hr-admin-teams-leave-app.md#turn-teams-notifications-on-or-off-for-individual-users) in Human Resources documentation
   - [Teams notifications](./hr-teams-leave-app.md#respond-to-teams-notifications) in Human Resources documentation
   - [View your team's leave calendar](./hr-teams-leave-app.md#view-your-teams-leave-calendar) in Human Resources documentation
 
- **Manager time-off calendar**: Managers will be able to see approved and pending time off for their direct reports in a calendar view. This view provides an easy understanding of when their team members are away from work. For more information, see:
   - [Employee leave and absence experience in Microsoft Teams](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/employee-leave-absence-experience-teams) in the Dynamics 365 2020 release wave 2 plan
   - [View your team's leave calendar](./hr-teams-leave-app.md#view-your-teams-leave-calendar) in Human Resources documentation

### Configuration option to position Work items assigned to me list (477004)

A new option is now available to position the **Work items assigned to me** list in the right-hand column of the dashboard. With this change, all work items and to do lists display in the same area. Enable this functionality by turning on **Preview - Workflow experience enhancements** in Feature management. For more information about turning on preview features, see [Manage features](hr-admin-manage-features.md).

This feature also promotes the workflow options that appear in the personnel actions forms. Workflow options also appear above the action fast tab for quick access. For more information, see: 

- [Organization and personnel management workflow experience enhancements](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) in the Dynamics 365 2020 release wave 2 plan

![Work items assigned to me.](./media/hr-workflow-work-items-assigned-to-me.png)

![Workflow items quick access.](./media/hr-workflow-quick-access.png)

## Coming Soon

### Checklist entities included in Dataverse

Checklist entities for Onboarding, Offboarding, Transfers, and Business processes will be available soon in Dataverse.

### Benefits management reason codes

Benefits management reason codes will soon be combined with existing reason codes in Human Resources. If you created reason codes in Benefits management that are over 15 characters, you must change the name of the reason code in the Benefits management **Reason codes** form to be 15 characters or less. After you update the name, the reason code will appear under the existing reason code form in Personnel management. This change will be available in the future and won't affect existing functionally.

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
