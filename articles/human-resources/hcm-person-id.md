---
# required metadata

title: HCM person identification entities
description: This article provides details and an example query for the HCM person identification entities in Microsoft Dynamics 365 Human Resources.
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

# HCM person identification entities

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM person identification entities for Dynamics 365 Human Resources.

Physical name: mshr\_hcmpersonidentificationnumberentities

## Description

These entities provide information about the person identification details.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| mshr\_EntryType | EntryType | String | Read-only |
| mshr\_Description | Description | String | Read-only |
| mshr\_ExpirationDate | ExpirationDate | Date time offset | Read-only |
| mshr\_IdentificationType | IdentificationType | Int64 | Read-only |
| mshr\_IsPrimary | IsPrimary | Enum | Read-only |
| mshr\_IssuedDate | IssuedDate | Date time offset | Read-only |
| mshr\_IssuingAgency | IssuingAgency | Int64 | Read-only |
| mshr\_Person | Person | Int64 | Read-only |
| mshr\_IdentificationNumber | IdentificationNumber | String | Read-only |
| mshr\_PartyNumber | PartyNumber | String | Read-only |
| mshr\_IdentificationTypeId | IdentificationTypeId | String | Read-only |
| mshr\_IssuingAgencyId | IssuingAgencyId | String | Read-only |

## Example query for the HCM person identification entities

Entity name: mshr\_hcmpersonidentificationnumberentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/hcmpersonidentificationnumberentities
```

**Response**

```JSON
{
    "mshr_entrytype": "",
    "mshr_description": "SSN",
    "mshr_isprimary": 200000000,
    "mshr_identificationnumber": "999-99-9999",
    "mshr_partynumber": "000000780",
    "mshr_identificationtypeid": "SSN",
    "mshr_issuingagencyid": "Government",
    "mshr_primaryfield": "000000780 | SSN | 999-99-9999",
    "mshr_expirationdate": null,
    "mshr_issueddate": null
}
```
