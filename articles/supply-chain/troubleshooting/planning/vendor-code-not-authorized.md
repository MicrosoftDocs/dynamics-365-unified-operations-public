---
title: Vendor code isn't authorized for a specific product and date
description: "When you try to firm a planned order or add a line to a purchase order, you get the error:
'Vendor code %1 is not authorized for %2 on %3'"
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

When you try to firm a planned order or add a line to a purchase order, you see the following error message:

> Vendor code %1 is not authorized for %2 on %3.

## Cause

This error occurs because **Approved vendor check method** is set to *Warning only* or *Not allowed* for the specified product, and the vendor is not currently authorized to supply that product.

## Resolution

To resolve this issue, either approve the vendor or disable the vendor check for the relevant product.

To disable the vendor check for a product:

1. Go to **Product information management > Products > Released products**
1. Open the relevant product.
1. Expand the **Purchase** FastTab.
1. Set **Approved vendor check method** to a value other than *Warning only* or *Not allowed*.

To approve a vendor for a product:

1. Go to **Product information management > Products > Released products**
1. Open the relevant item.
1. On the Action Pane, open the **Purchase** tab and, from the **Approved vendor** group, select **Setup**.
1. The **Approved vendor list page** opens. Add a new row to the grid and make the following settings for it:
    - **Vendor** – Select the vendor that you want to approve for the current product.
    - **Effective date** – Select the first date for which the vendor is approved.
    - **Expiration date** – Select the last date on which the vendor will be approved.

For more information, see [Approve vendors for specific products](dynamics365/supply-chain/procurement/tasks/approve-vendors-specific-products.md).
