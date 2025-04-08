---
# required metadata

title: HCM Fixed Compensation employee entity
description: This article provides details and an example query for the HCM Fixed Compensation employee entity in Microsoft Dynamics 365 Human Resources.
author: jcart
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
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# HCM Fixed Compensation employee entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Fixed Compensation employee entity (payintv1hcmcompfixedemplentities) for Dynamics 365 Human Resources.

Physical name: mserp\_payintv1hcmcompfixedemplentities

## Description

This entity provides information about the employee fixed compensation details.

## Properties

| Physical name| Property |Type | Use |
|---|---|---|---|
| mserp\_Action | Action | String | Read-only |
| mserp\_Currency | Currency | String | Read-only |
| mserp\_Dimension | Dimension | Int64 | Read-only |
| mserp\_LineNumber | LineNumber | Real | Read-only |
| mserp\_PayFrequency | PayFrequency | String | Read-only |
| mserp\_PayRate | PayRate | Real | Read-only |
| mserp\_Amount | Amount | Real | Read-only |
| mserp\_Plan | Plan | String | Read-only |
| mserp\_PlanId | PlanId | String | Read-only |
| mserp\_Position | Position | Int64 | Read-only |
| mserp\_ProcessType | ProcessType | Enum | Read-only |
| mserp\_Step | Step | String | Read-only |
| mserp\_Reference | Reference | Int64 | Read-only |
| mserp\_Type | Type | Enum | Read-only |
| mserp\_EffectiveDate | EffectiveDate | Date time offset | Read-only |
| mserp\_ExpirationDate | ExpirationDate | Date time offset | Read-only |
| mserp\_Worker | Worker | Int64 | Read-only |
| mserp\_PositionId | PositionId | String | Read-only |
| mserp\_PersonnelNumber | PersonnelNumber | String | Read-only |
| mserp\_DimensionDisplayValue | DimensionDisplayValue | String | Read-only |
| mserp\_CompensationLevel | CompensationLevel | Int64 | Read-only |
| mserp\_CompensationLevelId | CompensationLevelId | String | Read-only |
| mserp\_RefPointSetupId | RefPointSetupId | String | Read-only |

## Example query for the HCM Fixed compensation employee entity

Entity name: mserp\_payintv1hcmcompfixedemplentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/payintv1hcmcompfixedemplentities
```

**Response**

```JSON
{
    "mserp_action": "Hire",
    "mserp_currency": "USD",
    "mserp_dimension": 0,
    "mserp_dimension_bigint": 0,
    "mserp_linenumber": 0,
    "mserp_payfrequency": "Hourly",
    "mserp_payrate": 19,
    "mserp_amount": 39520,
    "mserp_plan": "StepC",
    "mserp_planid": "StepC",
    "mserp_position": 22565421004,
    "mserp_position_bigint": 22565421004,
    "mserp_processtype": 200000003,
    "mserp_step": "Step 2",
    "mserp_reference": 0,
    "mserp_reference_bigint": 0,
    "mserp_type": 200000003,
    "mserp_effectivedate": "2008-03-05T00:00:00Z",
    "mserp_expirationdate": "2016-01-01T00:00:00Z",
    "mserp_worker": 22565420995,
    "mserp_worker_bigint": 22565420995,
    "mserp_positionid": "000001",
    "mserp_personnelnumber": "000023",
    "mserp_dimensiondisplayvalue": "",
    "mserp_compensationlevel": 16928090052,
    "mserp_compensationlevel_bigint": 16928090052,
    "mserp_compensationlevelid": "S2",
    "mserp_refpointsetupid": "Steps",
    "mserp_dataareaid": "usmf",
}
```
