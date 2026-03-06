---
# required metadata

title: Worker contact entity
description: This article provides details and an example query for the Worker contact entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
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
ms.author: twheeloc
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Worker contact entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Worker contact entity for Dynamics 365 Human Resources.

## Description

This entity provides information about the worker contact.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| PersonnelNumber | mshr\_PersonnelNumber | String | Read-only |
| Type | mshr\_Type | Enum | Read-only |
| Locator | mshr\_Locator | String | Read-only |
| Description | mshr\_Description | String | Read-only |
| Purpose | mshr\_Purpose | String | Read-only |
| LocatorExtension | mshr\_LocatorExtension | String | Read-only |
| CountryRegionCode | mshr\_CountryRegionCode | String | Read-only |
| IsPrimary | mshr\_IsPrimary | Enum | Read-only |
| IsMobilePhone | mshr\_IsMobilePhone | Enum | Read-only |
| IsPrivate | mshr\_IsPrivate | Enum | Read-only |
| LocationId | mshr\_LocationId |String | Read-only |
| PartyNumber | mshr\_PartyNumber | String | Read-only |

## Example query for PayIntV1WorkerContactEntity

Entity name: mshr\_workercontactentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mshr_workercontactentities_
```

**Response**

```JSON
{  
    "mshr_personnelnumber": "000001",  
    "mshr_type": 200000002,  
    "mshr_locator": "<jodi@contoso.com>",  
    "mshr_description": "Work",  
    "mshr_purpose": "Home",  
    "mshr_locatorextension": "",  
    "mshr_countryregioncode": "",  
    "mshr_isprimary": 200000001,  
    "mshr_ismobilephone": 200000000,  
    "mshr_isprivate": 200000000,  
    "mshr_locationid": "000000042",  
    "mshr_partynumber": "000000032",  
    "mshr_primaryfield": "000001 | Email address | <jodi@contoso.com> | Work",  
}
```
