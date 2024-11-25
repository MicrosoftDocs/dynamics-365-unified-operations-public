---
# required metadata

title: HCM compensation fixed plan table entity
description: This article provides details and an example query for the HCM compensation fixed plan table entity in Microsoft Dynamics 365 Human Resources.
author: jcart
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
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# HCM compensation fixed plan table entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the HCM compensation fixed plan table entity (payintv1hcmcompfixedplantableentities) for Dynamics 365 Human Resources.

Physical name: mserp\_payintv1hcmcompfixedplantableentities

## Description

This entity provides information about the compensation fixed plan details.

## Properties

| Physical name|Property|Type | Use |
|---|---|---|---|
| mserp\_ControlPoint | ControlPoint | String | Read-only |
| mserp\_Currency | Currency | String | Read-only |
| mserp\_Description | Description | String | Read-only |
| mserp\_RecommendationAllowed | RecommendationAllowed | Enum | Read-only |
| mserp\_CompensationStructure | CompensationStructure | String | Read-only |
| mserp\_HireRule | HireRule | Enum | Read-only |
| mserp\_MarketPriceIndicator | MarketPriceIndicator | Enum | Read-only |
| mserp\_PayFrequency | PayFrequency | String | Read-only |
| mserp\_Plan | Plan | String | Read-only |
| mserp\_OutOfRangeTolerance | OutOfRangeTolerance | Enum | Read-only |
| mserp\_Type | Type | Enum | Read-only |
| mserp\_EffectiveDate | EffectiveDate | Date time offset | Read-only |
| mserp\_ExpirationDate | ExpirationDate | Date time offset | Read-only |
| mserp\_RefPointSetupId | Type | String | Read-only |

## Example query for the HCM compensation fixed plan table entity

Entity name: mserp\_payintv1hcmcompfixedplantableentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/payintv1hcmcompfixedplantableentities
```

**Response**

```JSON
{
    "mserp_controlpoint": "",
    "mserp_currency": "USD",
    "mserp_description": "Executive Broad Band",
    "mserp_recommendationallowed": 200000000,
    "mserp_compensationstructure": "ExBand",
    "mserp_hirerule": 200000001,
    "mserp_marketpriceindicator": 200000000,
    "mserp_payfrequency": "Annual",
    "mserp_plan": "ExBand",
    "mserp_outofrangetolerance": 200000002,
    "mserp_type": 200000002,
    "mserp_effectivedate": "2005-01-01T00:00:00Z",
    "mserp_expirationdate": "2154-12-31T00:00:00Z",
    "mserp_refpointsetupid": "",
}
```
