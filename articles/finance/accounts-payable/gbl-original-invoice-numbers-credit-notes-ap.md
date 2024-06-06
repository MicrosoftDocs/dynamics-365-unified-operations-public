---
title: Reference original invoices in credit notes (vendor invoices)
description: Learn about how to create a reference to an original invoice when you create a credit note, including prerequisites.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: article
ms.date: 09/28/2021
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-09-23
ms.search.form:
ms.dyn365.ops.version: 10.0.20
---

# Reference original invoices in credit notes (vendor invoices)

[!include [banner](../includes/banner.md)]

In some countries and regions, there's a legal requirement that printed credit notes or reporting routines include references to the original invoices. This article describes how to create a reference to an original invoice when you create a credit note.

## Prerequisites

In the **Feature management** workspace, enable the **Enable credit invoicing for vendor invoices** feature. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The functionality that is described in this article applies to the following business documents.

**Accounts payable:**

- Purchase order
- Invoice journal
- Invoice register

**General ledger:**

- General journal

## Define a reference to an original invoice

Defining a reference to an original invoice includes the following high-level steps:
1. Create and post a vendor invoice.
2. Create a vendor credit note.
3. Use the Credit invoicing function to link the invoice with a credit note.
4. Post the credit note.

Use the following procedures to define a reference to an original invoice in the specified business document types.

### Vendor credit note (purchase order)

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
2. Create a new purchase order, or use existing one to create a credit note.
3. On the Action pane, on the **Invoice** tab, in the **Introduce** group, select **Credit invoicing**.
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
