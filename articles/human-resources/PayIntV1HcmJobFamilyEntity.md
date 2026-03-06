---
# required metadata

title: Job Family entity
description: This article provides details and an example query for the Hcm Job Family entity in Microsoft Dynamics 365 Human Resources.
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

# Job Family entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Job Family entity (PayIntV1HcmJobFamilyEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the job family.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Jobfamilyid | mserp_jobfamilyid | String | Read-only |
| Description | mserp_description | String | Read-only |

## Example query for PayIntV1HcmJobFamilyEntity

Entity name: mserp_payintv1hcmjobfamilyentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmjobfamilyentities
```

**Response**

```JSON
{  
    "mserp_jobfamilyid": "Sales Associate",
    "mserp_description": "Sales job family"
}
```
