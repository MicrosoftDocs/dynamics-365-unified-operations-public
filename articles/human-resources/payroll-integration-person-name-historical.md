---
# required metadata

title: Person Name Historical entity
description: This article provides details and an example query for the Dir Person Name Historical entity in Microsoft Dynamics 365 Human Resources.
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

# Dir Person Name Historical entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Dir Person Name Historical entity (PayIntV1DirPersonNameHistoricalEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about history of person name.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Firstname | mserp_firstname | String | Read-only |
| Lastnameprefix | mserp_lastnameprefix | String | Read-only |
| Lastname | mserp_lastname | String | Read-only |
| Middlename | mserp_middlename | String | Read-only |
| Validto | mserp_validto | Date time offset | Read-only |
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Partynumber | mserp_partynumber | String | Read-only |

## Example query for PayIntV1DirPersonNameHistoricalEntity

Entity name: mserp_payintv1dirpersonnamehistoricalentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1dirpersonnamehistoricalentities
```

**Response**

```JSON
{  
    "mserp_firstname": "Jodi",
    "mserp_lastnameprefix": "",
    "mserp_lastname": "Christiansen",
    "mserp_middlename": "",
    "mserp_validto": "2024-01-01T00:00:00Z",
    "mserp_validfrom": "2024-01-01T00:00:00Z",
    "mserp_partynumber": "000000032"
}
```
