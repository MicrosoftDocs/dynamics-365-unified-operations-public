---
# required metadata

title: Historical person name entity
description: This article provides details and an example query for the Historical person name entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 04/04/2024
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

# Historical person name entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Person name history entity for Dynamics 365 Human Resources.

## Description

This entity provides information about the person name history.

## Properties

| Property | Physical name | Type | Use | Description |
|---|---|---|---|---|
| FirstName | mshr\_FirstName | String | Read-only | The first name of the person. |
| LastNamePrefix | mshr\_LastNamePrefix | String | Read-only | The last name prefix of the person. |
| LastName | mshr\_LastName | String | Read-only | The last name of the person. | 
| MiddleName | mshr\_MiddleName | String | Read-only | The middle name of the person. |
| ValidFrom | mshr\_ValidFrom | Date time offset | Read-only | The first date that the person's name is valid. |
| ValidTo | mshr\_ValidTo | Date time offset | Read-only | The last date that the person's name is valid. |
| PartyNumber | mshr\_PartyNumber | String | Read-only | The unique identifier of the party. |

## Example query for PayIntV1DirPersonNameHistoricalEntity

**Request**

Entity name: mshr\_dirpersonnamehistoricalentities

```http 
GET [Organization URI]/api/data/v9.1/mshr_dirpersonnamehistoricalentities
```

**Response**

```json
{
    "mshr_firstname": "Jodi",
    "mshr_lastnameprefix": "",
    "mshr_lastname": "Christiansen",
    "mshr_middlename": "",
    "mshr_validto": "2154-12-31T23:59:59Z",
    "mshr_partynumber": "000000032",
    "mshr_validfrom": null
}
```
