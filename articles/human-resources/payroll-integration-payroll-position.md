---
# required metadata

title: Payroll Position entity
description: This article provides details and an example query for the Payroll Position entity in Microsoft Dynamics 365 Human Resources.
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

# Payroll Position entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Payroll Position entity (PayIntV1PayrollPositionEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the payroll position.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Validto | mserp_validto | Date time offset | Read-only |
| Paidbylegalentity | mserp_paidbylegalentity | String | Read-only |
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Paycycleid | mserp_paycycleid | String | Read-only |
| Annualregularhours | mserp_annualregularhours | Real | Read-only |
| Positionid | mserp_positionid | String | Read-only |

## Example query for PayIntV1PayrollPositionEntity

Entity name: mserp_payintv1payrollpositionentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1payrollpositionentities
```

**Response**

```JSON
{  
    "mserp_validto": "2024-01-01T00:00:00Z",
    "mserp_paidbylegalentity": "USMF",
    "mserp_validfrom": "2024-01-01T00:00:00Z",
    "mserp_paycycleid": "w",
    "mserp_annualregularhours": 2080,
    "mserp_positionid": "000001"
}
```
