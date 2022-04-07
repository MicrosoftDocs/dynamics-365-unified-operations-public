---
# required metadata

title: Prices include sales tax configuration for e-Commerce channel
description: This topic provides guidance on how to configure an e-commerce channel to show or hide taxes breakup in prices include sales tax scenario.
author: gvrmohanreddy
ms.date: 04/07/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-03-28
---

[!include [banner](includes/banner.md)]

# Prices include sales tax configuration for e-Commerce channel

This topic provides guidance on how to configure e-Commerce channel to show or hide taxes breakup in prices include sales tax scenario

Your business in a specific legal entity may have **prices include sales tax** scenario and in your e-Commerce channel, on Dynamics 365 Commerce, you can now choose to show taxes breakup or hide taxes breakup, as your business requires. With 10.0.27 release, Dynamics 365 Commerce is rolling out some enhancements related to **prices include sales tax ** in your e-Commerce channel, giving an ability to show taxes breakup accurately and consistently across the pages such as cart, checkout, order confirmation and order details, or hide the taxes breakup. 

![Examples of cart with tax breakup shown and hidden](media/prices-include-sales-tax-e-Commerce.png)

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

![Show taxes breakup in order summary option highlighted in site builder](media/prices-include-sales-tax-e-Commerce-site-settings.png)

## Additional resources

[Sales tax overview](/finance/general-ledger/indirect-taxes-overview)

[Configure sales tax for online orders](sales-tax-config.md)

[Troubleshoot: Taxes on online orders are incorrectly calculated](troubleshoot/tax-miscalculated-online-order.md)
