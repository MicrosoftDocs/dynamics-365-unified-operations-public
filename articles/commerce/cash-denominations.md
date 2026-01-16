---
title: Configure cash denominations for the point of sale (POS)
description: Learn how to configure cash denominations for Microsoft Dynamics 365 Commerce point of sale (POS).
author: josaw1
ms.date: 01/16/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.assetid: f28a827c-3a50-4d5e-83eb-e5a768db70a1
ms.search.industry: Retail
ms.search.form: RetailStoreTable, RetailStoreCashDeclarationTable
---

# Configure cash denominations for the point of sale (POS)

[!include [banner](includes/banner.md)]

This article explains how to configure cash denominations for Microsoft Dynamics 365 Commerce point of sale (POS).

You can define cash denominations for notes and coins in Dynamics 365 Commerce headquarters. Cashiers, sales associates, and managers at the store can use these denominations within the POS. Use these denominations to help count cash for end of day tender declarations or for quickly tendering a sale.

## Define denominations

Set up denominations per store on the **Set up** > **Cash declaration** option from the store property page.

:::image type="content" source="./media/image1-denomination.png" alt-text="Screenshot of the Cash declaration option in the store setup menu.":::

To define a denomination:

1. Select **New**.
1. Enter the type (coin or note).
1. Enter the amount (value).

:::image type="content" source="./media/image2-denomination.png" alt-text="Screenshot of the Cash declaration denominations page showing denomination configuration.":::

## Configure the functionality profile

When you pay by cash in POS, use the note denominations to quickly enter the amount the customer pays. In the functionality profile, you can configure the two options for showing the denomination in POS.

- **Greater or equal to amount due** – By default, POS shows only the note denominations that are greater than the amount due, which it allows for one-touch tendering. For example, if the amount due is $7.50, POS shows the following denominations: $10, $20, $50, and $100. Touching any of these amounts automatically tenders the sale for that amount. The $1 and $5 notes don't show since these amounts are less than the amount due.
- **All denominations** – Select this option to always show all note denominations in POS, regardless of the amount due. The user can use a combination of notes to reach the amount due. For example, if the amount due is $25.00, the user can choose $20 and $5 to complete the sale.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
