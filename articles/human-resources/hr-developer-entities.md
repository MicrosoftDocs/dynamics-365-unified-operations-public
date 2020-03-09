---
# required metadata

title: Common Data Service entities
description: Microsoft Dynamics 365 Human Resources uses Common Data Service to enable extensibility and integration scenarios.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Common Data Service entities

Microsoft Dynamics 365 Human Resources uses Common Data Service to enable extensibility and integration scenarios.

For more information about Common Data Service, see [What is Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro).

The following Human Resources entities are available in Common Data Service.

## Benefit entities

| Name | Entity |
| --- | --- |
| Benefit Calculation Frequency | cdm_benefitcalculationfrequency |
| Benefit Calculation Frequency Pay Period | cdm_benefitcalculationfrequencypayperiod |
| Benefit Calculation Rate | cdm_benefitcalculationrate |
| Benefit Calculation Rate Detail | cdm_benefitcalculationratedetail |
| Benefit Option | cdm_benefitoption |
| Benefit Plan | cdm_benefitplan (Not enabled for custom field support) |
| Benefit Type | cdm_benefittype |

## Business process tasks entities

| Name | Entity |
| --- | --- |
| Business Process Calendar | cdm_businessprocesscalendar |
| Business Process Group Assignment | cdm_businessprocessgroupassignment |
| Business Process Library Task Group | cdm_businessprocesslibrarytaskgroup |
| Business Process Stage | cdm_businessprocessstage |
| Checklist Template Header | cdm_businessprocesstemplateheader |
| Checklist Template Task | cdm_businessprocesstemplatetask |

## Compensation entities

| Name | Entity |
| --- | --- |
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
| Fixed Compensation Event | cdm_fixedcompensationevent |
| Vesting Rule | cdm_vestingrule |
| Worker Fixed Compensation | cdm_workerfixedcompensation |

## Organization entities

| Name | Entity |
| --- | --- |
| Department | cdm_department |
| Employment | cdm_employment |
| Company | cdm_company |
| Job | cdm_job |
| Job Function | cdm_jobfunction |
| Job Position | cdm_jobposition |
| Position Type | cdm_positiontype |
| Position Worker Assignment | cdm_positionworkerassignmentmap |
| Job Type | cdm_jobtype |
| Language | cdm_language |

## Leave and absence entities

| Name | Entity |
| --- | --- |
| Leave Bank Transaction | cdm_leavebanktransaction |
| Leave Enrollment | cdm_leaveenrollment |
| Leave Plan | cdm_leaveplan |
| Leave Request | cdm_leaverequest |
| Leave Request Detail | cdm_leaverequestdetail |
| Leave Type | cdm_leavetype |
| Leave Type Reason Code | cdm_leavetypereasoncode |

## Payroll entities

| Name | Entity |
| --- | --- |
| Pay Cycle | cdm_paycycle |
| Pay Period | cdm_payperiod |
| Payroll Earning Code | cdm_payrollearningcode |
| Bank Account Disbursement | cdm_bankaccountdisbursement |
| Tax Region | cdm_taxregion |

## Worker entities

| Name | Entity |
| --- | --- |
| Worker | cdm_worker |
| Worker Address | cdm_workeraddress |
| Worker Personal Detail | cdm_workerpersonaldetail |
| Worker Person Identification Number | cdm_workerpersonidentificationnumber |
| Worker Person Identification Type | cdm_workerpersonidentificationtype |
| Work Calendar | cdm_workcalendar |
| Work Calendar Day | cdm_workcalendarday |
| Work Calendar Holiday |cdm_workcalendarholiday |
| Work Calendar Holiday Line | cdm_workcalendarholidayline |
| Work Calendar Time Interval | cdm_workcalendartimeinterval (Not enabled for custom field support) |
| Worker Bank Account | cdm_workerbankaccount |

## Worker setup entities

| Name | Entity |
| --- | --- |
| Veteran Status | cdm_veteranstatus |
| Ethnic Origin | cdm_ethnicorigin |
| Reason Code | cdm_reasoncode |
| Person Identification Issuing Agency | cdm_personidentificationissuingagency |

## Competency entities

| Name | Entity |
| --- | --- |
| Skill Type | cdm_skilltype |

## Entity relationship models

### Worker

![Worker](./media/HCMCommon-worker-entity-diagram.png)

### Job and Job Position

![Job and Job Position](./media/HCMCommon-job-and-job-position-entity-diagram.png)

### Benefits

![Benefits](./media/HCMCommon-benefits-entity-diagram.png)

### Compensation

![Compensation](./media/HCMCommon-compensation-entity-diagram.png)

### Leave

![Leave](./media/HCMCommon-leave-entity-diagram.png)

### Work Calendar

![Work Calendar](./media/HCMCommon-work-calendar-entity-diagram.png)

## See also

[Choose a data integration technology](hr-admin-integration-choose-technology.md)</br>
[Configure Common Data Service integration](hr-admin-integration-common-data-service.md)