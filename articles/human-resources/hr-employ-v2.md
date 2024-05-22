---
# required metadata

title: HCM employment V2 entity
description: This article provides details and an example query for the HCM employment V2 entity in Microsoft Dynamics 365 Human Resources.
author: jcart
ms.date: 05/22/2024
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

# HCM employment V2 entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Job type entity (payintv1hcmemploymentv2entities) for Dynamics 365 Human Resources.

Physical name: mserp_payintv1hcmemploymentv2entities

## Description

This entity provides information about the employment details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| mserp_Dimension|Dimension|Int64 | Read-only |
| mserp_DimensionDisplayValue DimensionDisplayValue|String | Read-only |
| mserp_RegulatoryEstablishment RegulatoryEstablishment|Int64 | Read-only |
| mserp_RegulatoryEstablishmentId RegulatoryEstablishmentId|String | Read-only |
| mserp_WorkerType|WorkerType|Enum | Read-only |
| mserp_LegalEntity|LegalEntity|Int64 | Read-only |
| mserp_LegalEntityId|LegalEntityId|String | Read-only |
| mserp_EmploymentStartDate EmploymentStartDate|Date time offset | Read-only |
| mserp_EmploymentEndDate EmploymentEndDate|Date time offset | Read-only |
| mserp_Worker|Worker|Int64 | Read-only |
| mserp_PersonnelNumber PersonnelNumber|String | Read-only |
| mserp_EmploymentId|EmploymentId|String | Read-only |

## Example query for HCM position detail entity

Entity Name: mserp_payintv1hcmemploymentv2entities

**Request**

```HTTPCopy
GET \[Organizaton URI\]/api/data/v9.1/payintv1hcmemploymentv2entities
```

**Response**

```JSONCopy
{
"mserp_dimensiondisplayvalue": "--026",
"mserp_regulatoryestablishmentid": "Seattle",
"mserp_workertype": 200000000,
"mserp_legalentityid": "USMF",
"mserp_employmentstartdate": "2006-02-01T08:00:00Z",
"mserp_employmentenddate": "2154-12-31T23:59:59Z",
"mserp_personnelnumber": "000001",
"mserp_employmentid": "000006201",
}
```

