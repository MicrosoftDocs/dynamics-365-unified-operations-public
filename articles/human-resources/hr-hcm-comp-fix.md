---
# required metadata

title: HCM Compensation fixed plan entity
description: This article provides details and an example query for the PayIntV1HcmCompFixedEmplEntity in Microsoft Dynamics 365 Human Resources.
author: avanish2821
ms.date: 03/25/2026
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

# HCM Compensation fixed plan entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Compensation fixed plan entity for Dynamics 365 Human Resources.

## Description

This entity provides information about the human capital management (HCM) fixed compensation plan of the employee.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Action | mshr\_Action| String | Read-only |
| Currency | mshr\_Currency | String | Read-only |
| Dimension | mshr\_Dimension | Int64 | Read-only |
| LineNumber | mshr\_LineNumber | Real | Read-only |
| PayFrequency | mshr\_PayFrequency | String | Read-only |
| PayRate | mshr\_PayRate | Real | Read-only |
| Amount | mshr\_Amount | Real | Read-only |
| Plan | mshr\_Plan | String | Read-only |
| PlanId | mshr\_PlanId | String | Read-only |
| Position | mshr\_Position | Int64 | Read-only |
| ProcessType | mshr\_ProcessType | Enum | Read-only |
| Step | mshr\_Step | String | Read-only |
| Reference | mshr\_Reference | Int64 | Read-only |
| Type | mshr\_Type | Enum | Read-only |
| EffectiveDate | mshr\_EffectiveDate | Date time offset | Read-only |
| ExpirationDate | mshr\_ExpirationDate | Date time offset | Read-only |
| Worker | mshr\_Worker | Int64 | Read-only |
| PositionId | mshr\_PositionId | String | Read-only |
| PersonnelNumber | mshr\_PersonnelNumber | String | Read-only |
| DimensionDisplayValue | mshr_DimensionDisplayValue | String | Read-only |
| | | Int64 | Read-only |
| CompensationLevelId | mshr_CompensationLevelId | String | Read-only |
| RefPointSetupId | mshr_RefPointSetupId | String | Read-only |

## Example query for PayIntV1HcmCompFixedEmplEntity

Entity name: mshr\_hcmcompfixedemplentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mshr_hcmcompfixedemplentities_
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
}
```
