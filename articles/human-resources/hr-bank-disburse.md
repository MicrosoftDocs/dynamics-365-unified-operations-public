---
# required metadata

title: Bank account disbursement entity
description: This article provides details and an example query for the Bank account disbursement table entity in Microsoft Dynamics 365 Human Resources.
author: jcart
ms.date: 04/24/2024
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

# Bank account disbursement entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Bank account disbursement entity (PayIntV1BankAccountDisbursementEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about bank account disbursement.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Amount | mserp\_Amount | Real | Read-only |
| Remainder | mserp\_Remainder | Int64 | Read-only |
| LegalEntity | mserp\_LegalEntity | Int64 | Read-only |
| LineNumber | mserp\_LineNumber | Real | Read-only |
| AccountIdentification | mserp\_AccountIdentification | Int64 | Read-only |
| Company | mserp\_Company | String | Read-only |
| AccountIdentificationId | mserp\_AccountIdentificationId | String | Read-only |
| Worker | mserp\_Worker | Int64 | Read-only |
| PersonnelNumber | mserp\_PersonnelNumber | String | Read-only |
| Priority | mserp\_Priority | Real | Read-only |

## Example query for PayIntV1BankAccountDisbursementEntity

Entity name: mserp\_payintv1bankaccountdisbursemententities\_

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1bankaccountdisbursemententities_
```

**Response**

```JSON
{  
    "mserp_amount": 0,  
    "mserp_remainder": 200000001,  
    "mserp_linenumber": 100,  
    "mserp_company": "USMF",  
    "mserp_accountidentificationid": "Checking1",  
    "mserp_personnelnumber": "000028",  
    "mserp_priority": 100,  
    "mserp_primaryfield": "000028 | Checking1 | USMF"  
}
```
