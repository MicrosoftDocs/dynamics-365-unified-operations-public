---
# required metadata

title: Position Hierarchy Type entity
description: This article provides details and an example query for the HCM Position Hierarchy Type entity in Microsoft Dynamics 365 Human Resources.
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

# Position Hierarchy Type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Position Hierarchy Type entity (PayIntV1HcmPositionHierarchyTypeEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the position hierarchy type.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Name | mserp_name | String | Read-only |

## Example query for PayIntV1HcmPositionHierarchyTypeEntity

Entity name: mserp_payintv1hcmpositionhierarchytypeentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpositionhierarchytypeentities
```

**Response**

```JSON
{  
    "mserp_name": "Line"
}
```
