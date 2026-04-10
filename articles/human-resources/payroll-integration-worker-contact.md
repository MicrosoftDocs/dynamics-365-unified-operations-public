---
# required metadata

title: Worker Contact entity
description: This article provides details and an example query for the Worker Contact entity in Microsoft Dynamics 365 Human Resources.
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

# Worker Contact entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Worker Contact entity (PayIntV1WorkerContactEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the worker contact.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Type | mserp_type | Enum | Read-only |
| Locator | mserp_locator | String | Read-only |
| Partynumber | mserp_partynumber | String | Read-only |
| Isprimary | mserp_isprimary | Enum | Read-only |
| Locatorextension | mserp_locatorextension | String | Read-only |
| Purpose | mserp_purpose | String | Read-only |
| Ismobilephone | mserp_ismobilephone | Enum | Read-only |
| Isprivate | mserp_isprivate | Enum | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Countryregioncode | mserp_countryregioncode | String | Read-only |
| Locationid | mserp_locationid | String | Read-only |
| Description | mserp_description | String | Read-only |

## Example query for PayIntV1WorkerContactEntity

Entity name: mserp_payintv1workercontactentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1workercontactentities
```

**Response**

```JSON
{  
    "mserp_type": 200000000,
    "mserp_locator": "jodi@contoso.com",
    "mserp_partynumber": "000000032",
    "mserp_isprimary": 200000000,
    "mserp_locatorextension": "",
    "mserp_purpose": "Home",
    "mserp_ismobilephone": 200000000,
    "mserp_isprivate": 200000000,
    "mserp_personnelnumber": "000023",
    "mserp_countryregioncode": "",
    "mserp_locationid": "000000042",
    "mserp_description": "Work"
}
```
