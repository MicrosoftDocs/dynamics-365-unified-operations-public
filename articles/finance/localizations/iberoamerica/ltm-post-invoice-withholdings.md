---
title: Post vendor invoices with withholding taxes
description: Learn how to post vendor invoices with withholding taxes.
author: Fhernandez0088
ms.date: 10/03/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Post vendor invoices with withholding taxes

This article explains how to post vendor invoices with tax withholdings. These types of withholdings are used by several LATAM Expansion reports on many countries (i.e. Colombia, Chile, Venezuela, etc.)

## Post vendor invoice with tax withholdings

1. Go to **Accounts payable > Invoices > Invoice journal**.
2. Create a new journal and select a “Vendor invoice” type journal name.
3. Select **Lines**.
4. In the voucher line select a vendor.
5. In the **Credit** field enter a value.
6. Select an offset account.
7. Assign the tax groups containing the negative tax codes.
8. Complete the LATAM fields.
9. Post the journal.

> [!NOTE]
> The vendor invoice can be posted from any journal configured for that purpose and from purchase orders. Just be sure that the correct tax groups are assigned.
