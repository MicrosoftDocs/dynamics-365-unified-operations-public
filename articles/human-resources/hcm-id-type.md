---
# required metadata

title: HCM identification type entity
description: This article provides details and an example query for the HCM identification type entity in Microsoft Dynamics 365 Human Resources.
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

# HCM identification type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM identification type entity (payintv1hcmidentificationtypeentities) for Dynamics 365 Human Resources.

Physical name: mserp\_payintv1hcmidentificationtypeentities

## Description

This entity provides information about the identification type details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| mserp\_Description | Description | String | Read-only |
| mserp\_IdentificationTypeId | IdentificationTypeId | String | Read-only |
| mserp\_CheckDuplicates | CheckDuplicates | Enum | Read-only |
| mserp\_AllowedValues | AllowedValues | Enum | Read-only |
| mserp\_IdentificationNumberFormat | IdentificationNumberFormat | String | Read-only |
| mserp\_FixedLength | FixedLength | Int | Read-only |

## Example query for the HCM identification type entity

Entity name: mserp\_payintv1hcmidentificationtypeentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/payintv1hcmidentificationtypeentities
```

**Response**

```JSON
{
    "mserp_description": "Alien/Admission no.",
    "mserp_identificationtypeid": "Alien/Admission",
    "mserp_checkduplicates": 200000000,
    "mserp_allowedvalues": 200000000,
    "mserp_identificationnumberformat": "",
    "mserp_fixedlength": 0,
}
```
