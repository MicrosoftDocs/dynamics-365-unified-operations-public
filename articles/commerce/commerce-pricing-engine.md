---
# required metadata

title: Commerce pricing engine
description: This article explains the core capabilities in Commerce pricing engine.
author: boycez
ms.date: 07/14/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail, Commerce
ms.author: boycez
ms.search.validFrom: 2022-07-14
ms.dyn365.ops.version: Application update 10.0.29

---

# Commerce pricing engine

[!include [banner](includes/banner.md)]

Pricing calculation across Commerce channels is empowered by a unified Commerce pricing engine. The engine in Commerce headquarters component supports call center  orders, and the engine deployed in Commerce scale unit (CSU) supports retail store and online store orders. This article explains various core capabilities in Commerce pricing engine.

## Streamlined discount data schema

The ability to find and calculate applicable discounts in a performant manner is a critical factor that affects a retailer's overall business efficiency. In **10.0.23** release, Commerce pricing engine introduces a streamlined discount data schema to achieve faster discount lookup and performant pricing calculation at runtime. 

To use this feature, follow these steps in Commerce headquarters.

1. Go to **Retail and Commerce \> Pricing and discounts** and select **Process commerce discounts**.
1. In the dialog box that appears, schedule the batch job to run on a recurrent basis.
1. Go to **Workspaces \> Feature management**, search for and enable the **Improve discount computation performance by using flattened discount tables** feature.
4.	Run the **1020** (**Prices and discounts**) and **1070** (**Channel configuration**) distribution schedule jobs.

When the feature is enabled, discount data configured in Commerce headquarters is denormalized before being sent to channel databases. The publishing of flattened discount data is triggered when a discount is enabled.

> [!NOTE]
> Make sure that you test this feature extensively before you enable it in production environments, especially if you have customizations in the Commerce pricing engine.

## Price lock and recalculation

When a customer order is placed, the customer commits to an amount. This amount includes prices and might also include discounts. A customer who places an order and then contacts the call center later to change that order (for example, to add another item) will have specific expectation about the application of discounts. Even if the promotions on the existing order lines have expired, the customer will expect the discounts that were originally applied to those lines to remain in effect. However, if no discount was in effect when the order was originally placed, but a discount has gone into effect since then, the customer will expect the new discount to be applied to the changed order. Otherwise, the customer might just cancel the existing order and then create a new order where the new discount is applied. As this scenario shows, prices and discounts that customers have committed to must be preserved. At the same time, POS and call center users must have the flexibility to recalculate prices and discounts for sales order lines as required.

In Commerce, after order capture is completed for an order placed from any channel, the prices and discounts of the existing sales lines are considered **locked**, and a **Price locked** property is automatically enabled for all  existing sales lines. If the order is further edited (for example, recalled and edited in POS or call center), the Commerce pricing engine by default excludes those locked sales lines from price recalculation. 

To recalculate the prices and discounts of existing sales lines:

- The POS user can use the **Calculate total** function in POS application to remove price lock from all existing sales lines and trigger on-demand price recalculation based on the latest price and discount configuration. POS users can’t unlock prices for selected sales lines.
- The call center user can manually disable the **Price locked** property by clearing the checkbox for one or more selected sales lines and then use **Recalculate** function to recalculate prices and discounts for those unlocked sales lines.
- The call center user can also disable the **Price locked** property for sales lines in bulk by selecting **Remove price lock** in the **Calculate** group on the **Sell** tab on the Action Pane of the **Sales order** page. In this case, the price lock is removed from all sales lines except lines that are non-editable (in other words, lines that have a status of **Partially invoiced** or **Invoiced**). Then, after the changes to the order are completed and submitted, the price lock is reapplied to all the sales lines.

With price lock, the setup of trade agreement evaluation is ignored in the pricing workflows. In other words, the trade agreement evaluation dialog doesn’t show the price related section. This behavior occurs because both the trade agreement evaluation setup and price lock have a similar purpose: to prevent unintentional price changes. However, the user experience for trade agreement evaluation doesn’t scale well for large orders where users must select one or more order lines for repricing.

To apply manual discount to a locked sales line, the call center user must firstly disable the **Price locked** property of the sales line.

> [!NOTE]
> In Commerce version earlier than **10.0.21**, price lock is only enabled for POS orders and any changes to the call center order lines cause prices and discounts to be recalculated immediately. In Commerce version **10.0.21** to **10.0.28**, you need to enable the **Prevent unintentional price calculation for commerce orders** feature in **Feature management** workspace to enable the price lock behavior in call center channel.

> [!IMPORTANT]
> 

## Delayed price and discount calculation

Commerce pricing engine supports multiline discounts (such as quantity discount, threshold discount, mix and match discount) that are applied when multiple qualified items exist in a sales order or sales quotation. Whenever a new line is added to an order, the pricing engine by default evaluates the whole order to determine whether any multiline discount can be applied. Because of this recalculation, the addition of new lines can affect performance as the sales order size grows.

Business-to-business (B2B) companies and some business-to-consumer (B2C) companies often have large order size. Therefore, it can be time consuming to wait for the pricing engine to recalculate after each item is added to the order. Moreover, for large orders, it usually isn't very important that the exact price and discount be shown every time that an item is added. It's more important that users be able to add items quickly. The capability to delay exact price and discount calculation until a user requests it or an order is finalized can significantly improve performance. It can also reduce the time that is required to finish placing an order.

To enable delayed price and discount calculation for POS, follow these steps in Commerce headquarters.

1. Go to the functionality profile that is associated with the retail store.
1. On the **Amount** FastTab, enable the **Manually calculate multiple item discounts** configuration.
1. For the registers where the delayed calculation should be enabled, add a button for the **Calculate total** operation to the desired button grid.
1. Run the **1070** (**Channel configuration**) and **1090** (**Registers**) distribution schedule jobs.

Now, when items are added to a transaction in POS, multiline discounts aren't calculated unless the cashier selects the **Calculate total** button. After **Calculate total** is selected for a transaction, multiline discounts will always be calculated for it. The cashier won't have to select the button again, even if additional items are added to the cart. The system won't allow the cashier to capture payment until **Calculate total** is executed.

Delayed price and discount calculation for call center is available in Commerce version **10.0.22** release and later. To enable this capability, follow these steps in Commerce headquarters.

1. Go to **Commerce parameters \> Prices and discounts**.
1. In the **Miscellaneous** section, enable the **Manually calculate multi-line prices and discounts** configuration.

> [!NOTE]
> For Commerce version earlier than **10.0.29**, you need to enable **Prevent unintentional price calculation for commerce order** feature in **Feature management** workspace to see the above configuration.

Now, when a sales order or sales quotation is created or edited in the call center, the exact price and discount calculation for it will be delayed. The pricing engine will consider only the sales line that is being added or edited, and will ignore all other sales lines. The net amount for an item includes the price calculation and simple discounts. However, mix and match, threshold, and quantity discounts won't be applied. Call center users who want to view the exact price, including all discounts, can select one of three buttons: **Recalculate**, **Totals**, or **Complete**.

For call center orders, the system shows a warning message to remind the user that they must select the **Recalculate**, **Totals**, or **Complete** button for the exact price and discount calculation to be done. For orders where the **Complete** button is available, there is no way for the call center user to omit the exact price and discount calculation, because they must select **Complete** to complete the order capture. For orders where the **Complete** button isn't available, there is no action that indicates completion of the order capture. Therefore, the call center user is responsible for selecting either **Recalculate** or **Totals** before they complete the order capture.

## Commerce pricing engine vs. Supply Chain Management pricing engine

- In general, Commerce pricing engine is designed to work with Commerce entities (for example, orders created in Commerce channels) only. We recommend that you don't edit sales orders and quotations in POS that are created by a non-Commerce channel. Those orders and quotes don't use the Commerce pricing engine, so if they're edited in POS, the Commerce pricing engine will re-price them.
- The standard Supply Chain Management pricing engine supports the pricing calculation based on the **Requested ship date** and **Requested receipt date** along with the today's date. However, Commerce pricing engine currently only supports today's date. The reason is that for B2C scenarios customers do not expect the requested delivery date to affect the item price. In some cases, retailers have both B2B and B2C operations. For B2B operations it is common to change prices based on the delivery dates. These retailers can use Supply Chain Management pricing for their B2B business and Commerce pricing for their B2C business. Commerce pricing kicks in only if the application user is added as a call center user, so the retailers can assign certain users who will work with the Supply Chain Management pricing and assign a few that will work with the Commerce pricing, that is, these users should be added as a call center users.
- Commerce pricing engine does not support vendor discount pass-through.
- The generic currency feature is not supported in Commerce pricing engine. For example, even if a trade agreement has the **Include generic currency** toggle turned on, still this trade agreement will only be considered valid for the currency defined on the trade agreement.

> [!NOTE]
> In Commerce version earlier than **10.0.26**, trade agreement sales price defined on storage dimensons is not fully supported in Commerce pricing engine. If site is specified but warehouse is not specified on a trade agreement, Commerce pricing engine ignores the site and considers the trade agreement applicable to all sites. In Commerce version **10.0.26** and later, you can enable **Honor site and warehouse setting on trade agreement in Commerce pricing engine** feature in **Feature management** workspace to upgrade Commerce pricing engine capability to fully support the site and warehouse setting on trade agreement sales price.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
