---
# required metadata

title: Position Default Dimension entity
description: This article provides details and an example query for the Hcm Position Default Dimension entity in Microsoft Dynamics 365 Human Resources.
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

# Position Default Dimension entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Position Default Dimension entity (PayIntV1HcmPositionDefaultDimensionEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the position default dimension.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Distributiontemplateid | mserp_distributiontemplateid | String | Read-only |
| Positionid | mserp_positionid | String | Read-only |
| Dataareaid | mserp_dataareaid | String | Read-only |
| Dimensiondisplayvalue | mserp_dimensiondisplayvalue | String | Read-only |
| Legalentitydataarea | mserp_legalentitydataarea | String | Read-only |
| Templatelegalentityid | mserp_templatelegalentityid | String | Read-only |

## Example query for PayIntV1HcmPositionDefaultDimensionEntity

Entity name: mserp_payintv1hcmpositiondefaultdimensionentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpositiondefaultdimensionentities
```

**Response**

```JSON
{  
    "mserp_distributiontemplateid": "Payroll",
    "mserp_positionid": "000006",
    "mserp_dataareaid": "USMF",
    "mserp_dimensiondisplayvalue": "-014-024",
    "mserp_legalentitydataarea": "USMF",
    "mserp_templatelegalentityid": "USMF"
}
```
