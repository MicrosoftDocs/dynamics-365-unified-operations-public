---
# required metadata

title: Identification Type entity
description: This article provides details and an example query for the Hcm Identification Type entity in Microsoft Dynamics 365 Human Resources.
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

# Hcm Identification Type entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Identification Type entity (PayIntV1HcmIdentificationTypeEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about identification types.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Checkduplicates | mserp_checkduplicates | Enum | Read-only |
| Fixedlength | mserp_fixedlength | Int | Read-only |
| Allowedvalues | mserp_allowedvalues | Enum | Read-only |
| Identificationtypeid | mserp_identificationtypeid | String | Read-only |
| Identificationnumberformat | mserp_identificationnumberformat | String | Read-only |
| Description | mserp_description | String | Read-only |

## Example query for PayIntV1HcmIdentificationTypeEntity

Entity name: mserp_payintv1hcmidentificationtypeentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmidentificationtypeentities
```

**Response**

```JSON
{  
    "mserp_checkduplicates": 200000000,
    "mserp_fixedlength": 0,
    "mserp_allowedvalues": 200000000,
    "mserp_identificationtypeid": "Drivers license",
    "mserp_identificationnumberformat": "",
    "mserp_description": "Drivers license"
}
```
