---
# required metadata

title: Compensation Fixed Plan Table entity
description: This article provides details and an example query for the Hcm Comp Fixed Plan Table entity in Microsoft Dynamics 365 Human Resources.
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

# Compensation Fixed Plan Table entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Comp Fixed Plan Table entity (PayIntV1HcmCompFixedPlanTableEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the compensation fixed plan table.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Payfrequency | mserp_payfrequency | String | Read-only |
| Controlpoint | mserp_controlpoint | String | Read-only |
| Refpointsetupid | mserp_refpointsetupid | String | Read-only |
| Recommendationallowed | mserp_recommendationallowed | Enum | Read-only |
| Compensationstructure | mserp_compensationstructure | String | Read-only |
| Hirerule | mserp_hirerule | Enum | Read-only |
| Outofrangetolerance | mserp_outofrangetolerance | Enum | Read-only |
| Dataareaid | mserp_dataareaid | String | Read-only |
| Plan | mserp_plan | String | Read-only |
| Expirationdate | mserp_expirationdate | Date time offset | Read-only |
| Marketpriceindicator | mserp_marketpriceindicator | Enum | Read-only |
| Description | mserp_description | String | Read-only |
| Effectivedate | mserp_effectivedate | Date time offset | Read-only |
| Currency | mserp_currency | String | Read-only |
| Type | mserp_type | Enum | Read-only |

## Example query for PayIntV1HcmCompFixedPlanTableEntity

Entity name: mserp_payintv1hcmcompfixedplantableentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmcompfixedplantableentities
```

**Response**

```JSON
{  
    "mserp_payfrequency": "Annual",
    "mserp_controlpoint": "Mid",
    "mserp_refpointsetupid": "Bands",
    "mserp_recommendationallowed": 200000001,
    "mserp_compensationstructure": "BandE",
    "mserp_hirerule": 200000001,
    "mserp_outofrangetolerance": 200000002,
    "mserp_dataareaid": "usmf",
    "mserp_plan": "BandE",
    "mserp_expirationdate": "2024-01-01T00:00:00Z",
    "mserp_marketpriceindicator": 200000000,
    "mserp_description": "Band East Region",
    "mserp_effectivedate": "2024-01-01T00:00:00Z",
    "mserp_currency": "USD",
    "mserp_type": 200000002
}
```
