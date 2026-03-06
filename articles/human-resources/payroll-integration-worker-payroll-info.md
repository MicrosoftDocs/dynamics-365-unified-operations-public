---
# required metadata

title: Worker Payroll Info entity
description: This article provides details and an example query for the Hcm Worker Payroll Info entity in Microsoft Dynamics 365 Human Resources.
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

# Worker Payroll Info entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Hcm Worker Payroll Info entity (PayIntV1HcmWorkerPayrollInfoEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the worker payroll info.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Dataareaid | mserp_dataareaid | String | Read-only |
| Readytopay | mserp_readytopay | Enum | Read-only |
| Paymentmethod | mserp_paymentmethod | Enum | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Company | mserp_company | String | Read-only |

## Example query for PayIntV1HcmWorkerPayrollInfoEntity

Entity name: mserp_payintv1hcmworkerpayrollinfoentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmworkerpayrollinfoentities
```

**Response**

```JSON
{  
    "mserp_dataareaid": "USRT",
    "mserp_readytopay": 200000000,
    "mserp_paymentmethod": 200000000,
    "mserp_personnelnumber": "000023",
    "mserp_company": "USRT"
}
```
