---
# required metadata

title: HCM position detail entity
description: This article provides details and an example query for the HCM position detail entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
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
ms.author: twheeloc
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# HCM position detail entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM position detail entity for Dynamics 365 Human Resources.

Physical name: mshr\_hcmpositiondetailentities

## Description

This entity provides information about the position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| mshr\_AvailableForAssignment | AvailableForAssignment | Date time offset | Read-only |
| mshr\_CompensationRegion | CompensationRegion | Int64 | Read-only |
| mshr\_CompensationRegionId | CompensationRegionId | String | Read-only |
| mshr\_Department | Department | Int64 | Read-only |
| mshr\_DepartmentNumber | DepartmentNumber | String | Read-only |
| mshr\_Description | Description | String | Read-only |
| mshr\_FullTimeEquivalent | FullTimeEquivalent | Real | Read-only |
| mshr\_Job | Job | Int64 | Read-only |
| mshr\_JobId | JobId | String | Read-only |
| mshr\_Position | Position | Int64 | Read-only |
| mshr\_PositionId | PositionId | String | Read-only |
| mshr\_PositionType | PositionType | Int64 | Read-only |
| mshr\_PositionTypeId | PositionTypeId | String | Read-only |
| mshr\_Title | Title | Int64 | Read-only |
| mshr\_TitleId | TitleId | String | Read-only |
| mshr\_ValidFrom | ValidFrom | Date time offset | Read-only |
| mshr\_ValidTo | ValidTo | Date time offset | Read-only |
| mshr\_JobFamilyId | JobFamilyId | String | Read-only |
| mshr\_JobFamily | JobFamily | Int64 | Read-only |

## Example query for the HCM position detail entity

Entity name: mshr\_hcmpositiondetailentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mshr_hcmpositiondetailentities
```

**Response**

```JSON
{
    "mshr_compensationregionid": "",
    "mshr_departmentnumber": "",
    "mshr_description": "Waterspider",
    "mshr_fulltimeequivalent": 1,
    "mshr_jobid": "Waterspider",
    "mshr_positionid": "000001",
    "mshr_positiontypeid": "",
    "mshr_titleid": "Waterspider",
    "mshr_validfrom": "2005-01-01T08:00:00Z",
    "mshr_validto": "2012-09-18T22:01:18Z",
    "mshr_jobfamilyid": "",
}
```
