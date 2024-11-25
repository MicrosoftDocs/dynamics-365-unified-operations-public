---
# required metadata

title: Job function entity
description: This article provides details and an example query for the Job function entity in Microsoft Dynamics 365 Human Resources.
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

# Job function entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Job function entity (PayIntV1HcmJobFunctionEntity) for Dynamics 365 Human Resources.

Physical name: mserp\_PayIntV1HcmJobFunctionEntity

## Description

This entity provides information about the job function.

## Properties

| Property | Physical name | Type | Use | Description |
|---|---|---|---|---|
| Description | mserp\_Description | String | Read-only | The description of the job function. |
| JobFunctionId | mserp\_JobFunctionId | String | Read-only | The ID of the job function. |
| RegulatoryJobCategory | mserp\_RegulatoryJobCategory | Enum | Read-only | The category of the job. |

## Example query for PayIntV1HcmJobFunctionEntity

**Request**

Entity name: mserp\_payintv1hcmjobfunctionentities

```http 
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmjobfunctionentities_
```

**Response**

```json
{
    "mserp_description": "Officials and Manager",
    "mserp_jobfunctionid": "0100",
    "mserp_regulatoryjobcategory": 200000000,
}
```
