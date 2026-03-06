---
# required metadata

title: Job type entity
description: This article provides details and an example query for the Job type entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 04/04/2024
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

# Job type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Job type entity for Dynamics 365 Human Resources.

## Description

This entity provides information about the job type.

## Properties

| Property | Physical name | Type | Use | Description |
|---|---|---|---|---|
| Description | mshr\_description | String | Read-only | The description of the job type. |
| exemptstatus | mshr\_exemptstatus | Enum | Read-only| A value that indicates whether the job type is exempt or not exempt from Fair Labor Standards Act (FLSA) coverage. Alternatively, a value that indicates that FLSA doesn't apply to the job type. |
| JobTypeId | mshr\_jobtypeid | String | Read-only | The ID of the job type. |
| PaidHourly | mshr\_PaidHourly | Enum | Read-only | A value that indicates whether the job is paid hourly. |
| CreatedBy | mshr\_System\_CreatedBy | Date time offset | Read-only | Created-by details for the job type. |
| CreatedDateTime | mshr\_System\_CreatedDateTime | Date time offset | Read-only| The date and time when the job type was created. |
| ModifiedBy | mshr\_System\_ModifiedBy | Date time offset | Read-only| Modified-by details for the job type. |
| ModifiedDateTime | mshr\_System\_ModifiedDateTime | Date time offset | Read-only | The data and time when the job type was modified. |

## Example query for PayIntV1HcmJobTypeEntity

**Request**

Entity name: mshr\_hcmjobtypeentities

```http 
GET [Organization URI]/api/data/v9.1/mshr_hcmjobtypeentities
```

**Response**

```json
{
    "mshr_description": "Clerical",
    "mshr_exemptstatus": 200000002,
    "mshr_jobtypeid": "Clerical",
    "mshr_paidhourly": 200000000,
    "mshr_system_createdby": "JACOB",
    "mshr_system_createddatetime": "2016-09-14T14:38:59Z",
    "mshr_system_modifiedby": "JACOB",
    "mshr_system_modifieddatetime": "2016-09-14T14:38:59Z",
}
```
