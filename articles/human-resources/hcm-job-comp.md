---
# required metadata

title: HCM job compensation entities
description: This article provides details and an example query for the HCM job compensation entities in Microsoft Dynamics 365 Human Resources.
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

# HCM job compensation entities

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM job compensation entities for Dynamics 365 Human Resources.

Physical name: mshr\_hcmjobcompensationentities

## Description

These entities provide information about the job compensation details.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| mshr\_Job | Job | Int64 | Read-only |
| mshr\_CompensationLevel | CompensationLevel | Int64 | Read-only |
| mshr\_MarketControlPay | MarketControlPay | Real | Read-only |
| mshr\_MarketMaximumPay | MarketMaximumPay | Real | Read-only |
| mshr\_MarketMinimumPay | MarketMinimumPay | Real | Read-only |
| mshr\_MarketSource | MarketSource | String | Read-only |
| mshr\_SurveyCompany | SurveyCompany | Int64 | Read-only |
| mshr\_ExternalSurveyCode | ExternalSurveyCode | String | Read-only |
| mshr\_JobId | JobId | String | Read-only |
| mshr\_CompensationLevelId | CompensationLevelId | String | Read-only |
| mshr\_SurveyCompanyId | SurveyCompanyId | String | Read-only |

## Example query for the HCM job compensation entities

Entity name: mshr\_hcmjobcompensationentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/hcmjobcompensationentities
```

**Response**

```JSON
{
    "mshr_marketcontrolpay": 160000,
    "mshr_marketmaximumpay": 240000,
    "mshr_marketminimumpay": 100000,
    "mshr_marketsource": "Market One",
    "mshr_externalsurveycode": "VP Operations",
    "mshr_jobid": "VP of Operations",
    "mshr_compensationlevelid": "B2",
    "mshr_surveycompanyid": "National1",
    "mshr_primaryfield": "VP of Operations | B2",
}
```
