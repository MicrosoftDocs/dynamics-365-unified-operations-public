---
# required metadata

title: HCM employment V2 entity
description: This article provides details and an example query for the HCM employment V2 entity in Microsoft Dynamics 365 Human Resources.
author: avanish2821
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

# HCM employment V2 entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM employment V2 entity for Dynamics 365 Human Resources.

Physical name: mshr\_hcmemploymentv2entities

## Description

This entity provides information about the employment details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| mshr\_Dimension | Dimension | Int64 | Read-only |
| mshr\_DimensionDisplayValue | DimensionDisplayValue | String | Read-only |
| mshr\_RegulatoryEstablishment | RegulatoryEstablishment | Int64 | Read-only |
| mshr\_RegulatoryEstablishmentId | RegulatoryEstablishmentId | String | Read-only |
| mshr\_WorkerType | WorkerType | Enum | Read-only |
| mshr\_LegalEntity | LegalEntity | Int64 | Read-only |
| mshr\_LegalEntityId | LegalEntityId | String | Read-only |
| mshr\_EmploymentStartDate | EmploymentStartDate | Date time offset | Read-only |
| mshr\_EmploymentEndDate | EmploymentEndDate | Date time offset | Read-only |
| mshr\_Worker | Worker | Int64 | Read-only |
| mshr\_PersonnelNumber | PersonnelNumber | String | Read-only |
| mshr\_EmploymentId | EmploymentId | String | Read-only |

## Example query for the HCM employment V2 entity

Entity name: mshr\_hcmemploymentv2entities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/hcmemploymentv2entities
```

**Response**

```JSON
{
    "mshr_dimensiondisplayvalue": "--026",
    "mshr_regulatoryestablishmentid": "Seattle",
    "mshr_workertype": 200000000,
    "mshr_legalentityid": "USMF",
    "mshr_employmentstartdate": "2006-02-01T08:00:00Z",
    "mshr_employmentenddate": "2154-12-31T23:59:59Z",
    "mshr_personnelnumber": "000001",
    "mshr_employmentid": "000006201",
}
```
