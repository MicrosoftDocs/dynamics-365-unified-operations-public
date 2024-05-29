---
# required metadata

title: HCM job compensation entities
description: This article provides details and an example query for the HCM Job Compensation entities in Microsoft Dynamics 365 Human Resources.
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

Physical name: mserp_payintv1hcmjobcompensationentities

## Description

This entity provides information about the job compensation details.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| mserp_Job | Job | Int64 |Read-only |
| mserp_CompensationLevel CompensationLevel | Int64 |Read-only |
| mserp_MarketControlPay MarketControlPay | Real |Read-only |
| mserp_MarketMaximumPay MarketMaximumPay | Real |Read-only |
| mserp_MarketMinimumPay MarketMinimumPay | Real |Read-only |
| mserp_MarketSource | MarketSource | String |Read-only |
| mserp_SurveyCompany | SurveyCompany | Int64 |Read-only |
| mserp_ExternalSurveyCode ExternalSurveyCode | String |Read-only |
| mserp_JobId | JobId | String |Read-only |
| mserp_CompensationLevelId CompensationLevelId | String |Read-only |
| mserp_SurveyCompanyId SurveyCompanyId | String |Read-only |


## Example query for HCM identification type entity

Entity Name: mserp_payintv1hcmjobcompensationentities

**Request**

```HTTPCopy

GET \[Organizaton URI\]/api/data/v9.1/payintv1hcmjobcompensationentities
```

**Response**

```JSONCopy

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
