---
# required metadata

title: Employee detail entity
description: This article provides details and an example query for the Employee detail entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 05/22/2024
ms.topic: article
ms.reviewer: twheeloc

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

# Employee detail entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Employee detail entity for Dynamics 365 Human Resources.

Physical name: mshr\_employmentdetailentity

## Description

This entity provides information about the employee details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| mshr\_AdjustedWorkerStartDate | AdjustedWorkerStartDate | Date Time Offset | Read-only |
| mshr\_EmployerQuantity | EmployerNoticeAmount | Int | Read-only |
| mshr\_EmployerUnit | EmployerUnit | Enum | Read-only |
| mshr\_LastDateWorked | LastDateWorked | Date Time Offset | Read-only |
| mshr\_TerminationDate | TransitionDate | Date Time Offset | Read-only |
| mshr\_Effective | Effective | Date Time Offset | Read-only |
| mshr\_Expiration | Expiration | Date Time Offset | Read-only |
| mshr\_WorkerNoticeAmount | WorkerNoticeAmount | Int | Read-only |
| mshr\_WorkerStartDate | WorkerStartDate | Date Time Offset | Read-only |
| mshr\_WorkerUnitOfNotice | WorkerUnitOfNotice | Enum | Read-only |
| mshr\_Status | Status | Enum | Read-only |
| mshr\_EmploymentStartDate | EmploymentStartDate | Date Time Offset | Read-only |
| mshr\_EmploymentEndDate | EmploymentEndDate | Date Time Offset | Read-only |
| mshr\_Company | Company | String | Read-only |
| mshr\_PersonnelNumber | PersonnelNumber | String | Read-only |
| mshr\_WorkerType | WorkerType | Enum | Read-only |
| mshr\_BenifitsEmploymentType | BenefitsEmploymentType | String | Read-only |
| mshr\_EmploymentCategory | EmploymentCategory | String | Read-only |
| mshr\_ReasonCodeId | ReasonCodeId | Int64 | Read-only |

## Example query for the Employee detail entity

Entity name: mshr\_employmentdetailentity

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/employmentdetailentity
```

**Response**

```JSON
{
    "mshr_employerquantity": 0,
    "mshr_employerunit": 200000000,
    "mshr_effective": "2012-09-11T20:30:58Z",
    "mshr_expiration": "2154-12-31T23:59:59Z",
    "mshr_workernoticeamount": 0,
    "mshr_workerstartdate": "2010-02-01T08:00:00Z",
    "mshr_workerunitofnotice": 200000000,
    "mshr_status": 200000000,
    "mshr_employmentstartdate": "2006-02-01T08:00:00Z",
    "mshr_employmentenddate": "2154-12-31T23:59:59Z",
    "mshr_company": "USMF",
    "mshr_personnelnumber": "000001",
    "mshr_workertype": 200000000,
    "mshr_benifitsemploymenttype": "",
    "mshr_employmentcategory": "",
    "mshr_reasoncodeid": 0,
    "mshr_reasoncodeid_bigint": 0,
    "mshr_adjustedworkerstartdate": null,
    "mshr_terminationdate": null,
    "mshr_lastdateworked": null,
}
```
