---
# required metadata

title: HCM Position hierarchy type entity
description: This article provides details and an example query for the HCM Position hierarchy type table entity in Microsoft Dynamics 365 Human Resources.
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

# HCM Position hierarchy type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Position hierarchy type entity (payintv1hcmpositionhierarchytypeentity) for Dynamics 365 Human Resources.

Physical name: mserp_payintv1hcmpositionhierarchytypeentity

## Description

This entity provides information about the payroll position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| HierarchyType | mserp_HierarchyType | Enum | Read-only |
| Name | mserp_Name | String | Read-only |
| IsImmutable | mserp_IsImmutable | Enum | Read-only |

## Example query for the HCM Position hierarchy type entity

**Request**

Entity name: mserp_payintv1hcmpositionhierarchytypeentity

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpositionhierarchytypeentity_
```

**Response**

```JSON
{  
    "mserp_name": "Line",  
}
```
