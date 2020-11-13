---
# required metadata

title: What's new or changed in Dynamics 365 Talent (December 3, 2019)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 12/03/2019
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
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-12-03
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (December 3, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This article describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2646. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### Feature management workspace

The **Feature management** workspace provides a list of features delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them. For more information about Feature management, see [Feature management overview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

All new features remain in preview for at least 30 days, and typically 30-60 days. Major features are generally available in October and April of each year following the preview period. As soon as you see new capabilities in the **Feature management** workspace, you can turn them on. Some features may be on by default.
 
At times, an integral feature will be on by default and can't be turned off (for example, the **Feature management** workspace).
 
Once a feature is generally available, it may be turned on or off in production environments. The **Feature management** workspace indicates when a preview feature will become mandatory. This date is usually on October 1 or April 1 to align with the semiannual release plans. You can't turn off mandatory features. Until it becomes mandatory, you can turn a feature on and off in all environments.

### Add automatic scheduling of Batch Job History cleanup (332528)

With this change, **Batch Job History** runs each night and removes batch job history items older than 30 days.

### Talent doesn't respond in worker actions when identification number length doesn't match the identification type (390971)

This release corrects the issue surfaced when the identification number length doesn't match the definition within the identification type. 

### Fixed compensation doesn't update level with changes to position details  (348085)

In this week's release, **Compensation start date** determines the job associated with the position at that point in time when creating a new fixed compensation record for an employee.

### Workers, Employees, and Contractors lists show Worker Type as Both when they should only be Worker or Contractor (384473)

This change accurately reflects the type of worker entered (contractor or employee).

### Email notifications for new hire actions don't contain name information due to security policies (383402)

This change corrects the information displayed in the first or surname fields within the placeholders for workflow when advanced security is enabled.

### System allows two full-day leave requests for the same day (379284)

With this change, you can't issue two leave requests for the same day. 

### Address changes list should be sorted by Effective date (352798)

With this change, the address change list is now sorted by **Effective date**.

### Leave requests should allow deletes from Common Data Service to Talent (376999)

With this change, draft and canceled leave requests can be deleted from Common Data Service and then removed from Talent.

### Delete earning codes is allowed when the same earning code is assigned to an employee (371792)

In this release, you must first remove the earning code from the employee before deleting the earning code from the system.

### Leave and Absence workflow with two approval stages fails to complete  (391116)

With this change, the leave and absence workflow continue through all steps when more than one approval stage is configured for the request.

### Issue date doesn't sync to Common Data Service when updated or entered in Talent (397361)

This change corrects a problem where the issue date for **Person identification** records didn't sync to Common Data Service from Talent.

### Hierarchy circular reference error issued when assigning a manager to a position (386659)

This change corrects a unique scenario where a circular reference error appears when assigning a new manager to a position.

### Common Data Service Entities that now support custom fields

The following Common Data Service entities now support custom fields:

| Name | Entity |
| --- | --- |
| Bank Account Disbursement | cdm_bankaccountdisbursement |
| Benefit Calculation Frequency | cdm_benefitcalculationfrequency |
| Benefit Calculation Frequency Pay Period | cdm_benefitcalculationfrequencypayperiod |
| Benefit Calculation Rate | cdm_benefitcalculationrate |
| Benefit Calculation Rate Detail | cdm_benefitcalculationratedetail |
| Benefit Option | cdm_benefitoption |
| Benefit Plan | cdm_benefitplan (Not enabled for custom field support) |
| Benefit Type | cdm_benefittype |
| Business Process Calendar | cdm_businessprocesscalendar |
| Business Process Group Assignment | cdm_businessprocessgroupassignment |
| Business Process Library Task Group | cdm_businessprocesslibrarytaskgroup |
| Business Process Stage | cdm_businessprocessstage |
| Checklist Template Header | cdm_businessprocesstemplateheader |
| Checklist Template Task | cdm_businessprocesstemplatetask |
| Company | cdm_company |
| Compensation Fixed Plan | cdm_compensationfixedplan |
| Compensation Grid | cdm_compensationgrid |
| Compensation Level | cdm_compensationlevel |
| Compensation Pay Frequency | cdm_compensationpayfrequency |
| Compensation Reference Point Setup | cdm_compensationreferencepointsetup |
| Compensation Reference Point Setup Line | cdm_compensationreferencepointsetupline |
| Compensation Region | cdm_compensationregion |
| Compensation Structure | cdm_compensationstructure |
| Compensation Variable Plan | cdm_compensationvariableplan |
| Compensation Variable Plan Level | cdm_compensationvariableplanlevel |
| Compensation Variable Plan Type | cdm_compensationvariableplantype |
| Department | cdm_department |
| Employment | cdm_employment |
| Ethnic Origin | cdm_ethnicorigin |
| Fixed Compensation Event | cdm_fixedcompensationevent |
| Job | cdm_job |
| Job Function | cdm_jobfunction |
| Job Position | cdm_jobposition |
| Job Type | cdm_jobtype |
| Language | cdm_language |
| Leave Bank Transaction | cdm_leavebanktransaction |
| Leave Enrollment | cdm_leaveenrollment |
| Leave Plan | cdm_leaveplan |
| Leave Request | cdm_leaverequest |
| Leave Request Detail | cdm_leaverequestdetail |
| Leave Type | cdm_leavetype |
| Leave Type Reason Code | cdm_leavetypereasoncode |
| Pay Cycle | cdm_paycycle |
| Pay Period | cdm_payperiod |
| Payroll Earning Code | cdm_payrollearningcode |
| Person Identification Issuing Agency | cdm_personidentificationissuingagency |
| Position Type | cdm_positiontype |
| Position Worker Assignment | cdm_positionworkerassignmentmap |
| Reason Code | cdm_reasoncode |
| Skill Type | cdm_skilltype |
| Tax Region | cdm_taxregion |
| Vesting Rule | cdm_vestingrule |
| Veteran Status | cdm_veteranstatus |
| Work Calendar | cdm_workcalendar |
| Work Calendar Day | cdm_workcalendarday |
| Work Calendar Holiday |cdm_workcalendarholiday |
| Work Calendar Holiday Line | cdm_workcalendarholidayline |
| Work Calendar Time Interval | cdm_workcalendartimeinterval (Not enabled for custom field support) |
| Worker | cdm_worker |
| Worker Address | cdm_workeraddress |
| Worker Bank Account | cdm_workerbankaccount |
| Worker Fixed Compensation | cdm_workerfixedcompensation |
| Worker Personal Detail | cdm_workerpersonaldetail |
| Worker Person Identification Number | cdm_workerpersonidentificationnumber |
| Worker Person Identification Type | cdm_workerpersonidentificationtype |

## In preview

Preview features are only available in **Sandbox** environments.

### Print performance reviews

See [Print performance reviews](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-talent/print-performance-reviews) in the Dynamics 365: 2019 release wave 2 plan.
