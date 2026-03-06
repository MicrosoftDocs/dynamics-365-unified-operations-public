---
# required metadata

title: Employment Employee entity
description: This article provides details and an example query for the Hcm Employment Employee entity in Microsoft Dynamics 365 Human Resources.
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

# Employment Employee entity

> [!NOTE]
> The functionality that is noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Employment Employee entity (PayIntV1HcmEmploymentEmployeeEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about employment of the employee.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Probationperiod | mserp_probationperiod | Date time offset | Read-only |
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Validto | mserp_validto | Date time offset | Read-only |
| Employmentstartdate | mserp_employmentstartdate | Date time offset | Read-only |
| Employmentenddate | mserp_employmentenddate | Date time offset | Read-only |
| LegalEntityId | mserp_legalentityid | String | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |

## Example query for PayIntV1HcmEmploymentEmployeeEntity

Entity name: mserp_payintv1hcmemploymentemployeeentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmemploymentemployeeentities
```

**Response**

```JSON
{  
    "mserp_probationperiod": "2024-01-01T00:00:00Z",
    "mserp_validfrom": "2024-01-01T00:00:00Z",
    "mserp_validto": "2024-01-01T00:00:00Z",
    "mserp_employmentstartdate": "2024-01-01T00:00:00Z",
    "mserp_employmentenddate": "2024-01-01T00:00:00Z",
    "mserp_legalentityid" : "USMF",
    "mserp_personnelnumber": "000171"
}
```
