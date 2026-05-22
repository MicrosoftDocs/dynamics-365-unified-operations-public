---
# required metadata

title: Payroll Position Details entity
description: This article provides details and an example query for the Payroll Position Details entity in Microsoft Dynamics 365 Human Resources.
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

# Payroll Position Details entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Payroll Position Details entity (PayIntV1PayrollPositionDetailsEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about details of payroll position.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Validto | mserp_validto | Date time offset | Read-only |
| Issalarygenerated | mserp_issalarygenerated | Enum | Read-only |
| Payperiodovertimehours | mserp_payperiodovertimehours | Real | Read-only |
| Positionid | mserp_positionid | String | Read-only |
| Benefitid | mserp_benefitid | String | Read-only |
| Schedule | mserp_schedule | String | Read-only |
| Paycycle | mserp_paycycle | Real | Read-only |
| Paidbylegalentity | mserp_paidbylegalentity | String | Read-only |
| Schedulelegalentity | mserp_schedulelegalentity | String | Read-only |
| Paycycle Bigint | mserp_paycycle_bigint | Int64 | Read-only |
| Defaultearningcodeid | mserp_defaultearningcodeid | String | Read-only |
| Areearningsgeneratedfromschedule | mserp_areearningsgeneratedfromschedule | Enum | Read-only |
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Annualregularhours | mserp_annualregularhours | Real | Read-only |
| Paycycleid | mserp_paycycleid | String | Read-only |

## Example query for PayIntV1PayrollPositionDetailsEntity

Entity name: mserp_payintv1payrollpositiondetailsentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1payrollpositiondetailsentities
```

**Response**

```JSON
{  
    "mserp_paycycle": 5637145336,
    "mserp_positionid": "000001",
    "mserp_validto": "2154-12-31T00:00:00Z",
    "mserp_payperiodovertimehours": 0,
    "mserp_issalarygenerated": 200000000,
    "mserp_areearningsgeneratedfromschedule": 200000001,
    "mserp_defaultearningcodeid": "Regular",
    "mserp_schedule": "Payroll",
    "mserp_validfrom": "2005-01-01T00:00:00Z",
    "mserp_annualregularhours": 2080,
    "mserp_paycycle_bigint": 5637145336,
    "mserp_paidbylegalentity": "USMF",
    "mserp_paycycleid": "w",
    "mserp_schedulelegalentity": "USMF",
    "mserp_benefitid": ""
}
```
