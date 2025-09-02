---
title: Create a purchase order for a one-time supplier
description: Learn how to create a purchase order for a one-time supplier, including an example step-by-step process
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchCreateOrder  
ms.topic: how-to
ms.date: 06/17/2025
ms.custom: 
  - bap-template
---

# Create a purchase order for a one-time supplier

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a purchase order for a one-time supplier. The supplier is created automatically with the purchase order, rather than having to create the vendor account manually. Purchase orders are typically created by a purchasing agent. A one-time vendor account must already be set up in the **Account payable parameters** page.

To create a purchase order for a one-time supplier, follow these steps:

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
2. Select **New**.
3. Select *Yes* in the **One-time supplier** field. A vendor account is automatically created and assigned to the purchase order. The vendor account is created based on the template that is specified on the **General** tab in the **Accounts payable parameters** page.  
4. In the **Name** field, type a name for the supplier.
5. Select **OK**. The purchase order can now be completed and processed like any other order. There are no special characteristics related to how this is done. The invoice will account a due transaction on the vendor account that was created with the order, and payment will then be processed.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
