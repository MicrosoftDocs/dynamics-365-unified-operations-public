---
# required metadata

title: Bank account disbursement entity
description: This article provides details and an example query for the Bank account disbursement table entity in Microsoft Dynamics 365 Human Resources.
author: avanish2821
ms.date: 03/25/2026
ms.topic: how-to

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

# Bank account disbursement entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Bank account disbursement entity for Dynamics 365 Human Resources.

## Description

This entity provides information about bank account disbursement.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Amount | mshr\_Amount | Real | Read-only |
| Remainder | mshr\_Remainder | Int64 | Read-only |
| LegalEntity | mshr\_LegalEntity | Int64 | Read-only |
| LineNumber | mshr\_LineNumber | Real | Read-only |
| AccountIdentification | mshr\_AccountIdentification | Int64 | Read-only |
| Company | mshr\_Company | String | Read-only |
| AccountIdentificationId | mshr\_AccountIdentificationId | String | Read-only |
| Worker | mshr\_Worker | Int64 | Read-only |
| PersonnelNumber | mshr\_PersonnelNumber | String | Read-only |
| Priority | mshr\_Priority | Real | Read-only |

## Example query for PayIntV1BankAccountDisbursementEntity

Entity name: mshr\_bankaccountdisbursemententities\_

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mshr_bankaccountdisbursemententities_
```

**Response**

```JSON
{  
    "mshr_amount": 0,  
    "mshr_remainder": 200000001,  
    "mshr_linenumber": 100,  
    "mshr_company": "USMF",  
    "mshr_accountidentificationid": "Checking1",  
    "mshr_personnelnumber": "000028",  
    "mshr_priority": 100,  
    "mshr_primaryfield": "000028 | Checking1 | USMF"  
}
```
