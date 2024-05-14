---
# required metadata

title: HCM position type entity
description: This article provides details and an example query for the HCM position type entity in Microsoft Dynamics 365 Human Resources.
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

# HCM position type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM position type entity (payintv1hcmpositiontypeentities) for Dynamics 365 Human Resources.

Physical name: mserp_payintv1hcmpositiontypeentities

## Description

This entity provides information about the payroll position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| Description | mserp_Description | String | Read-only |
| HcmEmploymentStatus | mserp_Classification | Enum | Read-only |
| TypeId | mserp_PositionTypeId | String | Read-only |

## Example query for the HCM position type entity

Entity name: mserp_payintv1hcmpositiontypeentities

## Request

```http
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpositiontypeentities
```

**Response**

```JSON
{  
    "mserp_description": "Full-time employee",  
    "mserp_classification": 200000001,  
    "mserp_positiontypeid": "Full-time",  
}
```
