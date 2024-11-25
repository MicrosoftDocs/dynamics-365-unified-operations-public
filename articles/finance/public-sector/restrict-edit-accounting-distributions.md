---
title: Restrict editing of accounting distributions on invoices
description: Learn how to require that the financial dimensions on a purchase order (PO) match the dimensions on the corresponding vendor invoice.
author: leizi2015
ms.author: raynezou
ms.topic: article
ms.date: 08/07/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-15
ms.search.form:
ms.dyn365.ops.version: 10.0.15
---

# Restrict editing of accounting distributions on invoices

[!include[banner](../includes/banner.md)]

This article explains how to require that the financial dimensions on a purchase order (PO) match the dimensions on the corresponding vendor invoice. You can set up specific financial dimensions that must match between a PO and an invoice that is created from it. For example, you can require that all financial dimensions match between POs and invoices. On invoices that are associated with a PO, you can't change the general ledger accounts on the invoice detail lines so that they differ from the accounts that were entered on the PO lines.

## Set up locked financial dimensions

Follow these steps to define the financial dimensions that must match between a PO and related invoices.

1. Go to **Accounts payable \> Setup \> Accounts payable parameters**.
2. On the **Accounts payable parameters** page, select **PO/Invoice matching validation**.
3. Select the **Matching required** check box for the dimensions that must match. All the financial dimensions that are set up on the **Financial dimensions** page are available for selection.
4. Select **Close**.

## Work with locked financial dimensions on an invoice

When you create a vendor invoice from a purchase order, you can't edit the locked financial dimensions. If you try to edit a locked financial dimension, you receive an error message, and the whole financial dimension string reverts to the original string.

You can view financial dimensions for the invoice.

1. Go to **Accounts payable \> Common \> Vendor invoices \> Pending vendor invoices**.
2. Open the invoice.
3. On the **Vendor invoice** page, on the **Lines** FastTab, select **Financials \> Distribute amount**.

> [!NOTE]
> The financial dimension advanced rule setting of the accounting structure is incompatible with this feature. When using the **Restrict editing of accounting distributions on invoices** feature, don't introduce additional segments for the main account.  
