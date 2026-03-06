---
# required metadata

title: Employment Detail entity
description: This article provides details and an example query for the Employment Detail entity in Microsoft Dynamics 365 Human Resources.
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

# Employment Detail entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.42.

This article describes the Employment Detail entity (PayIntV2EmploymentDetailEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the employment detail for an employee.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Employmentenddate | mserp_employmentenddate | Date time offset | Read-only |
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Transitiondate | mserp_transitiondate | Date time offset | Read-only |
| Lastdateworked | mserp_lastdateworked | Date time offset | Read-only |
| Validto | mserp_validto | Date time offset | Read-only |
| Employernoticeamount | mserp_employernoticeamount | Int | Read-only |
| Reasoncodeid | mserp_reasoncodeid | String | Read-only |
| Payfrequencyid | mserp_payfrequencyid | String | Read-only |
| Benefitemploymentstatus | mserp_benefitemploymentstatus | Enum | Read-only |
| Employmentcategoryid | mserp_employmentcategoryid | String | Read-only |
| Employerunitofnotice | mserp_employerunitofnotice | Enum | Read-only |
| Workerunitofnotice | mserp_workerunitofnotice | Enum | Read-only |
| Employmenttype | mserp_employmenttype | Enum | Read-only |
| Employmentstartdate | mserp_employmentstartdate | Date time offset | Read-only |
| Workerstartdate | mserp_workerstartdate | Date time offset | Read-only |
| Workernoticeamount | mserp_workernoticeamount | Enum | Read-only |
| Adjustedworkerstartdate | mserp_adjustedworkerstartdate | Date time offset | Read-only |
| Employmenttypeid | mserp_employmenttypeid | String | Read-only |
| Legalentityid | mserp_legalentityid | String | Read-only |

## Example query for PayIntV2EmploymentDetailEntity

Entity name: mserp_payintv2employmentdetailentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv2employmentdetailentities
```

**Response**

```JSON
{  
    "mserp_personnelnumber": "000001",
    "mserp_employmentenddate": "2024-01-01T00:00:00Z",
    "mserp_validfrom": "2024-01-01T00:00:00Z",
    "mserp_transitiondate": "2024-01-01T00:00:00Z",
    "mserp_lastdateworked": "2024-01-01T00:00:00Z",
    "mserp_validto": "2024-01-01T00:00:00Z",
    "mserp_employernoticeamount": 200000000,
    "mserp_reasoncodeid": "",
    "mserp_payfrequencyid": "",
    "mserp_benefitemploymentstatus": 200000000,
    "mserp_employmentcategoryid": "",
    "mserp_employerunitofnotice": 200000000,
    "mserp_workerunitofnotice": 200000000,
    "mserp_employmenttype": 200000000,
    "mserp_employmentstartdate": "2024-01-01T00:00:00Z",
    "mserp_workerstartdate": "2024-01-01T00:00:00Z",
    "mserp_workernoticeamount": 0,
    "mserp_adjustedworkerstartdate": "2024-01-01T00:00:00Z",
    "mserp_employmenttypeid": "",
    "mserp_legalentityid": "USMF"
}
```
