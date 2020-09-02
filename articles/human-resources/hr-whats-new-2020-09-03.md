---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (September 03, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 9/03/2020
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
ms.search.validFrom: 2020-09-03
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (August 25, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3504. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Checklist entities included in Common Data Service

Checklist entities for Onboarding, Offboarding, Transfers, and Business processes will be available soon in Common Data Service.

## Uptake new Default Financial Dimensions grid and dialog pattern throughout D365HR - (469495)

The new pattern for financial dimensions is now available in the following areas:
- Position Actions  (Form: HcmPositionActionDetail)
- Payroll Earning Codes  (Form: PayrollEarningCode)

## Entries not appearing in Company Leave Calendar if the 'Leave and absence calendar enhancements' feature is not enabled - (484406)

This change corrects an issue where leave entries are not being displayed in the company leave calendar. This only occurs when the feature management option "leave and absence calendar enhancements" is not enabled.

## BenefitPlanEmployeeEntity issues corrected - (467597)

The following issue has been corrected with the **BenefitsPlanEmployee** entity. When importing worker enrollments, the **Coverage code** and the **Plan type code** are now being set correctly. This issue caused employee benefit plans to display incorrectly in the **Worker benefits plan** form and in the **Open enrollment** form in Employee self service.

## Electronic file 1094-C output missing letter in XML - (435190)

This change corrects an issue with the 1094-C output file missing a character needed when submitting to the IRS.

## Employee Variable compensation table mapped to fixed compensation form - (476117)

This change aligns the fixed compensation fields with the fixed compensation form. Variable compensation fields are now only available with the variable compensation form.

## System allows leave requests prior to enrollment if that leave type has a negative minimum balance  - (469917)

This change prohibits entering leave requests prior to being enrolled in the plan, even if the enrollment has a negative minimum balance.Requests can only be entered/submitted when the type/plan is active.

## Document templates are not downloading - (457279)

With this change, all document templates can now be downloaded. 

## Compensation plan report. Data is showing as column headers instead of rows for the field Pay rate - (476077)

Analytics report has been corrected to display the correct information for Pay Rate.

## In preview

### Human Resources application in Teams

Employees can view and request time away from work within Microsoft Teams. They can interact with a bot to create leave requests. For more information, see:

- [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) in the Dynamics 365 2020 release wave 1 plan
- [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841)

### Human Resources app in Teams preview features
 
-  **Notifications**: Submitters and approvers of time-off requests will be notified in the Human Resources app in Teams. Approvers will be able to approve or deny time-off requests, and submitters will be notified if the request was approved or denied.
 
- **Manager time-off calendar**: Managers will be able to see approved and pending time off for their direct reports in a calendar view. This view provides an easy understanding of when their team members are away from work.

### Configuration option to position work items assigned to me list - (477004)

A new option is now available to position the work items assigned to me list in the right hand column of the dashboard. With this change, all work items and to do lists display in the same area. Enable this functionality by turning on the "Preview - Workflow experience enhancements" feature in feature management. This feature when enabled will also "promote" the workflow options that appear in the personnel actions forms. Workflow options have been collocated above the action fast tab for quick access.

## Coming Soon

## Benefits Management reason codes

Benefits Management reason codes will soon be combined with the existing reason codes within Dynamics 365 Human Resources.  If you have created reason codes within Benefits management over 15 characters, you will need to go to the Benefits Management Reason Codes form and update the name of the reason code to be 15 characters or less.  Once the name is updated, the reason code will appear under the existing reason code form in Personnel Management. This change will be available in the future and will not affect existing functionally.

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
