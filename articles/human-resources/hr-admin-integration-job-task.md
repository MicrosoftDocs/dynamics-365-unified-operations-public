---
# required metadata

title: Job task entity
description: This article provides details and an example query for the Job task entity in Microsoft Dynamics 365 Human Resources.
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

# Job task entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Job task entity for Dynamics 365 Human Resources.

## Description

This entity provides information about the job task.

## Properties

| Property | Physical name | Type | Use | Description |
|---|---|---|---|---|
| Description | mshr\_Description | String | Read-only| The description of the job task. |
| JobTaskId | mshr\_JobTaskId | String | Read-only | The ID of the job task. |
| Note | mshr\_Note | String | Read-only | Notes for the job task. |

## Example query for PayIntV1HcmJobTaskEntity

**Request**

Entity name: mshr\_hcmjobtaskentities

```http 
GET [Organization URI]/api/data/v9.1/mshr_hcmjobtaskentities
```

**Response**

```json
{
    "mshr_description": "Customer calls",
    "mshr_jobtaskid": "Customer calls",
    "mshr_note": "This job includes communication with the customers, and stakeholders.",
}
```
