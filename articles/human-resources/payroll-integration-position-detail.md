---
# required metadata

title: Position Detail entity
description: This article provides details and an example query for the HCM Position Detail entity in Microsoft Dynamics 365 Human Resources.
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

# Position Detail entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM Position Detail entity (PayIntV1HcmPositionDetailEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the position detail.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Positionid | mserp_positionid | String | Read-only |
| Positiontypeid | mserp_positiontypeid | String | Read-only |
| Validto | mserp_validto | Date time offset | Read-only |
| Jobid | mserp_jobid | String | Read-only |
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Jobfamilyid | mserp_jobfamilyid | String | Read-only |
| Departmentnumber | mserp_departmentnumber | String | Read-only |
| Compensationregionid | mserp_compensationregionid | String | Read-only |
| Fulltimeequivalent | mserp_fulltimeequivalent | Real | Read-only |
| Titleid | mserp_titleid | String | Read-only |
| Description | mserp_description | String | Read-only |
| Availableforassignment | mserp_availableforassignment | Date time offset | Read-only |

## Example query for PayIntV1HcmPositionDetailEntity

Entity name: mserp_payintv1hcmpositiondetailentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpositiondetailentities
```

**Response**

```JSON
{  
    "mserp_positionid": "000001",
    "mserp_positiontypeid": "",
    "mserp_validto": "2024-01-01T00:00:00Z",
    "mserp_jobid": "Waterspider",
    "mserp_validfrom": "2024-01-01T00:00:00Z",
    "mserp_jobfamilyid": "",
    "mserp_departmentnumber": "034",
    "mserp_compensationregionid": "",
    "mserp_fulltimeequivalent": 1,
    "mserp_titleid": "Waterspider",
    "mserp_description": "Waterspider",
    "mserp_availableforassignment": "2024-01-01T00:00:00Z"
}
```
