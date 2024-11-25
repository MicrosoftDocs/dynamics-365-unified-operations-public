---
# required metadata

title: Job type entity
description: This article provides details and an example query for the Job type entity in Microsoft Dynamics 365 Human Resources.
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

# Job type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Job type entity (PayIntV1HcmJobTypeEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the job type.

## Properties

| Property | Physical name | Type | Use | Description |
|---|---|---|---|---|
| Description | mserp\_description | String | Read-only | The description of the job type. |
| exemptstatus | mserp\_exemptstatus | Enum | Read-only| A value that indicates whether the job type is exempt or not exempt from Fair Labor Standards Act (FLSA) coverage. Alternatively, a value that indicates that FLSA doesn't apply to the job type. |
| JobTypeId | mserp\_jobtypeid | String | Read-only | The ID of the job type. |
| PaidHourly | mserp\_PaidHourly | Enum | Read-only | A value that indicates whether the job is paid hourly. |
| CreatedBy | mserp\_System\_CreatedBy | Date time offset | Read-only | Created-by details for the job type. |
| CreatedDateTime | mserp\_System\_CreatedDateTime | Date time offset | Read-only| The date and time when the job type was created. |
| ModifiedBy | mserp\_System\_ModifiedBy | Date time offset | Read-only| Modified-by details for the job type. |
| ModifiedDateTime | mserp\_System\_ModifiedDateTime | Date time offset | Read-only | The data and time when the job type was modified. |

## Example query for PayIntV1HcmJobTypeEntity

**Request**

Entity name: mserp\_payintv1hcmjobtypeentities

```http 
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmjobtypeentities
```

**Response**

```json
{
    "mserp_description": "Clerical",
    "mserp_exemptstatus": 200000002,
    "mserp_jobtypeid": "Clerical",
    "mserp_paidhourly": 200000000,
    "mserp_system_createdby": "JACOB",
    "mserp_system_createddatetime": "2016-09-14T14:38:59Z",
    "mserp_system_modifiedby": "JACOB",
    "mserp_system_modifieddatetime": "2016-09-14T14:38:59Z",
}
```
