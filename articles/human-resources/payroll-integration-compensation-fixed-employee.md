---
# required metadata

title: Compensation Fixed Employee entity
description: This article provides details and an example query for the Comp Fixed Empl entity in Microsoft Dynamics 365 Human Resources.
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

# Employee Fixed Compensation entity

> [!NOTE]
> The functionality that is noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Employee fixed compensation entity (PayIntV1HcmCompFixedEmplEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the employee fixed compensation plans.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Compensationlevel Bigint | mserp_compensationlevel_bigint | Int64 | Read-only |
| Payrate | mserp_payrate | Real | Read-only |
| Position Bigint | mserp_position_bigint | Int64 | Read-only |
| Expirationdate | mserp_expirationdate | Date time offset | Read-only |
| Dimensiondisplayvalue | mserp_dimensiondisplayvalue | String | Read-only |
| Linenumber | mserp_linenumber | Real | Read-only |
| Planid | mserp_planid | String | Read-only |
| Reference Bigint | mserp_reference_bigint | Int64 | Read-only |
| Positionid | mserp_positionid | String | Read-only |
| Compensationlevelid | mserp_compensationlevelid | String | Read-only |
| Processtype | mserp_processtype | Enum | Read-only |
| Action | mserp_action | String | Read-only |
| Amount | mserp_amount | Real | Read-only |
| Step | mserp_step | String | Read-only |
| Worker | mserp_worker | Real | Read-only |
| Type | mserp_type | Enum | Read-only |
| Compensationlevel | mserp_compensationlevel | Real | Read-only |
| Dataareaid | mserp_dataareaid | String | Read-only |
| Effectivedate | mserp_effectivedate | Date time offset | Read-only |
| Payfrequency | mserp_payfrequency | String | Read-only |
| Position | mserp_position | Real | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Refpointsetupid | mserp_refpointsetupid | String | Read-only |
| Currency | mserp_currency | String | Read-only |
| Plan | mserp_plan | String | Read-only |
| Reference | mserp_reference | Real | Read-only |
| Worker Bigint | mserp_worker_bigint | Int64 | Read-only |

## Example query for PayIntV1HcmCompFixedEmplEntity

Entity name: mserp_payintv1hcmcompfixedemplentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmcompfixedemplentities
```

**Response**

```JSON
{  
    "mserp_compensationlevel_bigint": 16928090052,
    "mserp_payrate": 19,
    "mserp_position_bigint": 22565421004,
    "mserp_expirationdate": "2024-01-01T00:00:00Z",
    "mserp_dimensiondisplayvalue": "",
    "mserp_linenumber": 0,
    "mserp_planid": "StepC",
    "mserp_reference_bigint": 0,
    "mserp_positionid": "000001",
    "mserp_compensationlevelid": "S2",
    "mserp_processtype": 200000003,
    "mserp_action": "Hire",
    "mserp_amount": 39520,
    "mserp_step": "Step 2",
    "mserp_worker": 22565421016,
    "mserp_type": 200000001,
    "mserp_compensationlevel": 16928090059,
    "mserp_dataareaid": "usmf",
    "mserp_effectivedate": "2024-01-01T00:00:00Z",
    "mserp_payfrequency": "Annual",
    "mserp_position": 22565421004,
    "mserp_personnelnumber": "000023",
    "mserp_refpointsetupid": "Steps",
    "mserp_currency": "USD",
    "mserp_plan": "StepC",
    "mserp_reference": 0,
    "mserp_worker_bigint": 22565421016
}
```
