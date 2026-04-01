---
# required metadata

title: Variable compensation type entity
description: This article provides details and an example query for the Variable compensation type entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
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
ms.author: twheeloc
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Variable compensation type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Variable compensation type entity for Dynamics 365 Human Resources. 

Physical name: mshr_hcmvariablecompensationtypeentities

## Description

This entity provides information about the payroll position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| Description | mshr_Description | String | Read-only |
| Type | mshr_Type | Enum | Read-only |
| TypeId | mshr_VariableCompensationType | String | Read-only |

## Example query for the Variable compensation type entity

Entity name: mshr_hcmvariablecompensationtypeentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mshr_hcmvariablecompensationtypeentities
```

**Response**

```JSON
{  
    "mshr_description": "Bonus",  
    "mshr_type": 200000000,  
    "mshr_variablecompensationtype": "Bonus",  
    "mshr_dataareaid": "usmf",  
}
```
