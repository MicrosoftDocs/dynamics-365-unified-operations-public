---
# required metadata

title: HCM person details entities
description: This article provides details and an example query for the HCM person details entities in Microsoft Dynamics 365 Human Resources.
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

# HCM person details entities

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM person details entities for Dynamics 365 Human Resources.

Physical name: mshr\_hcmpersondetailsentities

## Description

These entities provide information about the person details.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| mshr\_IsDisabledVeteran | IsDisabledVeteran | Enum | Read-only |
| mshr\_ExpatriateRulingValidTo | ExpatriateRulingValidTo | Date time offset | Read-only |
| mshr\_ExpatriateRulingValidFrom | ExpatriateRulingValidFrom | Date time offset | Read-only |
| mshr\_IsExpatriateRulingApplicable | IsExpatriateRulingApplicable | Enum | Read-only |
| mshr\_MaritalStatus | MaritalStatus | Enum | Read-only |
| mshr\_MilitaryServiceEndDate | MilitaryServiceEndDate | Date time offset | Read-only |
| mshr\_MilitaryServiceStartDate | MilitaryServiceStartDate | Date time offset | Read-only |
| mshr\_NumberOfDependents | NumberOfDependents | Int | Read-only |
| mshr\_Person | Person | Int64 | Read-only |
| mshr\_PartyNumber | PartyNumber | String | Read-only |
| mshr\_ValidFrom | ValidFrom | Date time offset | Read-only |
| mshr\_ValidTo | ValidTo | Date time offset | Read-only |
| mshr\_VeteranStatus | VeteranStatus | Int64 | Read-only |
| mshr\_VeteranStatusId | VeteranStatusId | | Read-only |

## Example query for the HCM person details entities

Entity name: mshr\_hcmpersondetailsentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/hcmpersondetailsentities
```

**Response**

```JSON
{
    "mshr_isdisabledveteran": 200000000,
    "mshr_isexpatriaterulingapplicable": 200000000,
    "mshr_maritalstatus": 200000001,
    "mshr_numberofdependents": 2,
    "mshr_partynumber": "000000032",
    "mshr_validfrom": "2012-09-11T20:09:56Z",
    "mshr_validto": "2154-12-31T23:59:59Z",
    "mshr_veteranstatusid": "",
    "mshr_militaryservicestartdate": null,
    "mshr_expatriaterulingvalidto": null,
    "mshr_militaryserviceenddate": null,
    "mshr_expatriaterulingvalidfrom": null
}
```
