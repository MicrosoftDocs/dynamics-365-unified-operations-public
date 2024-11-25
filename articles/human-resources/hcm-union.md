---
# required metadata

title: HCM unions entity
description: This article provides details and an example query for the HCM unions entity in Microsoft Dynamics 365 Human Resources.
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

# HCM unions entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM unions entity (payintv1hcmunionsentities) for Dynamics 365 Human Resources.

Physical name: mserp_payintv1hcmunionsentities

## Description

This entity provides information about the payroll position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| name | mserp_name | String | Read-only |
| Negotiator | mserp_negotiator | Enum | Read-only |
| UnionID | mserp_UnionID | String | Read-only |

## Example query for the HCM unions entity

Entity name: mserp__payintv1hcmunionsentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmunionsentities
```

**Response**

```JSON
{  
    "mserp_name": "United Consultants of America",  
    "mserp_negotiator": 200000001,  
    "mserp_unionid": "UCA",  
}
```
