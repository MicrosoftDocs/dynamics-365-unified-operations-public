---
title: Modern workflows in POS (preview)
description: This article provides an overview of modernized workflows that improve the usability, extensibility, and accessibility in Microsoft Dynamics 365 Commerce Store Commerce point of sale (POS).
author: anush6121
ms.author: anvenkat 
ms.topic: overview
ms.date: 02/10/2026
ms.reviewer: v-griffinc
ms.custom: 
  - bap-template
---

# Modern workflows in POS (preview)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article provides an overview of modernized workflows that improve the usability, extensibility, and accessibility in Microsoft Dynamics 365 Commerce Store Commerce point of sale (POS).

As of the Dynamics 365 Commerce 10.0.47 release, Store Commerce POS features continue to be enhanced with modern, mobile‑optimized POS experiences. These enhancements are built on the React‑based POS foundation and Fluent UI to bring a more consistent, faster, and accessible interface across devices. These updates help associates find products faster, understand product details more clearly, and surface contextual insights.

The React framework enables mobile-optimized modern workflows, simplifies extensibility, and complies with accessibility requirements across browsers and all Store Commerce applications. Fluent Design complements the React framework by bringing visual clarity and consistency, creating a more intuitive experience for users of all abilities and improving accessibility out of the box.

## Feature availability

The Commerce 10.0.47 release includes:
- **Modern search view results**
  - Refreshed product tiles.
  - Larger imagery.
  - Add to sale button on each card.
  - Filter/sort at the top.
  - Compact/tile view toggle.
  - Quantity discount captions.
  - Inventory visibility.
- **Modern product details page**
  - Sticky layout.
  - Always-visible key actions.
  - Improved image gallery.
  - Dimension/quantity controls.
  - Accordion sections.
  - Related products carousel.
  - Inventory preview.
  - Quantity discount.
- **Modern transaction grid cart**
  - Quantity discount captions.
  - Threshold discount bar.
  - Refreshed and extensible cart suggestions.

The Commerce 10.0.44 release includes:
- React-based controls on the transaction page.
- Inline actions on the transaction grid.
- Inline quantity update on the transaction grid.
- Loyalty upsell prompt.

The Commerce 10.0.43 release includes:
- Toast notification framework.

The Commerce 10.0.42 release includes:
- Fluent Design on transaction, numpad, customer card, and button grids.
- Product images in the cart view.

The Commerce 10.0.40 release includes:
- Streamlined workflow for adding items to cart.
- Ability to configure the display of search results.
- Reset of button grids at the end of a transaction.
- Ability to reprint receipts from a journal.
- Payment workflow improvements.

The Commerce 10.0.39 release includes:
- Enhanced date picker.
- Persist the zoom level.

The following sections describe the capabilities in more detail and the additional configuration that may be needed.

## Modern search view results

This feature introduces a streamlined React‑based search results experience designed for efficient, insight‑driven product discovery and supported by refreshed mobile‑optimized layouts and a streamlined card design. To help associates quickly find the right product, the modern search view surfaces contextual insights such as discount cues and availability directly in the search results.

### Commerce version 10.0.47 feature enhancements

- **Refreshed product tiles** – This enhancement presents a cleaner layout that improves scan speed and reduces visual clutter.
- **Larger imagery** – This enhancement supports quicker visual recognition, helping associates verify products at a glance.
- **Add to sale button on each card** – This enhancement shortens the path to starting a transaction by eliminating extra taps.
- **Filter/sort at the top** – This enhancement makes it easier to refine results without scrolling.
- **Compact/tile view toggle** – This enhancement lets associates switch between showing more cards per row (compact) or larger, more detailed cards (tile).
- **Quantity discount captions** – This enhancement helps associates explain pricing benefits clearly.
- **Inventory visibility** – This enhancement provides store and nearby availability directly on the card.

To enable this feature and related enhancements, follow these steps:

1. In headquarters, go to the **Feature management** workspace (**System administration > Workspaces > Feature management**) and enable **Enable modernized search view results**.
1. To enable the quantity discount captions enhancement, in headquarters go to **POS visual profile** and enable **Show quantity discount captions**.
1. To enable the inventory visibility enhancement, in headquarters go to **POS visual profile** and enable **Show stock count and availability across stores**.
1. Run the **Registers (1090)** job to implement the changes in POS.

## Modern product details page

This feature introduces a modern, vertical, mobile‑first  product details page (PDP) rebuilt on React that brings every detail and action into one focused view so associates move faster without switching screens. The feature provides associates with a faster, more focused product experience by consolidating details and actions into a modern, mobile‑optimized vertical layout.

### Commerce version 10.0.47 feature enhancements

- **Sticky layout** – This enhancement keeps primary info and actions visible while scrolling.
- **Always-visible key actions** – This enhancement reduces by keeping **Add to sale** and other actions within reach.
- **Improved image gallery** – This enhancement offers clearer visuals and faster product recognition with better swipe interactions.
- **Dimension/quantity controls** – This enhancement streamlines variant and quantity selection for quicker, error‑free entry.
- **Accordion sections** – This enhancement organizes long product details into easy‑to‑scan sections for faster understanding.
- **Related products carousel** – This enhancement enables quick cross‑sell with add‑to‑sale actions available on each card.
- **Inventory preview** – This enhancement provides instant availability through a side drawer and supports choosing pickup or ship‑from‑store options.
- **Quantity discount** – This enhancement helps associates explain pricing benefits clearly.

To enable this feature and related enhancements, follow these steps:

1. In headquarters, go to the **Feature management** workspace (**System administration > Workspaces > Feature management**) and enable **Enable modernized product details page**.
1. To enable the inventory preview enhancement, go to **POS visual profile** and enable **Show nearby store inventory**.
1. To enable the quantity discount enhancement, go to **POS visual profile** and enable **Show quantity discount on modern PDP**.
1. Run the **Registers (1090)** job to implement the changes in POS.

## Modern transaction grid cart

This feature introduces a cleaner, more intuitive cart that surfaces discount opportunities and transparent pricing. The feature helps associates edit the cart more quickly, understand discount opportunities in context, and take action efficiently without navigating away from the transaction.

### Commerce version 10.0.47 feature enhancements

- **Quantity discount captions** – This enhancement display an inline alert when quantity‑based discounts are available, allowing associates to proactively inform shoppers about potential savings.
- **Threshold discount bar** – This enhancement displays a threshold discount message bar helping associates understand how close the cart is to the next discount tier.
- **Refreshed and extensible cart suggestions** – This enhancement presents modernized recommendation cards with clearer visuals, improved layouts, and an Add to sale button on each card. The default suggestions use curated recommendations maintained by headquarters users.

To enable this feature and related enhancements, follow these steps:

1. In headquarters, go to the **Feature management** workspace (**System administration > Workspaces > Feature management**) and enable **Enable modern transaction grid in POS transaction view**.
1. Go to **POS visual profile** and enable **Modern transaction grid**.
1. To enable the quantity discount captions enhancement, go to **POS visual profile** and enable **Show inline quantity discount messages**.
1. To enable the threshold discount bar enhancement, go to **POS visual profile** and enable **Show threshold discount bar**.
1. To enable the refreshed and extensible cart suggestions enhancement, go to **POS visual profile** and enable **Show product suggestions**.
1. Run the **Registers (1090)** job to implement the changes in POS.

### Commerce version 10.0.44 feature enhancements

#### Inline actions on transaction grid

Inline actions on the transaction grid are available for common line actions such as void product, return item, line discounts, price override, coupons, line comment, and change unit of measure. The order of display of the inline actions is by frequency of use for each register and is automatically ordered based on usage.

To launch the inline actions list, hover over a line on the transaction grid and select the 3 dots (**…**). On mobile and touch devices, inline actions can be accessed by long-pressing the line on the transaction grid, which provides a more intuitive mobile-optimized experience.

There's an option for a more extensive list of line actions. To access more line actions, you must enable the **Enable advanced inline actions** feature in the Commerce headquarters **Feature management workspace** (**System administration \> Workspaces \> Feature management**).

Inline actions remove the need for nested buttons to access line operations, allowing for a cluster-free transaction page with fewer buttons.

Extensibility and customization of the line actions that can be included is planned for future releases.

#### Inline quantity update on transaction grid

To change the item quantity, select or tap the quantity directly within the transaction grid. This action reduces the number of clicks and removes the need to navigate nested buttons, providing a quick and intuitive workflow.

#### Loyalty upsell prompt

The loyalty upsell prompt empowers store associates with the right information at the right time to inform customers about how close they're to reaching their next loyalty tier. This prompt can drive continued customer engagement to unlock new benefits, leading to increased average order value through strategic upselling.

Learn more in [Loyalty upsell prompt feature in POS](loyalty-upsell-prompt.md).

### Commerce version 10.0.43 feature enhancements

#### Toast notification framework

The new toast notification framework brings flexible, real-time alerts to Store Commerce. With full extensibility support, this framework can be extended to customize your own store notifications to meet your unique business needs. Use the Toast notification framework to quickly share policy updates with store associates, flag low-stock items for restocking, and alert staff when customers request assistance from in-store kiosks.

Learn more about the toast notification framework in [Offline reliability toast notifications in the Store Commerce app - Commerce](dev-itpro/retail-sdk/offline-reliability-toast-notifications.md).

### Commerce version 10.0.42 feature enhancements

#### Product images on transaction grid

Product images can now be displayed on the transaction grid.

Make sure to correctly set up and manage images for Store Commerce for this feature to work. Learn more in [Set up and manage images for Store Commerce](set-up-manage-images-retail-mpos.md).

To enable this feature in releases earlier than 10.0.45, contact Microsoft support.

To enable this feature in your environment in Commerce version 10.0.46 and later releases, follow these steps:

1. In headquarters, go to the **Feature management** workspace (**System administration \> Workspaces \> Feature management**).
1. Search for the **Enable Modern Transaction Grid in POS Transaction View** feature, and then select it.
1. In the right pane, select **Enable now**.
1. Search for the **Enable product images on modern transaction grid** feature, and then select it.
1. In the right pane, select **Enable now**.
1. Go to **POS visual profiles** (**Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> POS visual profiles**).
1. For each visual profile, set the **Modern transaction grid** option to **Yes**. This setting allows you to roll out changes to specific registers as needed.
1. Run the **Registers (1090)** job to implement the change in POS.

### Commerce version 10.0.40 feature enhancements

#### Payment capture improvements

Payment workflows in the POS application are redesigned for all payment methods, providing a consistent and enhanced user experience. Learn  more about the payment capture improvements in [Check out faster with optimized payment flows](dev-itpro/faster-checkout-pos.md). 

#### Streamlined workflow for adding items to a transaction from the product page

Two new workflows are introduced to handle situations where you add an item to the cart from the product description or search results page.

The first workflow shows a confirmation dialog that clearly indicates that the item was successfully added to the cart. You can then continue to browse for products. This workflow is suited to assisted-selling scenarios where store associates browse and add many items to the cart.

The second workflow lets you immediately go to the transaction page after you add an item to the cart so that you can continue with the transaction process. No confirmation dialog is shown.

You can select between the two workflows via a configuration option in the POS visual profile in Commerce headquarters.

To bypass the confirmation dialog and always go to transaction page after you add an item, in headquarters go to **POS visual profiles**. In the **General** section, in the **Product details page** subsection, set the **Bypass Item added dialog** option to **Yes**. To show the confirmation dialog box, set the **Bypass Item added dialog** option to **No**.

> [!NOTE]
> After every configuration change made in headquarters, you must run the **Registers (1090)** job to realize the change in POS.

#### Configure the display of search results

In the POS visual profile in headquarters, you can configure the phone view port default view for the display of search results for products, customers, and categories. Previously, the list view was the default view. Search results in the phone view port can be shown in a card view by default to allow for easy product browsing. This update will be made available for other view ports in future releases.

To set your preference for the default search view, in headquarters, go to **POS visual profiles**. In the **General** section, in the **Search view** subsection, set the **Default view** field to **List view** or **Card view**.

> [!NOTE]
> After every configuration change made in headquarters, you must run the **Registers (1090)** job to realize the change in POS.

#### Reset button grids at the end of a transaction

With this feature, the default button grid that is assigned to the first tab is restored when a transaction is completed, suspended, or voided. This feature helps reduce confusion and the number of clicks that are required when a store associate handles multiple transactions.

#### Reprint receipts from a journal

To reduce the number of clicks that are required to reprint receipts, the **Print receipt** button is available at the bottom of the **Show journal** screen. To reprint receipts, select the journal and **Print receipt** in a single click.

### Commerce version 10.0.39 feature enhancements

#### Enhanced date picker

To enable intuitive interactions, the date picker in the Store Commerce app is updated to a React control.

#### Persist the zoom level

Store associates can persist their zoom settings, eliminating the need to readjust the display each time the application is opened. This feature is especially useful for kiosk mode users without a keyboard and mouse.

[!INCLUDE[footer-include](../includes/footer-banner.md)]









