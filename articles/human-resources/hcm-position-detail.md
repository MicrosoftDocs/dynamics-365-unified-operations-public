---
# required metadata

title: HCM position detail entity
description: This article provides details and an example query for the HCM position detail entity in Microsoft Dynamics 365 Human Resources.
author: jcart
ms.date: 05/22/2024
ms.topic: article
ms.reviewer: twheeloc

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

# HCM position detail entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM position detail entity (payintv1hcmpositiondetailentities) for Dynamics 365 Human Resources.

Physical name: mserp\_payintv1hcmpositiondetailentities

## Description

This entity provides information about the position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| mserp\_AvailableForAssignment | AvailableForAssignment | Date time offset | Read-only |
| mserp\_CompensationRegion | CompensationRegion | Int64 | Read-only |
| mserp\_CompensationRegionId | CompensationRegionId | String | Read-only |
| mserp\_Department | Department | Int64 | Read-only |
| mserp\_DepartmentNumber | DepartmentNumber | String | Read-only |
| mserp\_Description | Description | String | Read-only |
| mserp\_FullTimeEquivalent | FullTimeEquivalent | Real | Read-only |
| mserp\_Job | Job | Int64 | Read-only |
| mserp\_JobId | JobId | String | Read-only |
| mserp\_Position | Position | Int64 | Read-only |
| mserp\_PositionId | PositionId | String | Read-only |
| mserp\_PositionType | PositionType | Int64 | Read-only |
| mserp\_PositionTypeId | PositionTypeId | String | Read-only |
| mserp\_Title | Title | Int64 | Read-only |
| mserp\_TitleId | TitleId | String | Read-only |
| mserp\_ValidFrom | ValidFrom | Date time offset | Read-only |
| mserp\_ValidTo | ValidTo | Date time offset | Read-only |
| mserp\_JobFamilyId | JobFamilyId | String | Read-only |
| mserp\_JobFamily | JobFamily | Int64 | Read-only |

## Example query for the HCM position detail entity

Entity name: mserp\_payintv1hcmpositiondetailentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/payintv1hcmpositiondetailentities
```

**Response**

```JSON
{
    "mserp_compensationregionid": "",
    "mserp_departmentnumber": "",
    "mserp_description": "Waterspider",
    "mserp_fulltimeequivalent": 1,
    "mserp_jobid": "Waterspider",
    "mserp_positionid": "000001",
    "mserp_positiontypeid": "",
    "mserp_titleid": "Waterspider",
    "mserp_validfrom": "2005-01-01T08:00:00Z",
    "mserp_validto": "2012-09-18T22:01:18Z",
    "mserp_jobfamilyid": "",
}
```
