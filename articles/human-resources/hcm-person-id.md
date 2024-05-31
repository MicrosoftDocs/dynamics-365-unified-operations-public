---
# required metadata

title: HCM person identification entities
description: This article provides details and an example query for the HCM person identification entities in Microsoft Dynamics 365 Human Resources.
author: jcart
ms.date: 05/24/2024
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

# HCM person identification entities

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM person identification entities (payintv1hcmpersonidentificationnumberentities) for Dynamics 365 Human Resources.

Physical name: mserp\_payintv1hcmpersonidentificationnumberentities

## Description

These entities provide information about the person identification details.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| mserp\_EntryType | EntryType | String | Read-only |
| mserp\_Description | Description | String | Read-only |
| mserp\_ExpirationDate | ExpirationDate | Date time offset | Read-only |
| mserp\_IdentificationType | IdentificationType | Int64 | Read-only |
| mserp\_IsPrimary | IsPrimary | Enum | Read-only |
| mserp\_IssuedDate | IssuedDate | Date time offset | Read-only |
| mserp\_IssuingAgency | IssuingAgency | Int64 | Read-only |
| mserp\_Person | Person | Int64 | Read-only |
| mserp\_IdentificationNumber | IdentificationNumber | String | Read-only |
| mserp\_PartyNumber | PartyNumber | String | Read-only |
| mserp\_IdentificationTypeId | IdentificationTypeId | String | Read-only |
| mserp\_IssuingAgencyId | IssuingAgencyId | String | Read-only |

## Example query for the HCM person identification entities

Entity name: mserp\_payintv1hcmpersonidentificationnumberentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/payintv1hcmpersonidentificationnumberentities
```

**Response**

```JSON
{
    "mserp_entrytype": "",
    "mserp_description": "SSN",
    "mserp_isprimary": 200000000,
    "mserp_identificationnumber": "999-99-9999",
    "mserp_partynumber": "000000780",
    "mserp_identificationtypeid": "SSN",
    "mserp_issuingagencyid": "Government",
    "mserp_primaryfield": "000000780 | SSN | 999-99-9999",
    "mserp_expirationdate": null,
    "mserp_issueddate": null
}
```
