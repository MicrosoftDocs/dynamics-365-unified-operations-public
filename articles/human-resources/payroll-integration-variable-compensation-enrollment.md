---
# required metadata

title: Variable Compensation Enrollment entity
description: This article provides details and an example query for the HCM Variable Compensation Enrollment entity in Microsoft Dynamics 365 Human Resources.
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

# Variable Compensation Enrollment entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.40.

This article describes the HCM Variable Compensation Enrollment entity (PayIntV1HcmVariableCompensationEnrollmentEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about variable compensation enrollment.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Dimensiondisplayvalue | mserp_dimensiondisplayvalue | String | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Status | mserp_status | Enum | Read-only |
| Dataareaid | mserp_dataareaid | String | Read-only |
| Awardamount | mserp_awardamount | Real | Read-only |
| Numberofunitsreal | mserp_numberofunitsreal | Real | Read-only |
| Awardpercent | mserp_awardpercent | Real | Read-only |
| Plan | mserp_plan | String | Read-only |
| Hireruledate | mserp_hireruledate | Date time offset | Read-only |
| Expirationdate | mserp_expirationdate | Date time offset | Read-only |
| Effectivedate | mserp_effectivedate | Date time offset | Read-only |

## Example query for PayIntV1HcmVariableCompensationEnrollmentEntity

Entity name: mserp_payintv1hcmvariablecompensationenrollmententities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmvariablecompensationenrollmententities
```

**Response**

```JSON
{  
    "mserp_dimensiondisplayvalue": "--026",
    "mserp_personnelnumber": "000001",
    "mserp_status": 200000001,
    "mserp_dataareaid": "usmf",
    "mserp_awardamount": 0,
    "mserp_numberofunitsreal": 0,
    "mserp_awardpercent": 6.5,
    "mserp_plan": "MgBonus",
    "mserp_hireruledate": "2024-01-01T00:00:00Z",
    "mserp_expirationdate": "2024-01-01T00:00:00Z",
    "mserp_effectivedate": "2024-01-01T00:00:00Z"
}
```
