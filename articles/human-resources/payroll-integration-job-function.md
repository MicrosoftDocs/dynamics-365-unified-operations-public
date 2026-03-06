---
# required metadata

title: Job Function entity
description: This article provides details and an example query for the Hcm Job Function entity in Microsoft Dynamics 365 Human Resources.
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

# Job Function entity

> [!NOTE]
> The functionality that is noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Job Function entity (PayIntV1HcmJobFunctionEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about job function.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Regulatoryjobcategory | mserp_regulatoryjobcategory | Enum | Read-only |
| Jobfunctionid | mserp_jobfunctionid | String | Read-only |
| Description | mserp_description | String | Read-only |

## Example query for PayIntV1HcmJobFunctionEntity

Entity name: mserp_payintv1hcmjobfunctionentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmjobfunctionentities
```

**Response**

```JSON
{  
    "mserp_regulatoryjobcategory": 200000000,
    "mserp_jobfunctionid": "0100",
    "mserp_description": "Officials and Manager"
}
```
