---
# required metadata

title: HCM person details entities
description: This article provides details and an example query for the HCM person details entities in Microsoft Dynamics 365 Human Resources.
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

# HCM person details entities

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM person details entities (payintv1hcmpersondetailsentities) for Dynamics 365 Human Resources.

Physical name: mserp\_payintv1hcmpersondetailsentities

## Description

These entities provide information about the person details.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| mserp\_IsDisabledVeteran | IsDisabledVeteran | Enum | Read-only |
| mserp\_ExpatriateRulingValidTo | ExpatriateRulingValidTo | Date time offset | Read-only |
| mserp\_ExpatriateRulingValidFrom | ExpatriateRulingValidFrom | Date time offset | Read-only |
| mserp\_IsExpatriateRulingApplicable | IsExpatriateRulingApplicable | Enum | Read-only |
| mserp\_MaritalStatus | MaritalStatus | Enum | Read-only |
| mserp\_MilitaryServiceEndDate | MilitaryServiceEndDate | Date time offset | Read-only |
| mserp\_MilitaryServiceStartDate | MilitaryServiceStartDate | Date time offset | Read-only |
| mserp\_NumberOfDependents | NumberOfDependents | Int | Read-only |
| mserp\_Person | Person | Int64 | Read-only |
| mserp\_PartyNumber | PartyNumber | String | Read-only |
| mserp\_ValidFrom | ValidFrom | Date time offset | Read-only |
| mserp\_ValidTo | ValidTo | Date time offset | Read-only |
| mserp\_VeteranStatus | VeteranStatus | Int64 | Read-only |
| mserp\_VeteranStatusId | VeteranStatusId | | Read-only |

## Example query for the HCM person details entities

Entity name: mserp\_payintv1hcmpersondetailsentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/payintv1hcmpersondetailsentities
```

**Response**

```JSON
{
    "mserp_isdisabledveteran": 200000000,
    "mserp_isexpatriaterulingapplicable": 200000000,
    "mserp_maritalstatus": 200000001,
    "mserp_numberofdependents": 2,
    "mserp_partynumber": "000000032",
    "mserp_validfrom": "2012-09-11T20:09:56Z",
    "mserp_validto": "2154-12-31T23:59:59Z",
    "mserp_veteranstatusid": "",
    "mserp_militaryservicestartdate": null,
    "mserp_expatriaterulingvalidto": null,
    "mserp_militaryserviceenddate": null,
    "mserp_expatriaterulingvalidfrom": null
}
```
