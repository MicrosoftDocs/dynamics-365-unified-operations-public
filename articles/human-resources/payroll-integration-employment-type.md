---
# required metadata

title: Employment Type entity
description: This article provides details and an example query for the Hcm Employment Type entity in Microsoft Dynamics 365 Human Resources.
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

# Employment Type entity

> [!NOTE]
> The functionality that is noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Employment Type entity (PayIntV1HcmEmploymentTypeEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the employment types available.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Employmenttypeid | mserp_employmenttypeid | String | Read-only |
| Description | mserp_description | String | Read-only |

## Example query for PayIntV1HcmEmploymentTypeEntity

Entity name: mserp_payintv1hcmemploymenttypeentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmemploymenttypeentities
```

**Response**

```JSON
{  
    "mserp_employmenttypeid": "Salary",
    "mserp_description": "Salaried employees"
}
```
