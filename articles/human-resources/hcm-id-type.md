---
# required metadata

title: HCM identification type entity
description: This article provides details and an example query for the HCM identification type entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 03/25/2026
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

# HCM identification type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM identification type entity for Dynamics 365 Human Resources.

Physical name: mshr\_hcmidentificationtypeentities

## Description

This entity provides information about the identification type details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| mshr\_Description | Description | String | Read-only |
| mshr\_IdentificationTypeId | IdentificationTypeId | String | Read-only |
| mshr\_CheckDuplicates | CheckDuplicates | Enum | Read-only |
| mshr\_AllowedValues | AllowedValues | Enum | Read-only |
| mshr\_IdentificationNumberFormat | IdentificationNumberFormat | String | Read-only |
| mshr\_FixedLength | FixedLength | Int | Read-only |

## Example query for the HCM identification type entity

Entity name: mshr\_hcmidentificationtypeentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/hcmidentificationtypeentities
```

**Response**

```JSON
{
    "mshr_description": "Alien/Admission no.",
    "mshr_identificationtypeid": "Alien/Admission",
    "mshr_checkduplicates": 200000000,
    "mshr_allowedvalues": 200000000,
    "mshr_identificationnumberformat": "",
    "mshr_fixedlength": 0,
}
```
