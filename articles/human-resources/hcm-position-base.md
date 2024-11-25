---
# required metadata

title: HCM position base entity
description: This article provides details and an example query for the HCM position base entity in Microsoft Dynamics 365 Human Resources.
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

# HCM position base entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM position base entity (payintv1hcmpositionbaseentities) for Dynamics 365 Human Resources.

Physical name: mserp\_payintv1hcmpositionbaseentities

## Description

This entity provides information about the base position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| mserp\_PositionId | PositionId | String | Read-only |

## Example query for the HCM position base entity

Entity name: mserp\_payintv1hcmpositionbaseentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/payintv1hcmpositionbaseentities
```

**Response**

```JSON
{
    "mserp_positionid": "000001",
}
```
