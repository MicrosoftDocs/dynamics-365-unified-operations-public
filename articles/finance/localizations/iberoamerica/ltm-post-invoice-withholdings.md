---
title: Post vendor invoices with withholding taxes
description: Learn how to post vendor invoices with withholding taxes.
author: Fhernandez0088
ms.date: 10/07/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Post vendor invoices with withholding taxes

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to post vendor invoices with tax withholdings. Several LATAM Expansion reports use these types of withholdings in many countries and regions, such as Colombia, Chile, and Venezuela.

## Post vendor invoice with tax withholdings

To post vendor invoice with tax withholdings, follow these steps:

1. Go to **Accounts payable** > **Invoices** > **Invoice journal**.
1. Create a new journal and select a "Vendor invoice" type journal name.
1. Select **Lines**.
1. In the voucher line, select a vendor.
1. In the **Credit** field, enter a value.
1. Select an offset account.
1. Assign the tax groups containing the negative tax codes.
1. Complete the LATAM fields.
1. Post the journal.

> [!NOTE]
> You can post the vendor invoice from any journal configured for that purpose and from purchase orders. Just be sure that you assign the correct tax groups.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
