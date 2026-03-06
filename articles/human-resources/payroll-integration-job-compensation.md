---
# required metadata

title: Job Compensation entity
description: This article provides details and an example query for the Hcm Job Compensation entity in Microsoft Dynamics 365 Human Resources.
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

# Job Compensation entity

> [!NOTE]
> The functionality that is noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Job Compensation entity (PayIntV1HcmJobCompensationEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about job compensation.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Marketmaximumpay | mserp_marketmaximumpay | Real | Read-only |
| Surveycompanyid | mserp_surveycompanyid | String | Read-only |
| Externalsurveycode | mserp_externalsurveycode | String | Read-only |
| Jobid | mserp_jobid | String | Read-only |
| Marketminimumpay | mserp_marketminimumpay | Real | Read-only |
| Marketsource | mserp_marketsource | String | Read-only |
| Marketcontrolpay | mserp_marketcontrolpay | Real | Read-only |
| Compensationlevelid | mserp_compensationlevelid | String | Read-only |

## Example query for PayIntV1HcmJobCompensationEntity

Entity name: mserp_payintv1hcmjobcompensationentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmjobcompensationentities
```

**Response**

```JSON
{  
    "mserp_marketmaximumpay": 240000,
    "mserp_surveycompanyid": "National1",
    "mserp_externalsurveycode": "VP Operations",
    "mserp_jobid": "VP of Operations",
    "mserp_marketminimumpay": 100000,
    "mserp_marketsource": "Market One",
    "mserp_marketcontrolpay": 160000,
    "mserp_compensationlevelid": "B2"
}
```
