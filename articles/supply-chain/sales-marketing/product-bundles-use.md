---
title: Sell and allocate product bundles
description: Learn how to work with product bundles on sales orders and related documents, and explains how bundle item prices are allocated to each bundle component.
author: adpattanaik
ms.author: adpattanaik
ms.topic: how-to
ms.date: 04/29/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: Customer
---

# Sell and allocate product bundles

[!include [banner](../includes/banner.md)]

This article describes how to work with product bundles on sales orders and related documents, and explains how bundle item prices are allocated to each bundle component.

A product bundle consists of a parent item (product bundle item) and multiple component items. The parent item is entered on a sales order line. Therefore, order entry is more efficient. However, the parent item is then exploded into the component items. Internal documents such as picking lists and packing slips list the component items. However, external documents such as sales order confirmations and sales invoices show only the parent item.

> [!NOTE]
> The product bundle feature isn't supported in Microsoft Dynamics 365 Commerce channels, such as online, point of sale (POS), and call centers. It also isn't supported by the prospect-to-cash solution for Dynamics 365 Supply Chain Management and Dynamics 365 Sales. Items that are configured as product bundles shouldn't be added to orders or transactions that are created in Commerce channels or in the prospect-to-cash solution.

## How bundle items are set up and handled

You use the bill of materials (BOM) functionality to set up bundles. For information about how to set up a bundle item, see [Enable and set up product bundles](product-bundles-setup.md).

Parent items that are flagged as product bundles are handled differently than other BOM items. Here's a list of the differences:

- You explode product bundles that are included on a sales order by confirming the order. Open the sales order, and then, on the Action Pane, on the **Sell** tab, select **Confirm sales order**. Never explode a product bundle item from the **Sales order lines** FastTab (by selecting **Sales order line \> Explode \> BOM lines** on the toolbar). Otherwise, the system treats the item as a BOM instead of a product bundle.
- A sales order that contains a product bundle item must be confirmed before the picking list, packing slip, or invoice is created.
- When a product bundle is exploded through sales order confirmation, the parent item is canceled, and its unit price and discounts are allocated to the component items of the bundle.
- The sum of the component items must always equal the price of the parent item. Therefore, there are limitations on the fields that can be updated or changed for component items. For example, the unit price can't be manually changed. It also can't be indirectly changed. To help prevent scenarios such as searching and applying a new price, inventory dimensions can't be changed on the component items.
- When external-facing documents such as sales order confirmations or invoices are printed, only the parent item is shown on the printed document. The component items aren't shown.

## Example of a sales order that includes a product bundle

You set up a product bundle in the following way:

- **Parent item:** *Laptop bundle*
- **Component item:** 1 pcs. of item *1000* (the laptop itself), which has a base sales price of $1,900.00
- **Component item:** 1 pcs. of item *S0021* (insurance), which has a base sales price of $150.00
- **Component item:** 1 pcs. of item *Support* (support), which has a base sales price of $500.00

The base sales price of each component item is an essential part of the component setup. It's set on the **Sell** FastTab of the item. The base sales price is used to calculate the allocation factor when the parent item's unit price is allocated to the component items. Trade agreement sale prices are never used for this purpose.

Next, you have a sales order that includes a single sales order line for the *Laptop bundle* item. The default unit price for the parent item can be taken from numerous places, such as the trade agreement or the base sales price. For this example, $2,300 was manually entered as the unit price on the sales order, as shown in the following illustration.

[<img src="media/product-bundle-01.png" alt="Sales order where the Laptop bundle item has a manually entered unit price." title="Sales order where the Laptop bundle item has a manually entered unit price" width="720" />](media/product-bundle-01.png#lightbox)

### Confirm the order to explode the product bundle

Because the sales order includes a product bundle item, it must be confirmed. The **Confirmation sales order** dialog box shows the components of the product bundle, as shown in the following illustration.

[<img src="media/product-bundle-02.png" alt="Confirm sales order dialog box that shows the component items." title="Confirm sales order dialog box that shows the component items" width="720" />](media/product-bundle-02.png#lightbox)

However, because the printed confirmation report is the external-facing document for the customer, it shows only the parent item of the product bundle, as shown in the following illustration.

[<img src="media/product-bundle-03.png" alt="Printed confirmation report that shows only the parent item." title="Printed confirmation report that shows only the parent item" width="720" />](media/product-bundle-03.png#lightbox)

After the sales order is confirmed, the parent item is still shown on the sales order, but its status is changed to *Canceled*. Additionally, the net amount is tracked in the **Bundle net amount** field. This amount is required to print the invoice, because the invoice shows the parent item, not the component items.

### Allocate prices to component items

The sum of the component items must equal the **Bundle net amount** value of the parent item, because that value is the amount that's presented to the customer when the invoice is created. To ensure that the invoice matches the amounts that are posted to the general ledger, edits to the component items are limited. For example, the site and warehouse can't be changed, because those changes might trigger a price change based on a trade agreement.

Because the sum of the components doesn't match the bundle price entered on the sales order in this example, the unit prices are recalculated and allocated to the components in the following way:

- **Product bundle price entered on the sales order:** $2,300
- **Total base sales prices from components:** $1,900 + $500 + $150 = $2,550
- **Allocated price for component 1:** $2,300 × (1,900 ÷ 2,550) = $1,713.73
- **Allocated price for component 2:** $2,300 × (500 ÷ 2,550) = $450.98
- **Allocated price for component 3:** $2,300 × (150 ÷ 2,550) = $135.29

The sum of the components must equal $2,300, and it does ($1,713.73 + $450.98 + $135.29 = $2,300).

If changes are required for all component items, the parent item can be removed. In this case, the component items are also removed. The parent item can then be added again, and the required edits can be completed before the sales order is confirmed.

### Pick, pack, and ship the order

While the sales order is being picked and packed, only the components of the product bundle are shown. However, the packing slip and invoice must include a full product bundle. Otherwise, they can't be posted. For example, the dialog box shows three component items. If you try to delete one of them, you receive an error message that states that all products in the product bundle must be shipped before they can be invoiced.

Each product bundle must be shipped and invoiced as a full bundle. For example, if you change the quantity of component item *1000* to *4*, but you leave the quantity of the other component items set to *5*, the packing slip and invoice can't be posted.

A partial amount can be shipped and invoiced only if the quantity is reduced for all components of the bundle. For example, a quantity of *5* of the *Laptop bundle* item is entered on a sales order. After the sales order is confirmed, the three component items are shown on the sales order, and the quantity of each is *5*. By default, the quantity of each component is set to *5* during shipping and invoicing. However, you can adjust the quantity to *3* for all three component items. In this case, three full product bundles will be shipped and invoiced. The remaining two product bundle items (a quantity of *2* of each of the three component items) can be shipped and invoiced later.

### Invoice the sales order

The final step is to invoice the sales order. As for the sales order, the invoice dialog box shows the component items, whereas the printed invoice shows only the parent item.

The invoice journal that's created after posting occurs doesn't include the parent item from the product bundle, because that item has a status of *Canceled*.

The invoice journal must not include the parent item from the product bundle, because any processes that are performed after the invoice is posted are based on that invoice journal. For example, if you create a credit note from the **Sell** tab of the Action Pane, the credit note that's created will include the component items but not the parent item.

## <a name="bundles-journals"></a>Product bundles in journals

The *Product bundles in journals* feature extends the *Product bundle* feature. (Learn more in [Enable and set up product bundles](product-bundles-setup.md).) It enables the system to preserve detailed product bundle information in its database. Therefore, you can reprint original sales order confirmations and invoices even after the related sales order is deleted or archived and purged. This feature also improves the ability to exchange order confirmations and invoices electronically. Because product bundles are now represented in journals, you can electronically exchange order confirmations and invoices that include product bundles.

This section describes the changes that the *Product bundles in journals* feature introduces. These changes build on the features that were described earlier in this article.

### Changes in sales confirmation journals

After a sales order is confirmed, the parent item is still shown on the sales order, but its status is changed to *Canceled*. An additional status field, **Bundle line status**, represents the overall status across the components part of the product bundle. Use it to identify the overall status of the product bundle and its components on the sales order lines. A symbol in the **Type** column helps you identify which order line is a product bundle and which is a component. The net amount is tracked in the **Bundle net amount** field.

Sales confirmation journal lines now contain information that's related to product bundles. This information is presented in the **Bundle parent** column. For each component journal line that's part of a bundle, the **Bundle parent** column shows the lot ID and name of the bundle. Use the **Group by** option on the **Bundle parent** column to see which components belong to which bundle.

Product bundle information on the journal lines makes it possible to reprint sales confirmations correctly even after the sales order is deleted.

### Changes in packing slip journals

Sales packing slip journal lines now contain information that's related to product bundles. This information is presented in the **Bundle parent** column. For each component journal line that's part of a bundle, the **Bundle parent** column field shows the lot ID and name of the bundle. Use the **Group by** option on the **Bundle parent** column to see which components belong to which bundle.

Product bundle information on the journal lines makes it possible to reprint sales packing slips correctly even after the sales order is deleted.

### Changes in sales invoice journals

Sales invoice journal lines now contain information that's related to product bundles. This information is presented in the **Bundle parent** column. For each component journal line that's part of a bundle, the **Bundle parent** column field shows the lot ID and name of the bundle. Use the **Group by** option on the **Bundle parent** column to see which components belong to which bundle.

Product bundle information on the journal lines makes it possible to reprint sales invoices correctly even after the sales order is deleted.

### Entity support for exporting sales confirmations and invoiced with bundle information

The following data entities support bundle information on journal lines for sales confirmations and sales invoices. These entities let you send sales order confirmations and sales invoices that include product bundle lines to your customers.

- **Sales order confirmation bundle parent lines** – This entity includes both root and intermediate bundle parent lines. To set criteria that define which lines are included, apply a filter on the *journal line type*. Select *bundle parent* to include only the bundle parent.
- **Sales order confirmation lines including bundle component** – This entity includes standard sales order conformation transactions and bundle components, if they're available.​ To set criteria that define which lines are included, apply a filter on the *journal line type*. Select *standard* to exclude any components.
- **Sales invoice bundle parent lines** – This entity includes both root and intermediate bundle parent lines. To set criteria that define which lines are included, apply a filter on the *journal line type*. Select *bundle parent* to include only the bundle parent.
- **Sales invoice lines including bundle component** – This entity includes standard invoice transactions and bundle components, if they're available.​ To set criteria that define which lines are included, apply a filter on the *journal line type*. Select *standard* to exclude any components.

The data that's exported through these entities resembles the data that's printed on sales confirmations and sales invoices.

## Important limitations

The following important limitations apply when you use product bundle items:

- The product bundle feature isn't supported in Commerce channels, such as online, point of sale (POS), and call centers. It also isn't supported by the prospect-to-cash solution for Supply Chain Management and Sales. Items that are configured as product bundles shouldn't be added to orders or transactions that are created in Commerce channels or in the prospect-to-cash solution.
- Product bundle items aren't supported in intercompany orders. In a three-legged scenario, product bundle items aren't exploded during sales order confirmation on the original sales order. In a two-legged scenario, the sales order confirmation process is blocked.
- Product bundle items aren't supported in direct deliveries.
- Product bundle items aren't supported in delivery schedules.
- The delivery type of the sales order line for bundle components is always *Stock*, regardless of the direct delivery setting on the released product.
- Unless you're using the *(Preview) Product bundles in journals* feature, you can reprint an invoice or sales order confirmation only if the related sales order that includes the product bundle order lines still exists. If the sales order lines were deleted, the reprinted invoices and sales order confirmations include the component items but not the parent item.
- Miscellaneous charges that are added to a parent item line aren't allocated to the component item lines when the parent item is exploded.

## Related information

- [Product bundles overview](product-bundles-overview.md)
- [Enable and set up product bundles](product-bundles-setup.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
