---
# required metadata

title: Use Dynamics 365 Commerce pricing engine with Dynamics 365 Sales
description: This topic describes how to use the Commerce pricing engine for Sales quote creation in Dynamics 365 Sales.
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

# Use Dynamics 365 Commerce pricing engine with Dynamics 365 Sales

[!include [banner](../../includes/banner.md)]

This topic describes how to use the Commerce pricing engine for sales quote creation in Dynamics 365 Sales.

Microsoft Dynamics 365 Commerce pricing engine supports most of the business-to-consumer (B2C) pricing scenarios such as store level pricing, affiliation and loyalty-based pricing, mix and match discounts, quantity discounts, and threshold discounts. The pricing engine uses complex rules to determine the best price for a given quotation or order. When you use [dual-write](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-overview), you have three choices for your pricing needs. You can use the static pricing coming from the Dynamics 365 Sales price list, the pricing engine from Dynamics 365 Supply Chain Management, or the pricing engine from Dynamics 365 Commerce. As mentioned before, Commerce pricing is best suited for your B2C scenarios.

## Use the Commerce pricing engine in Dynamics 365 Sales

> [!NOTE]
> The Commerce pricing engine can currently only be used for the Quotes creation in the Dynamics 365 Sales application. The sales order integration with Commerce pricing will be available in future releases.

When a user initiates a quote in Dynamics 365 Sales, the dual-write framework copies the quote details in Dynamics 365 Commerce. Any changes to the existing quote lines or newly-added quote lines from Dynamics 365 Sales get copied to the Commerce application. Whenever users want to price the quote based on the Commerce pricing engine, they can select the **Price quote** button to update the prices of the quote based on the Commerce pricing engine. With this action, the prices are updated automatically in both Sales and Commerce applications.  

## Prerequisites   

- Following the steps provided in [Prospect-to-cash in dual-write](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-prospect-to-cash/) is a prerequisite for using Commerce pricing from Sales application.
- The trade agreement evaluation for manual entry should be disabled. To disable the trade agreement evaluation for manual entry, follow these steps.
    1. Navigate to your Dynamics 365 Commerce environment.
    1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
    1. Select the **Prices** tab in the side navigation bar.
    1. Under the **Trade agreement evaluation** FastTab, clear the **Manual entry** check box.
    
## Additional resources

[Prospect-to-cash in dual-write](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-prospect-to-cash/)



