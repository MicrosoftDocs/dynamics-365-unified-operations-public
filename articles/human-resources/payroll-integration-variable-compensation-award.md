---
# required metadata

title: Variable Compensation Award entity
description: This article provides details and an example query for the Hcm Variable Compensation Award entity in Microsoft Dynamics 365 Human Resources.
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

# Variable Compensation Award entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.40.

This article describes the Hcm Variable Compensation Award entity (PayIntV1HcmVariableCompensationAwardEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the variable compensation award.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Planid | mserp_planid | String | Read-only |
| Unitvaluev2 | mserp_unitvaluev2 | Real | Read-only |
| Positionvalidto | mserp_positionvalidto | Date time offset | Read-only |
| Fixedplanid | mserp_fixedplanid | String | Read-only |
| Dataareaid | mserp_dataareaid | String | Read-only |
| Unitsreal | mserp_unitsreal | Real | Read-only |
| Positionvalidfrom | mserp_positionvalidfrom | Date time offset | Read-only |
| Defaultdimensiondisplayvalue | mserp_defaultdimensiondisplayvalue | String | Read-only |
| Unitcurrencycode | mserp_unitcurrencycode | String | Read-only |
| Awardtype | mserp_awardtype | Enum | Read-only |
| Positionid | mserp_positionid | String | Read-only |
| Awarddate | mserp_awarddate | Date time offset | Read-only |
| Sequence | mserp_sequence | Real | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Processtype | mserp_processtype | Enum | Read-only |

## Example query for PayIntV1HcmVariableCompensationAwardEntity

Entity name: mserp_payintv1hcmvariablecompensationawardentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmvariablecompensationawardentities
```

**Response**

```JSON
{  
    "mserp_planid": "MgBonus",
    "mserp_unitvaluev2": 0,
    "mserp_positionvalidto": "2024-01-01T00:00:00Z",
    "mserp_fixedplanid": "",
    "mserp_dataareaid": "usmf",
    "mserp_unitsreal": 0,
    "mserp_positionvalidfrom": "2024-01-01T00:00:00Z",
    "mserp_defaultdimensiondisplayvalue": "",
    "mserp_unitcurrencycode": "USD",
    "mserp_awardtype": 200000000,
    "mserp_positionid": "",
    "mserp_awarddate": "2024-01-01T00:00:00Z",
    "mserp_sequence": 0,
    "mserp_personnelnumber": "000001",
    "mserp_processtype": 200000003
}
```
