---
# required metadata

title: Position Base entity
description: This article provides details and an example query for the HCM Position Base entity in Microsoft Dynamics 365 Human Resources.
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

# Position Base entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Position Base entity (PayIntV1HcmPositionBaseEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the position base.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Positionid | mserp_positionid | String | Read-only |

## Example query for PayIntV1HcmPositionBaseEntity

Entity name: mserp_payintv1hcmpositionbaseentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpositionbaseentities
```

**Response**

```JSON
{  
    "mserp_positionid": "000001"
}
```
