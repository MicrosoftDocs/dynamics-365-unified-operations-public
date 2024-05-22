---
# required metadata

title: Hcm compensation fixed plan table entity
description: This article provides details and an example query for the Hcm compensation fixed plan table entity in Microsoft Dynamics 365 Human Resources.
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

# Hcm compensation fixed plan table entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Job type entity (payintv1hcmcompfixedplantableentities) for Dynamics 365 Human Resources.

Physical name: mserp_payintv1hcmcompfixedplantableentities

## Description 

This entity provides information about the compensation fixed plan details.

## Properties

| Physical name|Property|Type | Use |
|---|---|---|---|
| mserp_ControlPoint|ControlPoint|String | Read-only|
| mserp_Currency|Currency|String | Read-only|
| mserp_Description|Description|String | Read-only|
| mserp_RecommendationAllowed RecommendationAllowed|Enum | Read-only|
| mserp_CompensationStructure|CompensationStructure|String | Read-only|
| mserp_HireRule|HireRule|Enum | Read-only|
| mserp_MarketPriceIndicator MarketPriceIndicator|Enum | Read-only|
| mserp_PayFrequency|PayFrequency|String | Read-only|
| mserp_Plan|Plan|String | Read-only|
| mserp_OutOfRangeTolerance|OutOfRangeTolerance|Enum | Read-only|
| mserp_Type|Type|Enum | Read-only|
| mserp_EffectiveDate|EffectiveDate|Date time offset | Read-only|
| mserp_ExpirationDate|ExpirationDate|Date time offset | Read-only|
| mserp_RefPointSetupId|Type|String | Read-only|


## Example query for HCM Fixed compensation employee entity**

Entity Name: mserp_payintv1hcmcompfixedplantableentities

**Request**

```HTTPCopy
GET \[Organizaton URI\]/api/data/v9.1/payintv1hcmcompfixedplantableentities
```

**Response**

```JSONCopy

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


