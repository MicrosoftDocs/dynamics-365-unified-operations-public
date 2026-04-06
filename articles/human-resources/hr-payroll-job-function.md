---
# required metadata

title: Job function entity
description: This article provides details and an example query for the Job function entity in Microsoft Dynamics 365 Human Resources.
author: avanish2821
ms.date: 03/25/2026
ms.topic: how-to

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

# Job function entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Job function entity for Dynamics 365 Human Resources.

Physical name: mshr\_HcmJobFunctionEntity

## Description

This entity provides information about the job function.

## Properties

| Property | Physical name | Type | Use | Description |
|---|---|---|---|---|
| Description | mshr\_Description | String | Read-only | The description of the job function. |
| JobFunctionId | mshr\_JobFunctionId | String | Read-only | The ID of the job function. |
| RegulatoryJobCategory | mshr\_RegulatoryJobCategory | Enum | Read-only | The category of the job. |

## Example query for HCM Job function entity

**Request**

Entity name: mshr\_hcmjobfunctionentities

```http 
GET [Organization URI]/api/data/v9.1/mshr_hcmjobfunctionentities_
```

**Response**

```json
{
    "mshr_description": "Officials and Manager",
    "mshr_jobfunctionid": "0100",
    "mshr_regulatoryjobcategory": 200000000,
}
```
