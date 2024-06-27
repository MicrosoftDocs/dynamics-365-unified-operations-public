---
title: POS modernization and usability improvements
description: This article describes POS modernization and usability improvements in Microsoft Dynamics 365 Commerce Store Commerce.
author: anush6121
ms.author: anvenkat 
ms.topic: article 
ms.date: 06/27/2024
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
---

# POS modernization and usability improvements

[!include [banner](../includes/banner.md)]

This article describes point of sale (POS) modernization and usability improvements in Microsoft Dynamics 365 Commerce Store Commerce.

To improve POS usability and adapt to modern, intuitive workflows, numerous workflow improvements that have been introduced. 

## Streamlined workflow for adding items to a transaction from the product page

When you add an item to the cart from the product description or search results pages, two new workflows are introduced in the Commerce 10.0.40 release. 

The first workflow shows a confirmation dialog after an item is added to the cart from the product description or search results pages that clearly indicates to the user that their action was successful. This workflow allows users to continue browsing for more products and is suited for assisted selling scenarios where store associates are browsing and adding many items to the cart.

The second workflow allows the user to immediately navigate to the transaction page once an item is added to the cart. This workflow allows user to immediately proceed to the transaction page to continue with the transaction process. 

Starting with the Commerce 10.0.40 release, these workflows can be selected using a configuration option in the POS visual profile in Commerce headquarters. 

To bypass the confirmation dialog and always navigate to transaction page after adding an item, in headquarters go to **POS visual profiles**. Under the **General** section, in the **Product details page** subsection, set the **Bypass Item added dialog** option to **Yes**.

To see the confirmation dialog, set the **Bypass Item added dialog** option to **No**.

## Configure display of search results

You can now configure the default view for displaying search results in the POS visual profile in headquarters. Previously, the list view was the default view for search results for products, customers, and categories. Starting with the Commerce 10.0.40 release, search results can default to a card view to allow easy products browsing.

To enable your search view preference, in headquarters go to **POS visual profiles**. Under the **General** section, in the **Search view** subsection, set **Default view** to **List view** or **Card view**.

## Reset button grids at the end of a transaction

With this feature, the default button grid assigned to the first tab is restored when a transaction is completed, suspended, or voided. This feature helps reduce confusion and the number of clicks when multiple transactions are handled by a store associate. This feature is enabled by default for all users and is available starting with the Commerce 10.0.40 release. 

## Reprint receipts from journal

To reduce number of clicks in reprinting receipts, the **Print receipt** button is available on the bottom of the **Show journal** screen. To reprint receipts, select the journal and **Print receipt** with a single click. This feature is available starting with the Commerce 10.0.40 release.

## Enhanced date picker

To enable intuitive interactions, the date picker in the Store Commerce app is updated to a React control. This feature is available starting with the Commerce 10.0.39 release. 

## Persist zoom level

Store associates can persist the zoom settings to fix their display and avoid adjusting it every time the application is reopened, which is especially useful for users who run the devices in kiosk mode without a keyboard and mouse. This feature is available starting with the Commerce 10.0.39 release. 

## Payment capture improvements 

To enable intuitive payment workflows in POS application, pay by credit card, cash, and check flows are updated to provide a consistent and enhanced user experience. The rest of the payment method flows will be refreshed in a future release. For more information on the payment capture improvements, see [Check out faster with optimized payment flows](dev-itpro/faster-checkout-pos.md). This feature is available starting with the Commerce 10.0.40 release.

## Fluent design

To improve performance, allow for extensibility, and remove legacy patterns, the number pad in the Store Commerce app is updated to use a React control in the payment workflows. This change prepares for a future larger React upgrade that extends to the transaction page, and also enables customers to create their own custom views in React.



[!INCLUDE[footer-include](../includes/footer-banner.md)]


