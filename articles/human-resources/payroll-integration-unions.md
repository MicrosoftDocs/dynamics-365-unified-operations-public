---
# required metadata

title: Unions entity
description: This article provides details and an example query for the HCM Unions entity in Microsoft Dynamics 365 Human Resources.
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

# Unions entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Unions entity (PayIntV1HcmUnionsEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the unions.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Unionid | mserp_unionid | String | Read-only |
| Name | mserp_name | String | Read-only |
| Negotiator | mserp_negotiator | Enum | Read-only |

## Example query for PayIntV1HcmUnionsEntity

Entity name: mserp_payintv1hcmunionsentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmunionsentities
```

**Response**

```JSON
{  
    "mserp_unionid": "UCA",
    "mserp_name": "United Consultants of America",
    "mserp_negotiator": 200000001
}
```
