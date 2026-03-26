---
# required metadata

title: HCM compensation fixed plan table entity
description: This article provides details and an example query for the HCM compensation fixed plan table entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 05/22/2024
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

# HCM compensation fixed plan table entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM compensation fixed plan table entity for Dynamics 365 Human Resources.

Physical name: mshr\_hcmcompfixedplantableentities

## Description

This entity provides information about the compensation fixed plan details.

## Properties

| Physical name|Property|Type | Use |
|---|---|---|---|
| mshr\_ControlPoint | ControlPoint | String | Read-only |
| mshr\_Currency | Currency | String | Read-only |
| mshr\_Description | Description | String | Read-only |
| mshr\_RecommendationAllowed | RecommendationAllowed | Enum | Read-only |
| mshr\_CompensationStructure | CompensationStructure | String | Read-only |
| mshr\_HireRule | HireRule | Enum | Read-only |
| mshr\_MarketPriceIndicator | MarketPriceIndicator | Enum | Read-only |
| mshr\_PayFrequency | PayFrequency | String | Read-only |
| mshr\_Plan | Plan | String | Read-only |
| mshr\_OutOfRangeTolerance | OutOfRangeTolerance | Enum | Read-only |
| mshr\_Type | Type | Enum | Read-only |
| mshr\_EffectiveDate | EffectiveDate | Date time offset | Read-only |
| mshr\_ExpirationDate | ExpirationDate | Date time offset | Read-only |
| mshr\_RefPointSetupId | Type | String | Read-only |

## Example query for the HCM compensation fixed plan table entity

Entity name: mshr\_hcmcompfixedplantableentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/hcmcompfixedplantableentities
```

**Response**

```JSON
{
    "mshr_controlpoint": "",
    "mshr_currency": "USD",
    "mshr_description": "Executive Broad Band",
    "mshr_recommendationallowed": 200000000,
    "mshr_compensationstructure": "ExBand",
    "mshr_hirerule": 200000001,
    "mshr_marketpriceindicator": 200000000,
    "mshr_payfrequency": "Annual",
    "mshr_plan": "ExBand",
    "mshr_outofrangetolerance": 200000002,
    "mshr_type": 200000002,
    "mshr_effectivedate": "2005-01-01T00:00:00Z",
    "mshr_expirationdate": "2154-12-31T00:00:00Z",
    "mshr_refpointsetupid": "",
}
```
