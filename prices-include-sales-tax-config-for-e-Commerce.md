---
# required metadata

title: Prices include sales tax configuration for e-Commerce channel
description: This topic provides guidance on how to configure an e-commerce channel to show or hide taxes breakup in prices include sales tax scenario.
author: [gvrmohanreddy]
manager: jeffbl
ms.date: 03/28/2022
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2022-03-28
ms.dyn365.ops.version: 10.0.27
---

[!include [banner](../../includes/banner.md)]

This topic provides guidance on how to configure e-Commerce channel to show or hide taxes breakup in prices include sales tax scenario

Your business in a specific legal entity may have **prices include sales tax** scenario and in your e-Commerce channel, on Dynamics 365 Commerce, you can now choose to show taxes breakup or hide taxes breakup, as your business requires. With 10.0.27 release, Dynamics 365 Commerce is rolling out some enhancements related to **prices include sales tax ** in your e-Commerce channel, giving an ability to show taxes breakup accurately and consistently across the pages such as cart, checkout, order confirmation and order details, or hide the taxes breakup. 

![Dynamics 365 Commerce - Show or hide taxes in e-commerce](media/prices-include-sales-tax-e-Commerce.png)

Enhancements also bring consistency in calculating taxes for shipping charges and other charges so that both showing and hiding taxes scenarios show order summary accurately, across the pages, on E-Commerce site. 

## Configuration

> [!NOTE]
> These enhancements are applicable only when e-Commerce channel's **prices include sales tax scenario** is set to yes, in Dynamics 365 Commerce Headquarters. 

### Showing taxes breakup in order summary

Starting from Dynamics 365 Commerce version 10.0.27, a change is made to calculate the line-level refundable charges based on the quantity returned.  Follow below steps to enable this feature.

1. Go to the site that you want to update.
2. In **Site settings**, open the **Extensions**.
3. Find **Show taxes breakup in order summary** option, by default it's enabled, which means end users see taxes breakup, in prices include sales tax scenario. 
4. Disable  **Show taxes breakup in order summary** option if you don't want to show taxes break up for end users on your e-Commerce channel. 

![Dynamics 365 Commerce - Show or hide taxes in e-commerce](media/prices-include-sales-tax-e-Commerce-site-settings.png)

## Additional resources

[Sales tax overview](/dynamics365/finance/general-ledger/indirect-taxes-overview?toc=/dynamics365/commerce/toc.json)

[Configure sales tax for online orders](commerce/sales-tax-config)

[Troubleshoot: Taxes on online orders are incorrectly calculated](troubleshoot/tax-miscalculated-online-order.md)
