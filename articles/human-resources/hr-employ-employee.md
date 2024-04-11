---
# required metadata

title: Employment employee entity
description: This article provides details and an example query for the Employment employee entity in Microsoft Dynamics 365 Human Resources.
author: jcart
ms.date: 04/10/2024
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
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Employment employee entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

## Description

This entity provides information about employee employment.

## Properties

| Property | Physical name | Type | Use | Description |
|---|---|---|---|---|
| ProbationPeriod | mserp\_ProbationPeriod | Date time offset | Read-only | Details of the probation period.|
| ValidFrom | mserp\_ValidFrom | Date time offset | Read-only | The first date that employment is valid. |
| ValidTo | mserp\_ValidTo | Date time offset | Read-only | The last date that employment is valid. |
| EmploymentStartDate | mserp\_EmploymentStartDate | Date time offset | Read-only | The start date of employment. |
| EmploymentEndDate | mserp\_EmploymentEndDate | Date time offset | Read-only | The end date of employment. |
| LegalEntityId | mserp\_LegalEntityId | String | Read-only | Details of the assigned legal entity. |
| PersonnelNumber | mserp\_PersonnelNumber | String | Read-only | The personnel number of the worker. |

## Example query for Employment employee entity

**Request**

Entity name: mserp\_payintv1hcmemploymentemployeeentities

```http
GET [Organizaton URI]/api/data/v9.1/mserp_payintv1hcmemploymentemployeeentities_
```

**Response**

```json
{
    "mserp_probationperiod": "2017-11-19T08:00:00Z",
    "mserp_validfrom": "2012-09-28T17:11:47Z",
    "mserp_validto": "2154-12-31T23:59:59Z",
    "mserp_employmentstartdate": "2011-11-19T08:00:00Z",
    "mserp_employmentenddate": "2154-12-31T23:59:59Z",
    "mserp_legalentityid": "USRT",
    "mserp_personnelnumber": "000171",
}
```
