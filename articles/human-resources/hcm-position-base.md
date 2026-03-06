---
# required metadata

title: HCM position base entity
description: This article provides details and an example query for the HCM position base entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
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
ms.author: twheeloc
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# HCM position base entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM position base entity for Dynamics 365 Human Resources.

Physical name: mshr\_hcmpositionbaseentities

## Description

This entity provides information about the base position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| mshr\_PositionId | PositionId | String | Read-only |

## Example query for the HCM position base entity

Entity name: mshr\_hcmpositionbaseentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mshr_hcmpositionbaseentities
```

**Response**

```JSON
{
    "mshr_positionid": "000001",
}
```
