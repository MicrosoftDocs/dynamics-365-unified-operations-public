---
# required metadata

title: Use the Dynamics 365 Commerce pricing engine with Dynamics 365 Sales
description: This topic describes how to use the Microsoft Dynamics 365 Commerce pricing engine to create sales quotations in Dynamics 365 Sales.
author: ShalabhjainMSFT
manager: AnnBe
ms.date: 11/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: shajain
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-11-03

---

# Use the Dynamics 365 Commerce pricing engine with Dynamics 365 Sales

[!include [banner](../../includes/banner.md)]

This topic describes how to use the Microsoft Dynamics 365 Commerce pricing engine to create sales quotations in Dynamics 365 Sales.

The Dynamics 365 Commerce pricing engine supports most business-to-consumer (B2C) pricing scenarios, such as store-level pricing, affiliation-based and loyalty-based pricing, mix-and-match discounts, quantity discounts, and threshold discounts. The pricing engine uses complex rules to determine the best price for a given quotation or order.

When you use [dual-write](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-overview), you have three options for your pricing needs. You can use the static pricing that comes from the price list in Dynamics 365 Sales, the pricing engine in Dynamics 365 Supply Chain Management, or the pricing engine in Dynamics 365 Commerce. Among these options, the Commerce pricing engine is best suited to B2C scenarios.

## Use the Commerce pricing engine in Sales

> [!NOTE]
> Currently, the Commerce pricing engine can be used only for quotation creation in the Sales. Sales order integration with the Commerce pricing engine isn't yet available.

When users initiate a quotation in Sales, the dual-write framework copies the quotation details to Commerce. Any changes to existing quotation lines or any newly added quotation lines in Sales are copied to Commerce. When users want to use the Commerce pricing engine to price the quotation, they can select **Price quote** to update the prices of the quotation, based on the Commerce pricing engine. Prices are then automatically updated in both Sales and Commerce.

## Prerequisites

- Before you can use the Commerce pricing engine in Sales, you must follow the steps in [Prospect-to-cash in dual-write](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-prospect-to-cash/).
- You must turn off trade agreement evaluation for manual entry by following these steps:

    1. In your Commerce environment, go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
    1. On the **Prices** tab, on the **Trade agreement evaluation** FastTab, clear the **Manual entry** check box.

## Additional resources

[Prospect-to-cash in dual-write](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-prospect-to-cash/)
