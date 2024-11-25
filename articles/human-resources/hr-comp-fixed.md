---
# required metadata

title: Compensation fixed plan table entity
description: This article provides details and an example query for the Compensation fixed plan table entity in Microsoft Dynamics 365 Human Resources.
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

# Compensation fixed plan table entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the PayIntV1HcmEmploymentEmployeeEntity entity for Dynamics 365 Human Resources.

## Description

This entity provides information about employee employment.

## Properties

| Property | Physical name | Type | Use | Description |
|---|---|---|---|---|
| ControlPoint | mserp\_ControlPoint | String | Read-only | Reference point setups. |
| Currency | mserp\_Currency | String | Read-only | Currency details. |
| Description | mserp\_Description | String | Read-only | The description of the fixed compensation plans. |
| EnableRecommendation | mserp\_RecommendationAllowed | Enum | Read-only | A value that indicates whether recommendations are allowed. |
| GridId | mserp\_CompensationStructure | String | Read-only | The compensation grid value. |
| HireRule | mserp\_HireRule | Enum | Read-only | The hire rule set. |
| MarketPriceIndicator | mserp\_MarketPriceIndicator | Enum | Read-only | The market price indicator set. |
| PayFrequencyId | mserp\_PayFrequency | String | Read-only | Pay rate conversion details. |
| PlanId | mserp\_Plan | String | Read-only | The name of the compensation plan. |
| Tolerance | mserp\_OutOfRangeTolerance | Enum | Read-only | Out-of-range tolerance details. |
| Type | mserp\_Type | Enum | Read-only | Type details. |
| ValidTo | mserp\_ExpirationDate | Date time offset | Read-only | The expiration date of the compensation plan. |
| ValidFrom | mserp\_EffectiveDate | Date time offset | Read-only | The effective date of the compensation plan. |
| RefPointSetupId | mserp\_RefPointSetupId | String | Read-only | The ID of the reference point setup. |

## Example query for the Employment employee detail entity

**Request**

Entity name: mserp\_payintv1hcmemploymentemployeeentities

```http
GET [OrganizatonURI]/api/data/v9.1/mserp_payintv1hcmemploymentemployeeentities_
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
