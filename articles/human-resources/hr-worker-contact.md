---
# required metadata

title: Worker contact entity
description: This article provides details and an example query for the Worker contact entity in Microsoft Dynamics 365 Human Resources.
author: jcart
ms.date: 04/24/2024
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
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Worker contact entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Worker contact entity (PayIntV1WorkerContactEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the worker contact.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| PersonnelNumber | mserp\_PersonnelNumber | String | Read-only |
| Type | mserp\_Type | Enum | Read-only |
| Locator | mserp\_Locator | String | Read-only |
| Description | mserp\_Description | String | Read-only |
| Purpose | mserp\_Purpose | String | Read-only |
| LocatorExtension | mserp\_LocatorExtension | String | Read-only |
| CountryRegionCode | mserp\_CountryRegionCode | String | Read-only |
| IsPrimary | mserp\_IsPrimary | Enum | Read-only |
| IsMobilePhone | mserp\_IsMobilePhone | Enum | Read-only |
| IsPrivate | mserp\_IsPrivate | Enum | Read-only |
| LocationId | mserp\_LocationId |String | Read-only |
| PartyNumber | mserp\_PartyNumber | String | Read-only |

## Example query for PayIntV1WorkerContactEntity

Entity name: mserp\_payintv1workercontactentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1workercontactentities_
```

**Response**

```JSON
{  
    "mserp_personnelnumber": "000001",  
    "mserp_type": 200000002,  
    "mserp_locator": "<jodi@contoso.com>",  
    "mserp_description": "Work",  
    "mserp_purpose": "Home",  
    "mserp_locatorextension": "",  
    "mserp_countryregioncode": "",  
    "mserp_isprimary": 200000001,  
    "mserp_ismobilephone": 200000000,  
    "mserp_isprivate": 200000000,  
    "mserp_locationid": "000000042",  
    "mserp_partynumber": "000000032",  
    "mserp_primaryfield": "000001 | Email address | <jodi@contoso.com> | Work",  
}
```
