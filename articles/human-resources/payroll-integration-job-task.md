---
# required metadata

title: Job Task entity
description: This article provides details and an example query for the Hcm Job Task entity in Microsoft Dynamics 365 Human Resources.
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

# Job Task entity

> [!NOTE]
> The functionality that is noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Job Task entity (PayIntV1HcmJobTaskEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about job task.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Jobtaskid | mserp_jobtaskid | String | Read-only |
| Description | mserp_description | String | Read-only |
| Note | mserp_note | String | Read-only |

## Example query for PayIntV1HcmJobTaskEntity

Entity name: mserp_payintv1hcmjobtaskentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmjobtaskentities
```

**Response**

```JSON
{  
    "mserp_jobtaskid": "Systems",
    "mserp_description": "Internal systems",
    "mserp_note": "Internal systems design and maintenance."
}
```
