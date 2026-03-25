---
# required metadata

title: Position Hierarchy entity
description: This article provides details and an example query for the HCM Position Hierarchy entity in Microsoft Dynamics 365 Human Resources.
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

# Position Hierarchy entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Position Hierarchy entity (PayIntV1HcmPositionHierarchyEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the position hierarchy.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Parentpositionid | mserp_parentpositionid | String | Read-only |
| Positionid | mserp_positionid | String | Read-only |
| Hierarchytypename | mserp_hierarchytypename | String | Read-only |
| Validto | mserp_validto | Date time offset | Read-only |

## Example query for PayIntV1HcmPositionHierarchyEntity

Entity name: mserp_payintv1hcmpositionhierarchyentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpositionhierarchyentities
```

**Response**

```JSON
{  
    "mserp_validfrom": "2024-01-01T00:00:00Z",
    "mserp_parentpositionid": "000100",
    "mserp_positionid": "000287",
    "mserp_hierarchytypename": "Line",
    "mserp_validto": "2024-01-01T00:00:00Z"
}
```
