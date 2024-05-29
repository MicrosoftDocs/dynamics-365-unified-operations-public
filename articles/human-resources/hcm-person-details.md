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

This article describes the Job type entity (payintv1hcmpersondetailsentities) for Dynamics 365 Human Resources.

Physical name: mserp_payintv1hcmpersondetailsentities

## Description

This entity provides information about the person details.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| mserp_IsDisabledVeteran IsDisabledVeteran | Enum | Read-only |
| mserp_ExpatriateRulingValidTo ExpatriateRulingValidTo | Date time offset | Read-only |
| mserp_ExpatriateRulingValidFrom ExpatriateRulingValidFrom | Date time offset | Read-only |
| mserp_IsExpatriateRulingApplicable IsExpatriateRulingApplicable | Enum | Read-only |
| mserp_MaritalStatus | MaritalStatus | Enum | Read-only |
| mserp_MilitaryServiceEndDate MilitaryServiceEndDate | Date time offset | Read-only |
| mserp_MilitaryServiceStartDate MilitaryServiceStartDate | Date time offset | Read-only |
| mserp_NumberOfDependents NumberOfDependents | Int | Read-only |
| mserp_Person | Person | Int64 | Read-only |
| mserp_PartyNumber | PartyNumber | String | Read-only |
| mserp_ValidFrom | ValidFrom | Date time offset | Read-only |
| mserp_ValidTo | ValidTo | Date time offset | Read-only |
| mserp_VeteranStatus | VeteranStatus | Int64 | Read-only |
| mserp_VeteranStatusId VeteranStatusId | Read-only |


## Example query for HCM person details entity

_Entity Name: mserp_payintv1hcmpersondetailsentities_

**Request**

```HTTP

GET \[Organizaton URI\]/api/data/v9.1/payintv1hcmpersondetailsentities
```

**Response**

```JSONCopy

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
