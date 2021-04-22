---
# required metadata

title: Posting invoices with zero amount
description: This topic explains how you can post financial transactions for invoices that have an amount of 0 (zero).
author: ilkond
ms.date: 11/21/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2019-11-29
ms.dyn365.ops.version: 10.0.8

---

# Posting invoices with zero amount

[!include [banner](../includes/banner.md)]

In Italy, financial transactions for invoices that have a total amount of 0 (zero) must be posted.

## Prerequisites

Before you can post financial transactions for invoices that have a total amount of 0 (zero), the following prerequisites must be met:

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, turn on the **Posting invoices with zero amount** feature. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Posting invoices that have an amount of 0 (zero)

The Posting invoices with zero amount feature applies to invoices that are created in the **Accounts receivable** and **Accounts payable** modules.

When invoices that have an amount of 0 (zero) are posted, the system creates customer/vendor transactions and voucher transactions.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]