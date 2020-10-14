---
# required metadata

title: Restrict editing of accounting distributions on invoices
description: This topic describes the steps for requiring the financial dimensions on a purchase order (PO) to match the dimensions on the corresponding vendor invoice.
author: v-kiarnd
manager: AnnBe
ms.date: 10/14/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Operations, Core 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
ms.search.industry: public sector
ms.author: v-kiarnd
ms.search.validFrom: 2020-10-15
ms.dyn365.ops.version: 10.0.15

---

# Restrict editing of accounting distributions on invoices

[!include[banner](../includes/banner.md)]

This topic describes the steps for requiring the financial dimensions on a purchase order (PO) to match the dimensions on the corresponding vendor invoice. You can set up specific financial dimensions that must match between a purchase order  and an invoice that’s created from that purchase order. For example, matching is required for all financial dimensions between purchase orders and invoices. On invoices associated with a PO, you can’t change the general ledger accounts on the invoice detail lines from what was entered on the PO lines.
 
## Setting up locked financial dimensions
Complete the following steps to define the financial dimensions that must match between a purchase order and related invoices.
1.	Open the **Accounts payable parameters**  page (**Accounts payable > Setup > Accounts payable parameters**).
2.	In the **Accounts payable parameters** page, click **PO/Invoice matching validation**. 
3.	Select the **Matching required** check box for the dimensions you want. All of the financial dimensions set up by on the **Financial dimensions** page  are available to select for matching.
4.	Click **Close**.
 
## Working with locked financial dimensions on an invoice
When you create a vendor invoice from a purchase order, you cannot edit the locked financial dimensions. If you attempt to make a change to a locked financial dimension, an error message will be provided, and the entire financial dimension string will revert back to the original string.
 
You can view financial dimensions for the invoice.
1.	Open the Pending vendor invoices page (**Accounts payable > Common > Vendor invoices > Pending vendor invoices**).
2.	Open the invoice.
3.	Click **Financials > Distribute amount** On the **Vendor invoice** page, in the Lines FastTab. 
 
> [!Note]
> Financial dimensions aren’t locked on lines that are added to an invoice manually and that aren’t based on PO. You can change the financial dimensions as needed on such an invoice until the invoice is posted.

