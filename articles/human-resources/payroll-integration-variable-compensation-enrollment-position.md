---
# required metadata

title: Variable Compensation Enrollment Position entity
description: This article provides details and an example query for the Hcm Variable Compensation Enrollment Position entity in Microsoft Dynamics 365 Human Resources.
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

# Hcm Variable Compensation Enrollment Position entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.45.

This article describes the Hcm Variable Compensation Enrollment Position entity (PayIntV2HcmVariableCompensationEnrollmentPositionEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the variable compensation enrollment position for worker.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Dataareaid | mserp_dataareaid | String | Read-only |
| Positionvalidfrom | mserp_positionvalidfrom | Date time offset | Read-only |
| Planvalidfrom | mserp_planvalidfrom | Date time offset | Read-only |
| Partynumber | mserp_partynumber | String | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Positionid | mserp_positionid | String | Read-only |
| Positionvalidto | mserp_positionvalidto | Date time offset | Read-only |
| Planid | mserp_planid | String | Read-only |

## Example query for PayIntV2HcmVariableCompensationEnrollmentPositionEntity

Entity name: mserp_payintv2hcmvariablecompensationenrollmentpositionentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv2hcmvariablecompensationenrollmentpositionentities
```

**Response**

```JSON
{  
    "mserp_dataareaid": "usmf",
    "mserp_positionvalidfrom": "2024-01-01T00:00:00Z",
    "mserp_planvalidfrom": "2024-01-01T00:00:00Z",
    "mserp_partynumber": "000023",
    "mserp_personnelnumber": "000001",
    "mserp_positionid": "000001",
    "mserp_positionvalidto": "2024-01-01T00:00:00Z",
    "mserp_planid": "StepC"
}
```
