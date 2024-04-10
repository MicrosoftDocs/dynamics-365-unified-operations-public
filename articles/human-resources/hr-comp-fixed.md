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

# Compensation fixed plan table 

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.


This article describes the (PayIntV1HcmEmploymentEmployeeEntity) entity for Dynamics 365 Human Resources.

## Description

This entity provides information about the employee employment.

## Properties
| Property|Physical name|Type | Use | Description |
| --- | --- | --- |
| ControlPoint|mserp_ControlPoint |String | Read-only | Reference point setups. |
| Currency|mserp_Currency |String | Read-only | Currency details. |
| Description|mserp_Description| String | Read-only | Description of the fixed compensation plans. |
| EnableRecommendation| mserp_RecommendationAllowed| Enum | Read-only | Recommendations allowed or not. |
| GridId | mserp_CompensationStructure| String | Read-only | Compensation grid value. |
| HireRule|mserp_HireRule | Enum | Read-only | Hire rule set. |
| MarketPriceIndicator|mserp_MarketPriceIndicator |Enum | Read-only | Market price indicator set. |
| PayFrequencyId| mserp_PayFrequency | String | Read-only | Pay rate conversion details. |
| PlanId | mserp_Plan |String | Read-only | Name of the compensation plan. |
| Tolerance|  mserp_OutOfRangeTolerance| Enum | Read-only | Out of range tolerance details. |
| Type| mserp_Type |Enum | Read-only | Type details. |
| ValidTo| mserp_ ExpirationDate |Date time offset | Read-only | Expiration date of the Compensation plan. |
| ValidFrom|  mserp_EffectiveDate| Date time offset | Read-only | Effective date of the Compensation plan. |
| RefPointSetupId| mserp_RefPointSetupId| String | Read-only | Reference point setup id. |



## Example query for Employment employee detail entity

**Request**

Entity name: *mserp_payintv1hcmemploymentemployeeentities*

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
