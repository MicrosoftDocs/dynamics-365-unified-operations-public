---
# required metadata

title: Job Base entity
description: This article provides details and an example query for the Hcm Job Base entity in Microsoft Dynamics 365 Human Resources.
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

# Job Base entity

> [!NOTE]
> The functionality that is noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Job Base entity (PayIntV1HcmJobBaseEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about jobs.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Jobid | mserp_jobid | String | Read-only |
| Maximumnumberofpositions | mserp_maximumnumberofpositions | Int | Read-only |
| Allowunlimitedpositions | mserp_allowunlimitedpositions | Enum | Read-only |

## Example query for PayIntV1HcmJobBaseEntity

Entity name: mserp_payintv1hcmjobbaseentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmjobbaseentities
```

**Response**

```JSON
{  
    "mserp_jobid": "VP of Operations",
    "mserp_maximumnumberofpositions": 2147483647,
    "mserp_allowunlimitedpositions": 200000001
}
```
