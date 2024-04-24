---
# required metadata

title: Job base entity
description: This article provides details and an example query for the Job base entity in Microsoft Dynamics 365 Human Resources.
author: jcart
ms.date: 04/04/2024
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
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Job base entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Job base entity (PayIntV1HcmJobBaseEntity) for Dynamics 365 Human Resources.

## Description

This entity is the base entity that provides information about the job.

## Properties

| Property | Physical name | Type | Use | Description |
|---|---|---|---|---|
| JobId | mserp\_JobId | String | Read-only | The ID of the job. |
| MaximumPositions | mserp\_MaximumPositions | Integer | Read-only | The maximum number of positions that are allowed for the job. |
| AllowUnlimitedPositions | mserp\_AllowUnlimitedPositions | NoYes | Read-only | A value that indicates whether unlimited positions are allowed for the job. |

## Example query for PayIntV1HcmJobBaseEntity

**Request**

Entity name: mserp\_payintv1hcmjobbaseentities\_

```http 
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmjobbaseentities_
```

**Response**

```json
{
    "mserp_jobid": "VP of Operations",
    "mserp_maximumnumberofpositions": 2147483647,
    "mserp_allowunlimitedpositions": 200000001,_
}
```
