---
# required metadata

title: Variable compensation type entity
description: This article provides details and an example query for the Variable compensation type entity in Microsoft Dynamics 365 Human Resources.
author: jcart
ms.date: 05/10/2024
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

# Variable compensation type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Variable compensation type entity (payintv1hcmvariablecompensationtypeentities) for Dynamics 365 Human Resources. 

Physical name: mserp_payintv1hcmvariablecompensationtypeentities

## Description

This entity provides information about the payroll position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| Description | mserp_Description | String | Read-only |
| Type | mserp_Type | Enum | Read-only |
| TypeId | mserp_VariableCompensationType | String | Read-only |

## Example query for the Variable compensation type entity

Entity name: mserp_payintv1hcmvariablecompensationtypeentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmvariablecompensationtypeentities
```

**Response**

```JSON
{  
    "mserp_description": "Bonus",  
    "mserp_type": 200000000,  
    "mserp_variablecompensationtype": "Bonus",  
    "mserp_dataareaid": "usmf",  
}
```
