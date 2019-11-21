---
# required metadata

title: Posting invoices with zero amount
description: This topic provides information about how to post financial transactions for invoices with an amount of zero.
author: ilkond
manager: AnnBe
ms.date: 11/21/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
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

In Italy, it is required to post financial transactions for invoices with a total amount of zero.

## Prerequisites
Before you can post financial transactions for invoices with a total amount of zero, the following prerequisites must be met:

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, enable the **Posting invoices with zero amount** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

### Post invoices with zero amount
This feature is applicable to invoices that are created in the **Accounts receivable** and **Accounts payable** modules.
When posting invoices with an amount of zero, the system creates **Customer/ Vendor transactions** and **Voucher transactions**.

 

