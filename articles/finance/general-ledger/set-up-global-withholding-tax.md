---
title: Set up global withholding tax
description: Learn about the steps for setting up global withholding tax for sales and purchases, including multiple steps for setting up withholding tax within ledger groups.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.date: 06/15/2026
ms.reviewer: kfend 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-01-12
ms.search.form:
ms.dyn365.ops.version: AX 10.0.17
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
---

# Set up global withholding tax

This article lists the steps for setting up global withholding tax for sales and purchases.

1. Set up withholding tax authorities on the **Withholding tax authorities** page.

1. Set up withholding settlement periods on the **Withholding tax settlement periods** page.

1. Set up withholding ledger posting group on the **Withholding tax > ledger posting group** page.

   > [!NOTE]
   >
   > Assign the **Withholding tax** account to a main account with a **Posting type** of Withholding tax. Assign the **Withholding tax offset** account to a main account with a **Posting type** of "Withholding tax offset". Go to **General ledger > Chart of accounts > Accounts > Main accounts** and set up the **Posting type** in the **Posting validation** sub-form for the main accounts.

1. Set up withholding tax codes on the **Withholding tax codes** page.

1. Set up withholding tax groups on the **Withholding tax groups** page.

1. Set up withholding tax revenue types on the **Withholding tax revenue types** page.

1. Set up withholding tax groups on the **Item withholding tax groups** page for an item or service.

1. Set up **Minimum invoice amount** on the **General ledger parameters > Withholding tax** page.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
