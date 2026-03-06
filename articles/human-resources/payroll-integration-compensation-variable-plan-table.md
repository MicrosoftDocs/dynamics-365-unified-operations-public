---
# required metadata

title: Compensation Variable Plan Table entity
description: This article provides details and an example query for the Hcm Comp Var Plan Table entity in Microsoft Dynamics 365 Human Resources.
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

# Compensation Variable Plan Table entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Comp Var Plan Table entity (PayIntV1HcmCompVarPlanTableEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the compensation variable plan table.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Enableenrollment | mserp_enableenrollment | Enum | Read-only |
| Enablelevels | mserp_enablelevels | Enum | Read-only |
| Leverageminimum | mserp_leverageminimum | Real | Read-only |
| Percentofbasis | mserp_percentofbasis | Real | Read-only |
| Variableawardbasis | mserp_variableawardbasis | Enum | Read-only |
| Vestingrule | mserp_vestingrule | String | Read-only |
| Leverage100percent | mserp_leverage100percent | Real | Read-only |
| Hirerule | mserp_hirerule | Enum | Read-only |
| Leverageoverobjective | mserp_leverageoverobjective | Real | Read-only |
| Effectivedate | mserp_effectivedate | Date time offset | Read-only |
| Planid | mserp_planid | String | Read-only |
| Leveragemaximum | mserp_leveragemaximum | Real | Read-only |
| Leveragetolerancemax | mserp_leveragetolerancemax | Enum | Read-only |
| Numberofunitsreal | mserp_numberofunitsreal | Real | Read-only |
| Leveragetolerancemin | mserp_leveragetolerancemin | Enum | Read-only |
| Expirationdate | mserp_expirationdate | Date time offset | Read-only |
| Calculationtype | mserp_calculationtype | Enum | Read-only |
| Awardbasiscalculation | mserp_awardbasiscalculation | Enum | Read-only |
| Dataareaid | mserp_dataareaid | String | Read-only |
| Description | mserp_description | String | Read-only |
| Variablecompensationtype | mserp_variablecompensationtype | String | Read-only |
| Unitvalue | mserp_unitvalue | Real | Read-only |
| Leverageunderobjective | mserp_leverageunderobjective | Real | Read-only |
| Enablerecommendation | mserp_enablerecommendation | Enum | Read-only |
| Unitcurrencycode | mserp_unitcurrencycode | String | Read-only |
| Unitrelationship | mserp_unitrelationship | Enum | Read-only |

## Example query for PayIntV1HcmCompVarPlanTableEntity

Entity name: mserp_payintv1hcmcompvarplantableentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmcompvarplantableentities
```

**Response**

```JSON
{  
    "mserp_enableenrollment": 200000001,
    "mserp_enablelevels": 200000001,
    "mserp_leverageminimum": 0,
    "mserp_percentofbasis": 5,
    "mserp_variableawardbasis": 200000000,
    "mserp_vestingrule": "",
    "mserp_leverage100percent": 0,
    "mserp_hirerule": 200000001,
    "mserp_leverageoverobjective": 0,
    "mserp_effectivedate": "2024-01-01T00:00:00Z",
    "mserp_planid": "MgBonus",
    "mserp_leveragemaximum": 0,
    "mserp_leveragetolerancemax": 200000000,
    "mserp_numberofunitsreal": 0,
    "mserp_leveragetolerancemin": 200000000,
    "mserp_expirationdate": "2024-01-01T00:00:00Z",
    "mserp_calculationtype": 200000000,
    "mserp_awardbasiscalculation": 200000000,
    "mserp_dataareaid": "usmf",
    "mserp_description": "Management Bonus",
    "mserp_variablecompensationtype": "Bonus",
    "mserp_unitvalue": 1,
    "mserp_leverageunderobjective": 0,
    "mserp_enablerecommendation": 200000001,
    "mserp_unitcurrencycode": "USD",
    "mserp_unitrelationship": 200000001
}
```
