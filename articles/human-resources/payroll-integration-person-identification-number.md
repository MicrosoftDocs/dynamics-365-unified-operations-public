---
# required metadata

title: Person Identification Number entity
description: This article provides details and an example query for the Hcm Person Identification Number entity in Microsoft Dynamics 365 Human Resources.
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

# Person Identification Number entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Person Identification Number entity (PayIntV1HcmPersonIdentificationNumberEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the person identification numbers.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Issueddate | mserp_issueddate | Date time offset | Read-only |
| Identificationnumber | mserp_identificationnumber | String | Read-only |
| Description | mserp_description | String | Read-only |
| Issuingagencyid | mserp_issuingagencyid | String | Read-only |
| Entrytype | mserp_entrytype | String | Read-only |
| Expirationdate | mserp_expirationdate | Date time offset | Read-only |
| Partynumber | mserp_partynumber | String | Read-only |
| Isprimary | mserp_isprimary | Enum | Read-only |
| Identificationtypeid | mserp_identificationtypeid | String | Read-only |

## Example query for PayIntV1HcmPersonIdentificationNumberEntity

Entity name: mserp_payintv1hcmpersonidentificationnumberentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpersonidentificationnumberentities
```

**Response**

```JSON
{  
    "mserp_issueddate": "2024-01-01T00:00:00Z",
    "mserp_identificationnumber": "999-99-9999",
    "mserp_description": "US Passport",
    "mserp_issuingagencyid": "Government",
    "mserp_entrytype": "US Passport",
    "mserp_expirationdate": "2024-01-01T00:00:00Z",
    "mserp_partynumber": "000000068",
    "mserp_isprimary": 200000000,
    "mserp_identificationtypeid": "Passport"
}
```
