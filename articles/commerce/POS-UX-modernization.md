---
title: Modern Workflows in POS
description: This article describes modern workflows in POS that improve usability, extensibility, and accessibility of Microsoft Dynamics 365 Commerce Store Commerce.
author: anush6121
ms.author: anvenkat 
ms.topic: how-to 
ms.date: 10/31/2024
ms.reviewer: v-chrgriffin
ms.custom: 
  - bap-template
---

# POS modernization and usability improvements

[!include [banner](../includes/banner.md)]
[!INCLUDE [banner](includes/preview-banner.md)]

This article describes modern workflows in POS that improve usability, extensibility, and accessibility of Microsoft Dynamics 365 Commerce Store Commerce.

The Dynamics 365 Commerce team is modernizing the POS by transitioning to the React framework and Fluent Design. The React framework enables mobile-optimized modern workflows, simplifies extensibility, and is accessibility compliant across browsers and all Store Commerce applications. Fluent Design complements the React framework by bringing visual clarity and consistency, creating a more intuitive experience for users of all abilities and improving accessibility out of the box.

The transaction page is the most used page on the POS, and is the first page to be fully moved to React and Fluent Design along with introducing new modern workflows for faster checkout.

## Prerequisites

To transition to the modern workflows on POS, the following prerequisites must be met:
1. You must be running Commerce version **10.0.40 or later**. For React-based controls on transaction grid, **10.0.44 or later** is required.
1. You must enable the **Enable Modern Transaction Grid in POS Transaction View**  feature in the Commerce headquarters.

To enable this feature in Commerce headquarters, follow these steps.
1. Go to the **Feature management** workspace (**System administration \> Workspaces \> Feature management**).
1. Search for the **Enable Modern Transaction Grid in POS Transaction View** feature, and then select it.
1. In the right pane, select **Enable now**.
1. Go to **POS visual profiles** (**Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> POS visual profiles**).
1. For each visual profile, set the **Modern transaction grid** option to **Yes**. This setting allows you to roll out changes to specific registers as needed.
1. Run the **Registers (1090)** job to implement the change in POS.


## Feature availability
The Commerce **10.0.40** release includes:
1. Streamlined workflow for adding items to cart
1. Configure display of search results
1. Reset of button grids at the end of a transaction
1. Reprint receipts from a journal
1. Payment workflows improvements

The Commerce **10.0.42** release includes:
1. Fluent Design on transaction, numpad, customer card, and button grids
1. Product images in the cart view.

The Commerce **10.0.43** release includes:
1.	Toast notification framework

The Commerce **10.0.44** release includes:
1. React-based controls on transaction page
1. Inline actions on transaction grid
1. Inline quantity update on transaction grid.
1. Loyalty upsell prompt

The following sections describe the capabilities in more details and additional configuration that may be needed.

## Inline actions on transaction grid
Inline actions on transaction grid are available for common line actions such as void product, return item, line discounts, price override, coupons, line comment and change unit of measure. The order of display of the inline actions is by frequency of use for each register and is automatically ordered based on usage.

To launch the inline actions list, hover over a line on the transaction grid and click on the 3 dots (…) that appears. On mobile and touch devices, inline actions can be accessed by long-pressing the line on transaction grid providing a more intuitive mobile-optimized experience.

There's an option for a more extensive list of line actions. To access additional line actions, you must enable the **Enable Advanced Line Inline Actions** feature in the Commerce headquarters **Feature management workspace (System administration > Workspaces > Feature management).**

Inline actions remove the need for nested buttons to access line operations, allowing for a cluster-free transaction page with fewer buttons.

This feature is available starting with the Commerce 10.0.44 release. Extensibility and customization of the line actions that can be included will be delivered in future releases.

## Inline quantity update on transaction grid
To change item quantity, click or tap the quantity directly within the transaction grid. This reduces the number of clicks and removes the need to navigate nested buttons providing a quick and intuitive workflow.

This feature is available starting with the Commerce 10.0.44 release.

## Payment capture improvements
Payment workflows in the POS application have been redesigned for all payment methods providing a consistent and enhanced user experience. For more information about the payment capture improvements, see [Check out faster with optimized payment flows](dev-itpro/faster-checkout-pos.md). This feature is available starting with the Commerce 10.0.40 release.

## Toast notification framework
The new toast notification framework brings flexible, real-time alerts to Store Commerce. With full extensibility support, this framework can be extended to build your own store notifications that meet your unique business needs. Use it to quickly share policy updates with store associates, flag low-stock items for restocking, alert staff when customers request assistance from in-store kiosks and more.

For more information about the toast notification framework, see [Offline reliability toast notifications in the Store Commerce app - Commerce](dev-itpro/retail-sdk/offline-reliability-toast-notifications.md).

This feature is available starting with the Commerce 10.0.43 release.

## Loyalty upsell prompt
The loyalty upsell prompt empowers store associates with the right information at the right time to inform customers about how close they are to reaching their next loyalty tier. This can nudge continued customer engagement to unlock new benefits leading to increased average order value through strategic upselling.

This feature is available starting with the Commerce 10.0.44 release. For more information on how to enable this feature, see [Loyalty Upsell Prompt](loyalty-upsell-prompt.md).

## Product images on transaction grid
Product images can now be displayed on the transaction grid.

Make sure to correctly set up and manage images for Store Commerce for this feature to work, see [Set up and manage images for Store Commerce](set-up-manage-images-retail-mpos.md).

This feature is available starting with the Commerce 10.0.42 release. Reach out to customer support to enable this feature in your environment.

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
Store associates can persist their zoom settings, eliminating the need to readjust the display each time the application is opened. This feature is especially useful for kiosk mode users without a keyboard and mouse, available from Commerce 10.0.39 release.

## Extensibility
The modernization and move to React-based controls on the transaction page keeps full parity with existing extensibility capabilities. Custom columns, fields, and controls continue to work as expected, making it easier to adopt the new experience without additional development effort.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
