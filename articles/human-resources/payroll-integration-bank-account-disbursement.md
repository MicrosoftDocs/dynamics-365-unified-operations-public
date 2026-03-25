---
# required metadata

title: Bank Account Disbursement entity
description: This article provides details and an example query for the Bank Account Disbursement entity in Microsoft Dynamics 365 Human Resources.
author: avanish2821
ms.date: 03/25/2026
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

# Bank Account Disbursement entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Bank Account Disbursement entity (PayIntV1BankAccountDisbursementEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the bank account disbursement.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Priority | mserp_priority | Real | Read-only |
| Linenumber | mserp_linenumber | Real | Read-only |
| Inprenotestatus | mserp_inprenotestatus | Enum | Read-only |
| Remainder | mserp_remainder | Enum | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Amount | mserp_amount | Real | Read-only |
| Accountidentificationid | mserp_accountidentificationid | String | Read-only |
| Company | mserp_company | String | Read-only |

## Example query for PayIntV1BankAccountDisbursementEntity

Entity name: mserp_payintv1bankaccountdisbursemententities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1bankaccountdisbursemententities
```

**Response**

```JSON
{  
    "mserp_priority": 100.00,
    "mserp_linenumber": 100.00,
    "mserp_inprenotestatus": 200000000,
    "mserp_remainder": 200000000,
    "mserp_personnelnumber": "000028",
    "mserp_amount": 0.00,
    "mserp_accountidentificationid": "Checking1",
    "mserp_company": "USMF"
}
```
