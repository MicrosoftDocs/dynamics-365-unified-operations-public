---
# required metadata

title: HCM unions entity
description: This article provides details and an example query for the HCM unions entity in Microsoft Dynamics 365 Human Resources.
author: avanish2821
ms.date: 03/25/2026
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

# HCM unions entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM unions entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmunionsentities

## Description

This entity provides information about the payroll position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| name | mshr_name | String | Read-only |
| Negotiator | mshr_negotiator | Enum | Read-only |
| UnionID | mshr_UnionID | String | Read-only |

## Example query for the HCM unions entity

Entity name: mshr_hcmunionsentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mshr_hcmunionsentities
```

**Response**

```JSON
{  
    "mshr_name": "United Consultants of America",  
    "mshr_negotiator": 200000001,  
    "mshr_unionid": "UCA",  
}
```
