---
# required metadata

title: HCM job compensation entities
description: This article provides details and an example query for the HCM job compensation entities in Microsoft Dynamics 365 Human Resources.
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

# HCM job compensation entities

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM job compensation entities (payintv1hcmjobcompensationentities) for Dynamics 365 Human Resources.

Physical name: mserp\_payintv1hcmjobcompensationentities

## Description

These entities provide information about the job compensation details.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| mserp\_Job | Job | Int64 | Read-only |
| mserp\_CompensationLevel | CompensationLevel | Int64 | Read-only |
| mserp\_MarketControlPay | MarketControlPay | Real | Read-only |
| mserp\_MarketMaximumPay | MarketMaximumPay | Real | Read-only |
| mserp\_MarketMinimumPay | MarketMinimumPay | Real | Read-only |
| mserp\_MarketSource | MarketSource | String | Read-only |
| mserp\_SurveyCompany | SurveyCompany | Int64 | Read-only |
| mserp\_ExternalSurveyCode | ExternalSurveyCode | String | Read-only |
| mserp\_JobId | JobId | String | Read-only |
| mserp\_CompensationLevelId | CompensationLevelId | String | Read-only |
| mserp\_SurveyCompanyId | SurveyCompanyId | String | Read-only |

## Example query for the HCM job compensation entities

Entity name: mserp\_payintv1hcmjobcompensationentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/payintv1hcmjobcompensationentities
```

**Response**

```JSON
{
    "mserp_marketcontrolpay": 160000,
    "mserp_marketmaximumpay": 240000,
    "mserp_marketminimumpay": 100000,
    "mserp_marketsource": "Market One",
    "mserp_externalsurveycode": "VP Operations",
    "mserp_jobid": "VP of Operations",
    "mserp_compensationlevelid": "B2",
    "mserp_surveycompanyid": "National1",
    "mserp_primaryfield": "VP of Operations | B2",
}
```
