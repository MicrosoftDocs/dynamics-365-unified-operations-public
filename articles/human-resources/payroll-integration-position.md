---
# required metadata

title: Position entity
description: This article provides details and an example query for the HCM Position entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 02/20/2026
ms.topic: article

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Position entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Position entity (PayIntV1HcmPositionEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the position.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Unionagreementlegalentity | mserp_unionagreementlegalentity | String | Read-only |
| Defaultearningcodeid | mserp_defaultearningcodeid | String | Read-only |
| Department | mserp_department | Real | Read-only |
| Worker Bigint | mserp_worker_bigint | Int64 | Read-only |
| Paycycle | mserp_paycycle | Real | Read-only |
| Positiontype Bigint | mserp_positiontype_bigint | Int64 | Read-only |
| Paidby | mserp_paidby | Real | Read-only |
| Departmentnumber | mserp_departmentnumber | String | Read-only |
| Unionagreementeffective | mserp_unionagreementeffective | Date time offset | Read-only |
| Detaileffective | mserp_detaileffective | Date time offset | Read-only |
| Workerassignmentreasoncode | mserp_workerassignmentreasoncode | Real | Read-only |
| Laborunionid | mserp_laborunionid | String | Read-only |
| Compensationregion | mserp_compensationregion | Real | Read-only |
| Insurancebenefit Bigint | mserp_insurancebenefit_bigint | Int64 | Read-only |
| Workerassignmentend | mserp_workerassignmentend | Date time offset | Read-only |
| Legalentity Bigint | mserp_legalentity_bigint | Int64 | Read-only |
| Job Bigint | mserp_job_bigint | Int64 | Read-only |
| Insurancebenefit | mserp_insurancebenefit | Real | Read-only |
| Paycycle Bigint | mserp_paycycle_bigint | Int64 | Read-only |
| Issalarygenerated | mserp_issalarygenerated | Enum | Read-only |
| Title | mserp_title | Real | Read-only |
| Benefitid | mserp_benefitid | String | Read-only |
| Activation | mserp_activation | Date time offset | Read-only |
| Unionagreementexpiration | mserp_unionagreementexpiration | Date time offset | Read-only |
| Positionid | mserp_positionid | String | Read-only |
| Workerassignmentreasoncode Bigint | mserp_workerassignmentreasoncode_bigint | Int64 | Read-only |
| Reportstoexpiration | mserp_reportstoexpiration | Date time offset | Read-only |
| Payrolldetaileffective | mserp_payrolldetaileffective | Date time offset | Read-only |
| Fulltimeequivalent | mserp_fulltimeequivalent | Real | Read-only |
| Unionagreement | mserp_unionagreement | Real | Read-only |
| Paidbylegalentity | mserp_paidbylegalentity | String | Read-only |
| Description | mserp_description | String | Read-only |
| Schedule | mserp_schedule | String | Read-only |
| Positiontypeid | mserp_positiontypeid | String | Read-only |
| Unionagreement Bigint | mserp_unionagreement_bigint | Int64 | Read-only |
| Retirement | mserp_retirement | Date time offset | Read-only |
| Reportstopositionid | mserp_reportstopositionid | String | Read-only |
| Isprimaryposition | mserp_isprimaryposition | Enum | Read-only |
| Department Bigint | mserp_department_bigint | Int64 | Read-only |
| Workerpersonnelnumber | mserp_workerpersonnelnumber | String | Read-only |
| Legalentity | mserp_legalentity | Real | Read-only |
| Paycycleid | mserp_paycycleid | String | Read-only |
| Job | mserp_job | Real | Read-only |
| Paidby Bigint | mserp_paidby_bigint | Int64 | Read-only |
| Compensationregionid | mserp_compensationregionid | String | Read-only |
| Detailexpiration | mserp_detailexpiration | Date time offset | Read-only |
| Schedulelegalentity | mserp_schedulelegalentity | String | Read-only |
| Titleid | mserp_titleid | String | Read-only |
| Unionagreementname | mserp_unionagreementname | String | Read-only |
| Compensationregion Bigint | mserp_compensationregion_bigint | Int64 | Read-only |
| Annualregularhours | mserp_annualregularhours | Real | Read-only |
| Worker | mserp_worker | Real | Read-only |
| Reportstoeffective | mserp_reportstoeffective | Date time offset | Read-only |
| Workerassignmentreasoncodeid | mserp_workerassignmentreasoncodeid | String | Read-only |
| Workerassignmentstart | mserp_workerassignmentstart | Date time offset | Read-only |
| Positiontype | mserp_positiontype | Real | Read-only |
| Title Bigint | mserp_title_bigint | Int64 | Read-only |
| Payrolldetailexpiration | mserp_payrolldetailexpiration | Date time offset | Read-only |
| Payperiodovertimehours | mserp_payperiodovertimehours | Real | Read-only |
| Jobid | mserp_jobid | String | Read-only |
| Workername | mserp_workername | String | Read-only |
| Availableforassignment | mserp_availableforassignment | Date time offset | Read-only |
| Areearningsgeneratedfromschedule | mserp_areearningsgeneratedfromschedule | Enum | Read-only |

## Example query for PayIntV1HcmPositionEntity

Entity name: mserp_payintv1hcmpositionentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpositionentities
```

**Response**

```JSON
{  
    "mserp_insurancebenefit": 0,
    "mserp_unionagreementname": "",
    "mserp_paycycle_bigint": 5637145336,
    "mserp_unionagreementlegalentity": "",
    "mserp_activation": "2005-01-01T08:00:00Z",
    "mserp_laborunionid": "",
    "mserp_unionagreement": 0,
    "mserp_schedulelegalentity": "USMF",
    "mserp_compensationregionid": "Central",
    "mserp_department_bigint": 22565423100,
    "mserp_fulltimeequivalent": 1,
    "mserp_workerassignmentreasoncode_bigint": 22565420937,
    "mserp_title": 22565421000,
    "mserp_positiontypeid": "Full-time",
    "mserp_annualregularhours": 2080,
    "mserp_compensationregion_bigint": 16928090027,
    "mserp_positiontype": 16928090027,
    "mserp_unionagreementexpiration": null,
    "mserp_title_bigint": 22565421000,
    "mserp_unionagreementeffective": null,
    "mserp_worker": 22565420995,
    "mserp_workerpersonnelnumber": "000023",
    "mserp_worker_bigint": 22565420995,
    "mserp_payrolldetailexpiration": "2154-12-31T00:00:00Z",
    "mserp_payrolldetaileffective": "2005-01-01T00:00:00Z",
    "mserp_workername": "Ahmed Barnett",
    "mserp_paycycle": 5637145336,
    "mserp_titleid": "Waterspider",
    "mserp_unionagreement_bigint": 0,
    "mserp_job_bigint": 22565421019,
    "mserp_workerassignmentstart": "2008-03-05T08:00:00Z",
    "mserp_paidby": 22565422580,
    "mserp_detaileffective": "2016-07-06T18:11:33Z",
    "mserp_legalentity_bigint": 22565422580,
    "mserp_issalarygenerated": 200000000,
    "mserp_isprimaryposition": 200000001,
    "mserp_paidbylegalentity": "USMF",
    "mserp_workerassignmentreasoncode": 22565420937,
    "mserp_workerassignmentend": "2154-12-31T23:59:59Z",
    "mserp_reportstoeffective": "2012-09-18T22:01:02Z",
    "mserp_areearningsgeneratedfromschedule": 200000001,
    "mserp_reportstopositionid": "000280",
    "mserp_payperiodovertimehours": 0,
    "mserp_detailexpiration": "2154-12-31T23:59:59Z",
    "mserp_insurancebenefit_bigint": 0,
    "mserp_defaultearningcodeid": "Regular",
    "mserp_positionid": "000001",
    "mserp_benefitid": "",
    "mserp_paidby_bigint": 22565422580,
    "mserp_compensationregion": 16928090027,
    "mserp_availableforassignment": null,
    "mserp_paycycleid": "w",
    "mserp_department": 22565423100,
    "mserp_jobid": "Waterspider",
    "mserp_legalentity": 22565422580,
    "mserp_job": 22565421019,
    "mserp_description": "Waterspider",
    "mserp_schedule": "Payroll",
    "mserp_workerassignmentreasoncodeid": "Career",
    "mserp_positiontype_bigint": 16928090027,
    "mserp_retirement": "2154-12-31T23:59:59Z",
    "mserp_departmentnumber": "023",
    "mserp_reportstoexpiration": "2154-12-31T23:59:59Z"
}
```
