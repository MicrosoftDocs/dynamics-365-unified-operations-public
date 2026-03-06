---
# required metadata

title: HCM Fixed Compensation employee entity
description: This article provides details and an example query for the HCM Fixed Compensation employee entity in Microsoft Dynamics 365 Human Resources.
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

# HCM Fixed Compensation employee entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Fixed Compensation employee entity for Dynamics 365 Human Resources.

Physical name: mshr\_hcmcompfixedemplentities

## Description

This entity provides information about the employee fixed compensation details.

## Properties

| Physical name| Property |Type | Use |
|---|---|---|---|
| mshr\_Action | Action | String | Read-only |
| mshr\_Currency | Currency | String | Read-only |
| mshr\_Dimension | Dimension | Int64 | Read-only |
| mshr\_LineNumber | LineNumber | Real | Read-only |
| mshr\_PayFrequency | PayFrequency | String | Read-only |
| mshr\_PayRate | PayRate | Real | Read-only |
| mshr\_Amount | Amount | Real | Read-only |
| mshr\_Plan | Plan | String | Read-only |
| mshr\_PlanId | PlanId | String | Read-only |
| mshr\_Position | Position | Int64 | Read-only |
| mshr\_ProcessType | ProcessType | Enum | Read-only |
| mshr\_Step | Step | String | Read-only |
| mshr\_Reference | Reference | Int64 | Read-only |
| mshr\_Type | Type | Enum | Read-only |
| mshr\_EffectiveDate | EffectiveDate | Date time offset | Read-only |
| mshr\_ExpirationDate | ExpirationDate | Date time offset | Read-only |
| mshr\_Worker | Worker | Int64 | Read-only |
| mshr\_PositionId | PositionId | String | Read-only |
| mshr\_PersonnelNumber | PersonnelNumber | String | Read-only |
| mshr\_DimensionDisplayValue | DimensionDisplayValue | String | Read-only |
| mshr\_CompensationLevel | CompensationLevel | Int64 | Read-only |
| mshr\_CompensationLevelId | CompensationLevelId | String | Read-only |
| mshr\_RefPointSetupId | RefPointSetupId | String | Read-only |

## Example query for the HCM Fixed compensation employee entity

Entity name: mshr\_hcmcompfixedemplentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/hcmcompfixedemplentities
```

**Response**

```JSON
{
    "mshr_action": "Hire",
    "mshr_currency": "USD",
    "mshr_dimension": 0,
    "mshr_dimension_bigint": 0,
    "mshr_linenumber": 0,
    "mshr_payfrequency": "Hourly",
    "mshr_payrate": 19,
    "mshr_amount": 39520,
    "mshr_plan": "StepC",
    "mshr_planid": "StepC",
    "mshr_position": 22565421004,
    "mshr_position_bigint": 22565421004,
    "mshr_processtype": 200000003,
    "mshr_step": "Step 2",
    "mshr_reference": 0,
    "mshr_reference_bigint": 0,
    "mshr_type": 200000003,
    "mshr_effectivedate": "2008-03-05T00:00:00Z",
    "mshr_expirationdate": "2016-01-01T00:00:00Z",
    "mshr_worker": 22565420995,
    "mshr_worker_bigint": 22565420995,
    "mshr_positionid": "000001",
    "mshr_personnelnumber": "000023",
    "mshr_dimensiondisplayvalue": "",
    "mshr_compensationlevel": 16928090052,
    "mshr_compensationlevel_bigint": 16928090052,
    "mshr_compensationlevelid": "S2",
    "mshr_refpointsetupid": "Steps",
    "mshr_dataareaid": "usmf",
}
```
