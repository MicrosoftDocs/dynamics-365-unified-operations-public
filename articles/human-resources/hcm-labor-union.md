---
# required metadata

title: HCM Labor union entity
description: This article provides details and an example query for the HCM Labor union entity in Microsoft Dynamics 365 Human Resources.
author: jcart
ms.date: 05/22/2024
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

# HCM Labor union entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Labor union entity (payintv1hcmlaborunionentities) for Dynamics 365 Human Resources.

Physical name: mserp\_payintv1hcmlaborunionentities

## Description

This entity provides information about the labor union details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| mserp\_Name | name | String | Read-only |
| mserp\_EntitledToNegotiate | EntitledToNegotiate | Enum | Read-only |
| mserp\_UnionId | UnionID | String | Read-only |

## Example query for the HCM Labor union entity

Entity name: mserp\_payintv1hcmlaborunionentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/payintv1hcmlaborunionentities
```

**Response**

```JSON
{
    "mserp_name": "United Consultants of America",
    "mserp_entitledtonegotiate": 200000001,
    "mserp_unionid": "UCA",
}
```
