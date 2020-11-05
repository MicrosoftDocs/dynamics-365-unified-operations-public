---
# required metadata

title: Use Dynamics 365 Commerce pricing engine with Dynamics 365 Sales
description: This topic describes how to use the Commerce pricing engine for Sales quote creation in Dynamics 365 Sales.
author: ShalabhjainMSFT
manager: AnnBe
ms.date: 11/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
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

Microsoft Dynamics 365 Commerce pricing engine supports most of the B2C pricing scenarios such as store level pricing, affiliation and loyalty based pricing, mix and match discounts, quantity discounts, threshold discounts etc. The pricing engine uses complex rules to determine the best price for a given quotation or order. When you use dual-write, you have three choices for your pricing needs. You can use the static pricing coming from the Dynamics 365 Sales price list, or you can use the pricing engine from Dynamics 365 Supply Chain Management or use the pricing engine from Dynamics 365 Commerce application. As mentioned before, Commerce pricing is best suited for your B2C scenarios.

## Use the Commerce pricing engine in Sales

> [!NOTE]
> The Commerce pricing engine can currently be used only for the Quotes creation in the Dynamics 365 Sales application. The sales order integration with Commerce pricing will be available in future releases.

When the user initiates a quote in the Sales application, the dual write framework copies the quote details in the Dynamics 365 Commerce application. Any changes to the existing quote lines or newly added quote lines from Sales application get copied to the Commerce application. Whenever the users want to price the quote based on the Commerce pricing engine, they can click on the "Price quote" button to update the prices of the quote based on Commerce pricing engine. With this action, the prices are updated automatically in both Sales and Commerce applications.  

## Prerequisites   
- Steps provided in the "Prospect to cash" document are a prerequisite for using Commerce pricing from Sales application. Here is a link to [Prospect to cash](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-prospect-to-cash/) 

- The trade agreement evaluation for Manual entry should be disabled. Here are the steps:
    - Navigate to your Dynamics 365 Commerce environment.
    - Navigate to **Accounts receivable \> Setup \> Accounts receivable parameters**.
    - Select the **Prices** tab in the side navigation bar.
    - Under the **Trade agreement evaluation** fast tab, uncheck the **Manual entry** option.
