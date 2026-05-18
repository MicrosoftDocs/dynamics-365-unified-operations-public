---
# required metadata

title: Position Worker Assignment entity
description: This article provides details and an example query for the HCM Position Worker Assignment entity in Microsoft Dynamics 365 Human Resources.
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

# Position Worker Assignment entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Position Worker Assignment entity (PayIntV1HcmPositionWorkerAssignmentEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the position worker assignment.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Positionid | mserp_positionid | String | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Isprimaryposition | mserp_isprimaryposition | Enum | Read-only |
| Worker | mserp_worker | Real | Read-only |
| Reasoncode | mserp_reasoncode | Real | Read-only |
| Position | mserp_position | Real | Read-only |
| Reasoncodeid | mserp_reasoncodeid | String | Read-only |
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Validto | mserp_validto | Date time offset | Read-only |
| Position Bigint | mserp_position_bigint | Int64 | Read-only |
| Worker Bigint | mserp_worker_bigint | Int64 | Read-only |
| Reasoncode Bigint | mserp_reasoncode_bigint | Int64 | Read-only |

## Example query for PayIntV1HcmPositionWorkerAssignmentEntity

Entity name: mserp_payintv1hcmpositionworkerassignmententities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpositionworkerassignmententities
```

**Response**

```JSON
{  
    "mserp_positionid": "000256",
    "mserp_personnelnumber": "000001",
    "mserp_isprimaryposition": 200000001,
    "mserp_worker": 22565420973,
    "mserp_reasoncode": 22565420940,
    "mserp_position": 22565421259,
    "mserp_reasoncodeid": "Reorganization",
    "mserp_validfrom": "2024-01-01T00:00:00Z",
    "mserp_validto": "2024-01-01T00:00:00Z",
    "mserp_position_bigint": 22565421259,
    "mserp_worker_bigint": 22565420973,
    "mserp_reasoncode_bigint": 22565420940
}
```
