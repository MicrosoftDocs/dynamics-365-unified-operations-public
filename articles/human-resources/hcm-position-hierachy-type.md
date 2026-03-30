---
# required metadata

title: HCM Position hierarchy type entity
description: This article provides details and an example query for the HCM Position hierarchy type table entity in Microsoft Dynamics 365 Human Resources.
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

# HCM Position hierarchy type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Position hierarchy type entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmpositionhierarchytypeentity

## Description

This entity provides information about the payroll position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| HierarchyType | mshr_HierarchyType | Enum | Read-only |
| Name | mshr_Name | String | Read-only |
| IsImmutable | mshr_IsImmutable | Enum | Read-only |

## Example query for the HCM Position hierarchy type entity

**Request**

Entity name: mshr_hcmpositionhierarchytypeentity

```HTTP
GET [Organization URI]/api/data/v9.1/mshr_hcmpositionhierarchytypeentity_
```

**Response**

```JSON
{  
    "mshr_name": "Line",  
}
```
