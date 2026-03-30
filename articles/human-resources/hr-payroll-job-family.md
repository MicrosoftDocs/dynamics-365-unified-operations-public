---
# required metadata

title: Job family entity
description: This article provides details and an example query for the Job family entity in Microsoft Dynamics 365 Human Resources.
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

# Job family entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Job family entity for Dynamics 365 Human Resources.

## Description

This entity provides information about the job family.

## Properties

| Property | Physical name | Type | Use | Description |
|---|---|---|---|---|
| JobFamilyId | mshr\_JobFamilyId | String | Read-only | The ID of the job family. |
| Description | mshr\_Description | String | Read-only | The description of the job family. |

## Example query for HCM job family entity

**Request**

Entity name: mshr\_hcmjobfamilyentities

```http
GET [Organization URI]/api/data/v9.1/mshr_hcmjobfamilyentities_
```

**Response**

```json
{
    "mshr_jobfamilyid": "Finance Jobs",
    "mshr_description": "Accounting, Payroll",
}
```
