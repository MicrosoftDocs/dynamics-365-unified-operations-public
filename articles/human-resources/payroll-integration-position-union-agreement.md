---
# required metadata

title: Position Union Agreement entity
description: This article provides details and an example query for the Position Union Agreement entity in Microsoft Dynamics 365 Human Resources.
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

# Position Union Agreement entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Position Union Agreement entity (PayIntV1PositionUnionAgreementEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the position union agreement.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Positionid | mserp_positionid | String | Read-only |
| Laborunionid | mserp_laborunionid | String | Read-only |
| Validto | mserp_validto | Date time offset | Read-only |
| Validfrom | mserp_validfrom | Date time offset | Read-only |
| Unionagreementname | mserp_unionagreementname | String | Read-only |
| Legalentityid | mserp_legalentityid | String | Read-only |

## Example query for PayIntV1PositionUnionAgreementEntity

Entity name: mserp_payintv1positionunionagreemententities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1positionunionagreemententities
```

**Response**

```JSON
{  
    "mserp_positionid": "000052",
    "mserp_laborunionid": "MWA",
    "mserp_validto": "2024-01-01T00:00:00Z",
    "mserp_validfrom": "2024-01-01T00:00:00Z",
    "mserp_unionagreementname": "MWA - Machine Operators",
    "mserp_legalentityid": "USMF"
}
```
