---
# required metadata

title: Position Type entity
description: This article provides details and an example query for the HCM Position Type entity in Microsoft Dynamics 365 Human Resources.
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

# Position Type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Position Type entity (PayIntV1HcmPositionTypeEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the position type.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Classification | mserp_classification | Enum | Read-only |
| Description | mserp_description | String | Read-only |
| Positiontypeid | mserp_positiontypeid | String | Read-only |

## Example query for PayIntV1HcmPositionTypeEntity

Entity name: mserp_payintv1hcmpositiontypeentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpositiontypeentities
```

**Response**

```JSON
{  
    "mserp_classification": 200000001,
    "mserp_description": "Full-time employee",
    "mserp_positiontypeid": "Full-time"
}
```
