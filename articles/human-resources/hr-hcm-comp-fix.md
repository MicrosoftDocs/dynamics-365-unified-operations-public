---
# required metadata

title: HCM Compensation fixed plan entity
description: This article provides details and an example query for the PayIntV1HcmCompFixedEmplEntity in Microsoft Dynamics 365 Human Resources.
author: jcart
ms.date: 04/10/2024
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
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# HCM Compensation fixed plan entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Compensation fixed plan entity (PayIntV1HcmCompFixedEmplEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the human capital management (HCM) fixed compensation plan of the employee.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Action | mserp\_Action| String | Read-only |
| Currency | mserp\_Currency | String | Read-only |
| Dimension | mserp\_Dimension | Int64 | Read-only |
| LineNumber | mserp\_LineNumber | Real | Read-only |
| PayFrequency | mserp\_PayFrequency | String | Read-only |
| PayRate | mserp\_PayRate | Real | Read-only |
| Amount | mserp\_Amount | Real | Read-only |
| Plan | mserp\_Plan | String | Read-only |
| PlanId | mserp\_PlanId | String | Read-only |
| Position | mserp\_Position | Int64 | Read-only |
| ProcessType | mserp\_ProcessType | Enum | Read-only |
| Step | mserp\_Step | String | Read-only |
| Reference | mserp\_Reference | Int64 | Read-only |
| Type | mserp\_Type | Enum | Read-only |
| EffectiveDate | mserp\_EffectiveDate | Date time offset | Read-only |
| ExpirationDate | mserp\_ExpirationDate | Date time offset | Read-only |
| Worker | mserp\_Worker | Int64 | Read-only |
| PositionId | mserp\_PositionId | String | Read-only |
| PersonnelNumber | mserp\_PersonnelNumber | String | Read-only |
| DimensionDisplayValue | mserp_DimensionDisplayValue | String | Read-only |
| | | Int64 | Read-only |
| CompensationLevelId | mserp_CompensationLevelId | String | Read-only |
| RefPointSetupId | mserp_RefPointSetupId | String | Read-only |

## Example query for PayIntV1HcmCompFixedEmplEntity

Entity name: mserp\_payintv1hcmcompfixedemplentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmcompfixedemplentities_
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
}
```
