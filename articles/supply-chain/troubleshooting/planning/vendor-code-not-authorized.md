---
title: Vendor code isn't authorized for a specific product and date
description: When you try to firm a planned order or add a line to a purchase order, you receive an error message that states that the vendor code isn't authorized for a product and date.
author: ankubik
ms.date: 06/10/2021
ms.topic: troubleshooting
ms.search.form: ReqTransPO_ReqTransPoMarkFirm
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: ankubik
ms.search.validFrom: 2021-06-10
ms.dyn365.ops.version: 10.0.20
---

# Vendor code isn't authorized for a specific product and date

Error code: SYP4881415

## Symptoms

When you try to firm a planned order or add a line to a purchase order, you receive the following error message:

> Vendor code %1 is not authorized for %2 on %3.

## Cause

The error occurs because the **Approved vendor check method** field is set to *Warning only* or *Not allowed* for the specified product, and the vendor isn't currently authorized to supply that product.

## Resolution

To fix this issue, either disable the vendor check for the relevant product or approve the vendor.

To disable the vendor check for a product, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Open the relevant product.
1. On the **Purchase** FastTab, set the **Approved vendor check method** field to a value other than *Warning only* or *Not allowed*.

To approve a vendor for a product, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Open the relevant item.
1. On the Action Pane, on the **Purchase** tab, in the **Approved vendor** group, select **Setup**.
1. On the **Approved vendor** list page, add a row to the grid, and set the following values for it:

    - **Vendor** – Select the vendor to approve for the current product.
    - **Effective date** – Select the first date that the vendor is approved for.
    - **Expiration date** – Select the last date that the vendor is approved for.

For more information, see [Approve vendors for specific products](../../procurement/tasks/approve-vendors-specific-products.md).
