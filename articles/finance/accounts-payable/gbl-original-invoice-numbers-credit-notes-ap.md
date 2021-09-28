---
# required metadata

title: Reference original invoices in credit notes (vendor invoices)
description: This topic describes how to create a reference to an original invoice when you create a credit note.
author: v-oloski
ms.date: 09/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: v-oloski
ms.search.validFrom: 2021-09-23
ms.dyn365.ops.version: 10.0.20

---

# Reference original invoices in credit notes (vendor invoices)

[!include [banner](../includes/banner.md)]

This topic describes how to create a reference to an original invoice when you create a credit note.

## Prerequisites

In the **Feature management** workspace, enable the **Enable credit invoicing for vendor invoices** feature. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The functionality that is described in this topic applies to the following business documents.

**Accounts payable:**

- Purchase order
- Invoice journal
- Invoice register

**General ledger:**

- General journal

## Define a reference to an original invoice

Use the following procedures to define a reference to an original invoice in the specified business document types.

### Vendor credit note (purchase order)

1. Go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
2. Create a new purchase order, or use existing one to create a credit note.
3. On the Action Pane, on the **Invoice** tab, in the **Introduce** group, select **Credit invoicing**.
4. Enter the reason for the correction and the reference to the original invoice.

### Vendor credit note (ledger journals)

1. Follow one of these steps:

    - Go to **Accounts payable** \> **Invoice journals**.
    - Go to **Accounts payable** \> **Invoice register**.
    - Go to **General ledger** \> **Journal entries** \> **General journals**.

2. Create a new journal and new journal lines.
3. On the Action Pane, select **Functions** \> **Credit invoicing**.
4. Enter the reason for the correction and the reference to the original invoice.

> [!NOTE]
> The **Credit invoicing** command is visible in a general journal voucher if the **Account type** field is set to **Vendor**.
