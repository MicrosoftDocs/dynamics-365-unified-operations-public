---
# required metadata

title: Person Details entity
description: This article provides details and an example query for the Hcm Person Details entity in Microsoft Dynamics 365 Human Resources.
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

# Person Details entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Person Details entity (PayIntV1HcmPersonDetailsEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about person details.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Isdisabledveteran | mserp_isdisabledveteran | Enum | Read-only |
| Militaryserviceenddate | mserp_militaryserviceenddate | Date time offset | Read-only |
| Isexpatriaterulingapplicable | mserp_isexpatriaterulingapplicable | Enum | Read-only |
| Partynumber | mserp_partynumber | String | Read-only |
| Numberofdependents | mserp_numberofdependents | Enum | Read-only |
| Validto | mserp_validto | Date time offset | Read-only |
| Expatriaterulingvalidfrom | mserp_expatriaterulingvalidfrom | Date time offset | Read-only |
| Expatriaterulingvalidto | mserp_expatriaterulingvalidto | Date time offset | Read-only |
| Militaryservicestartdate | mserp_militaryservicestartdate | Date time offset | Read-only |
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Benefitmaritalstatusdate | mserp_benefitmaritalstatusdate | Date time offset | Read-only |
| Maritalstatus | mserp_maritalstatus | Enum | Read-only |
| Veteranstatusid | mserp_veteranstatusid | String | Read-only |

## Example query for PayIntV1HcmPersonDetailsEntity

Entity name: mserp_payintv1hcmpersondetailsentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmpersondetailsentities
```

**Response**

```JSON
{  
    "mserp_isexpatriaterulingapplicable": 200000000,
    "mserp_veteranstatusid": "",
    "mserp_militaryservicestartdate": "2012-09-11T20:09:56Z",
    "mserp_expatriaterulingvalidto": "2012-09-11T20:09:56Z",
    "mserp_militaryserviceenddate": "2012-09-11T20:09:56Z",
    "mserp_benefitmaritalstatusdate": "2012-09-11T20:09:56Z",
    "mserp_numberofdependents": 2,
    "mserp_isdisabledveteran": 200000000,
    "mserp_partynumber": "000000032",
    "mserp_validfrom": "2012-09-11T20:09:56Z",
    "mserp_validto": "2154-12-31T23:59:59Z",
    "mserp_expatriaterulingvalidfrom": "2012-09-11T20:09:56Z",
    "mserp_maritalstatus": 200000001
}
```
