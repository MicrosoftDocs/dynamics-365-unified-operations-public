---
# required metadata

title: Variable Compensation Type entity
description: This article provides details and an example query for the Hcm Variable Compensation Type entity in Microsoft Dynamics 365 Human Resources.
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

# Variable Compensation Type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Variable Compensation Type entity (PayIntV1HcmVariableCompensationTypeEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the variable compensation type.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Dataareaid | mserp_dataareaid | String | Read-only |
| Type | mserp_type | Enum | Read-only |
| Variablecompensationtype | mserp_variablecompensationtype | String | Read-only |
| Description | mserp_description | String | Read-only |

## Example query for PayIntV1HcmVariableCompensationTypeEntity

Entity name: mserp_payintv1hcmvariablecompensationtypeentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmvariablecompensationtypeentities
```

**Response**

```JSON
{  
    "mserp_dataareaid": "usmf",
    "mserp_type": 200000000,
    "mserp_variablecompensationtype": "Bonus",
    "mserp_description": "Bonus"
}
```
