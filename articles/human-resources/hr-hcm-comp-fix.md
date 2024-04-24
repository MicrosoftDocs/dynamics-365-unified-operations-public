---
# required metadata

title: HCM Compensation fixed plan table entity
description: This article provides details and an example query for the Compensation fixed plan table entity in Microsoft Dynamics 365 Human Resources.
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

This article describes the entity **PayIntV1HcmCompFixedEmplEntity** for Dynamics 365 Human Resources.

## Description

This entity provides information about the HCM Compensation fixed plan of the employee.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Action| mserp_Action| String | Read-only |
| Currency| mserp_Currency|_String | Read-only |
| Dimension| mserp_Dimension|Int64 | Read-only |
| LineNumber| mserp_LineNumber| Real | Read-only |
| PayFrequency| Mserp_PayFrequency| String  | Read-only |
| PayRate| mserp_PayRate|  Real | Read-only |
| Amount| mserp_Amount| Real | Read-only |
| Plan| mserp_Plan| String | Read-only |
| PlanId| mserp_PlanId| String | Read-only |
| Position| mserp_Position| Int64 | Read-only |
| ProcessType| mserp_ProcessType| Enum | Read-only |
| Step| mserp_Step| String | Read-only |
| Reference| mserp_Reference| Int64 | Read-only |
| Type| mserp_Type| Enum | Read-only |
| EffectiveDate| mserp_EffectiveDate| Date time offset | Read-only |
| ExpirationDate| mserp_ExpirationDate| Date time offset | Read-only |
| Worker| mserp_Worker| Int64 | Read-only |
| PositionId| mserp_PositionId| String | Read-only |
| PersonnelNumber| mserp_PersonnelNumber| String | Read-only |
| DimensionDisplayValue| mserp_DimensionDisplayValue| String | Read-only |
| Int64 | Read-only |
| CompensationLevelId| mserp_CompensationLevelId| String | Read-only |
| RefPointSetupId| mserp_RefPointSetupId| String | Read-only |


## Example query for Employment Detail entity

Entity name: mserp_payintv1hcmcompfixedemplentities

**Request**

```HTTP
GET \[Organizaton URI\]/api/data/v9.1/mserp_payintv1hcmcompfixedemplentities_
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
