---
# required metadata

title: Labor Union entity
description: This article provides details and an example query for the HCM Labor Union entity in Microsoft Dynamics 365 Human Resources.
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

# Labor Union entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Labor Union entity (PayIntV1HcmLaborUnionEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the labor unions.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Unionid | mserp_unionid | String | Read-only |
| Entitledtonegotiate | mserp_entitledtonegotiate | Enum | Read-only |
| Name | mserp_name | String | Read-only |

## Example query for PayIntV1HcmLaborUnionEntity

Entity name: mserp_payintv1hcmlaborunionentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmlaborunionentities
```

**Response**

```JSON
{  
    "mserp_unionid": "UCA",
    "mserp_entitledtonegotiate": 200000001,
    "mserp_name": "United Consultants of America"
}
```
