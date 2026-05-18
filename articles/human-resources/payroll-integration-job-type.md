---
# required metadata

title: Job Type entity
description: This article provides details and an example query for the HCM Job Type entity in Microsoft Dynamics 365 Human Resources.
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

# Job Type entity

> [!NOTE]
> The functionality that is noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Job Type entity (PayIntV1HcmJobTypeEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about job types.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| System Modifiedby | mserp_system_modifiedby | String | Read-only |
| System Modifieddatetime | mserp_system_modifieddatetime | Date time offset | Read-only |
| System Createdby | mserp_system_createdby | String | Read-only |
| System Createddatetime | mserp_system_createddatetime | Date time offset | Read-only |
| Exemptstatus | mserp_exemptstatus | Enum | Read-only |
| Paidhourly | mserp_paidhourly | Enum | Read-only |
| Jobtypeid | mserp_jobtypeid | String | Read-only |
| Description | mserp_description | String | Read-only |

## Example query for PayIntV1HcmJobTypeEntity

Entity name: mserp_payintv1hcmjobtypeentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmjobtypeentities
```

**Response**

```JSON
{  
    "mserp_system_modifiedby": "JACOB",
    "mserp_system_modifieddatetime": "2024-01-01T00:00:00Z",
    "mserp_system_createdby": "JACOB",
    "mserp_system_createddatetime": "2024-01-01T00:00:00Z",
    "mserp_exemptstatus": 200000002,
    "mserp_paidhourly": 200000000,
    "mserp_jobtypeid": "Clerical",
    "mserp_description": "Clerical"
}
```
