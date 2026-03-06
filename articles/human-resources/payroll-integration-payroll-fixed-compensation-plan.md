---
# required metadata

title: Payroll Fixed Compensation Plan entity
description: This article provides details and an example query for the Payroll Fixed Compensation Plan entity in Microsoft Dynamics 365 Human Resources.
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

# Payroll Fixed Compensation Plan entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Payroll Fixed Compensation Plan entity (PayIntV1PayrollFixedCompensationPlanEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about fixed compensation plan for payroll employee.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Payrate | mserp_payrate | Real | Read-only |
| Processtype | mserp_processtype | Enum | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Currency | mserp_currency | String | Read-only |
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Type | mserp_type | Enum | Read-only |
| Planid | mserp_planid | String | Read-only |
| Linenum | mserp_linenum | Real | Read-only |
| Dataareaid | mserp_dataareaid | String | Read-only |
| Validto | mserp_validto | Date time offset | Read-only |
| Positionid | mserp_positionid | String | Read-only |
| Actionid | mserp_actionid | String | Read-only |
| Payfrequency | mserp_payfrequency | String | Read-only |

## Example query for PayIntV1PayrollFixedCompensationPlanEntity

Entity name: mserp_payintv1payrollfixedcompensationplanentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1payrollfixedcompensationplanentities
```

**Response**

```JSON
{  
    "mserp_payrate": 19,
    "mserp_processtype": 200000003,
    "mserp_personnelnumber": "000001",
    "mserp_currency": "USD",
    "mserp_validfrom": "2024-01-01T00:00:00Z",
    "mserp_type": 200000003,
    "mserp_planid": "StepC",
    "mserp_linenum": 0,
    "mserp_dataareaid": "usmf",
    "mserp_validto": "2024-01-01T00:00:00Z",
    "mserp_positionid": "000001",
    "mserp_actionid": "Hire",
    "mserp_payfrequency": "Hourly"
}
```
