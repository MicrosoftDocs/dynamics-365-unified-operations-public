---
# required metadata

title: Job family entity
description: This article provides details and an example query for the Job family entity in Microsoft Dynamics 365 Human Resources.
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

# Job family entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Job family entity (PayIntV1HcmJobFamilyEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the job family.

## Properties

| Property | Physical name | Type | Use | Description |
|---|---|---|---|---|
| JobFamilyId | mserp\_JobFamilyId | String | Read-only | The ID of the job family. |
| Description | mserp\_Description | String | Read-only | The description of the job family. |

## Example query for PayIntV1HcmJobFamilyEntity

**Request**

Entity name: mserp\_payintv1hcmjobfamilyentities

```http
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmjobfamilyentities_
```

**Response**

```json
{
    "mserp_jobfamilyid": "Finance Jobs",
    "mserp_description": "Accounting, Payroll",
}
```
