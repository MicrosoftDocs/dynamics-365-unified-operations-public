---
title: POS modernization and usability improvements
description: This article describes POS modernization and usability improvements in Microsoft Dynamics 365 Commerce Store Commerce.
author: anush6121
ms.author: anvenkat 
ms.topic: how-to 
ms.date: 07/16/2024
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
---

# POS modernization and usability improvements

[!include [banner](../includes/banner.md)]

This article describes point of sale (POS) modernization and usability improvements in Microsoft Dynamics 365 Commerce Store Commerce.

To improve POS usability and adapt to modern, intuitive workflows, numerous workflow improvements have been introduced.

## Modern transaction grid in POS transaction view

This feature is available from Commerce 10.0.42 release and includes refreshed transaction grid, numpad, customer card, and the button grids. It also enables retailers to show product image in cart view.

To enable this feature:

  1. Enable Modern Transaction Grid in POS Transaction View feature (**System administration > Workspaces > Feature management**)
  2. For each visual profile, set the **modern transaction grid** flag to **Yes** in the POS Visual Profiles configuration (**Retail and Commerce > Channel setup > POS setup > POS profiles > Visual profiles**). This allows you to rollout the changes to specific registers as needed.
  3. Run the **Registers (1090)** job to realize the change in POS.

## Streamlined workflow for adding items to a transaction from the product page

Two new workflows are introduced in the Commerce 10.0.40 release to handle situations where you add an item to the cart from the product description or search results page.

The first workflow shows a confirmation dialog box that clearly indicates that the item was successfully added to the cart. You can then continue to browse for products. This workflow is suited to assisted-selling scenarios where store associates browse and add many items to the cart.

The second workflow lets you immediately go to the transaction page after you add the item to the cart, so that you can continue with the transaction process. No confirmation dialog box is shown.

Starting with the Commerce 10.0.40 release, a configuration option in the POS visual profile in Commerce headquarters is used to select between the two workflows.

To bypass the confirmation dialog box and always go to transaction page after you add an item, in headquarters, go to **POS visual profiles**. In the **General** section, in the **Product details page** subsection, set the **Bypass Item added dialog** option to **Yes**. To show the confirmation dialog box, set the **Bypass Item added dialog** option to **No**.

> [!NOTE]
> After every configuration change made in headquarters, you must run the **Registers (1090)** job to realize the change in POS.

## Configure the display of search results

In the POS visual profile in headquarters, you can configure the phone view port default view for the display of search results for products, customers, and categories. Previously, the list view was the default view. Starting with the Commerce 10.0.40 release, search results in the phone view port can be shown in a card view by default to allow for easy product browsing. This update will be made available for other view ports in future releases.

To set your preference for the default search view, in headquarters, go to **POS visual profiles**. In the **General** section, in the **Search view** subsection, set the **Default view** field to **List view** or **Card view**.

> [!NOTE]
> After every configuration change made in headquarters, you must run the **Registers (1090)** job to realize the change in POS.

## Reset button grids at the end of a transaction

With this feature, the default button grid that is assigned to the first tab is restored when a transaction is completed, suspended, or voided. This feature helps reduce confusion and the number of clicks that are required when a store associate handles multiple transactions. This feature is enabled by default for all users and is available starting with the Commerce 10.0.40 release.

## Reprint receipts from a journal

To reduce the number of clicks that are required to reprint receipts, the **Print receipt** button is available at the bottom of the **Show journal** screen. To reprint receipts, select the journal and **Print receipt** in a single click. This feature is available starting with the Commerce 10.0.40 release.

## Enhanced date picker

To enable intuitive interactions, the date picker in the Store Commerce app is updated to a React control. This feature is available starting with the Commerce 10.0.39 release.

## Persist the zoom level

Store associates can persist their zoom settings, so that they don't have to readjust their display every time they open the application. This feature is especially useful for users who run the devices in kiosk mode without a keyboard and mouse. This feature is available starting with the Commerce 10.0.39 release.

## Payment capture improvements

To enable intuitive payment workflows in the POS application, the flows for payment by credit card, cash, and check are updated to provide a consistent and enhanced user experience. The remaining payment method flows will be refreshed in a future release. For more information about the payment capture improvements, see [Check out faster with optimized payment flows](dev-itpro/faster-checkout-pos.md). This feature is available starting with the Commerce 10.0.40 release.

## Fluent design

To improve performance, allow for extensibility, and remove legacy patterns, the number pad in the Store Commerce app is updated to use a React control in the payment workflows. This change prepares for a future larger React upgrade that extends to the transaction page and lets customers create their own custom views in React.

Also, minor updates that follow fluent design constructs were made to the user experience, such as rounded corners on tiles and buttons in the transaction grid, drop shadows and rollover elevation on product and category cards, and a refreshed sign-out experience. These updates are available by default starting with the Commerce 10.0.36 release.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
