---
# required metadata

title: Employment V2 entity
description: This article provides details and an example query for the Hcm Employment V2 entity in Microsoft Dynamics 365 Human Resources.
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

# Employment V2 entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Employment V2 entity (PayIntV1HcmEmploymentV2Entity) for Dynamics 365 Human Resources.

## Description

This entity provides information about basic employment for an employee.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Calendarid | mserp_calendarid | String | Read-only |
| CalendarLegalEntityId | mserp_calendarlegalentityid | String | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Employmentid | mserp_employmentid | String | Read-only |
| Dimensiondisplayvalue | mserp_dimensiondisplayvalue | String | Read-only |
| Workertype | mserp_workertype | Enum | Read-only |
| LegalEntityId | mserp_legalentityid | String | Read-only |
| Employmentstartdate | mserp_employmentstartdate | Date time offset | Read-only |
| Regulatoryestablishmentid | mserp_regulatoryestablishmentid | String | Read-only |
| Employmentenddate | mserp_employmentenddate | Date time offset | Read-only |

## Example query for PayIntV1HcmEmploymentV2Entity

Entity name: mserp_payintv1hcmemploymentv2entities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmemploymentv2entities
```

**Response**

```JSON
{  
    "mserp_calendarid": "Standard",
    "mserp_calendarlegalentityid": "usmf",
    "mserp_personnelnumber": "000001",
    "mserp_employmentid": "000006201",
    "mserp_dimensiondisplayvalue": "--026",
    "mserp_workertype": 200000000,
    "mserp_legalentityid": "USMF",
    "mserp_employmentstartdate": "2024-01-01T00:00:00Z",
    "mserp_regulatoryestablishmentid": "Seattle",
    "mserp_employmentenddate": "2024-01-01T00:00:00Z"
}
```
