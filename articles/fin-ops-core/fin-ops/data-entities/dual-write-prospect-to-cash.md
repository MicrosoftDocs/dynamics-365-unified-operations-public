---
title: Prospect-to-cash in dual-write
description: Learn about prospect-to-cash in dual-write, including outlines on prerequisites, mapping setup, and sales quotations.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/26/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Prospect-to-cash in dual-write

[!include [banner](../../../finance/includes/banner.md)]

In Microsoft Dynamics 365 apps, the prospect-to-cash process occurs through quotations or order processing workflows, and the financials are reconciled and recognized. Integration of prospect-to-cash with dual-write creates a workflow that takes a quotation and an order that originate in either Dynamics 365 Sales or Dynamics 365 Supply Chain Management, and makes the quotation and order available in both apps.

In the app interfaces, you can access the processing statuses and invoice information in real time. Therefore, you can more easily manage functions such as product stocking, inventory handling, and fulfillment in Supply Chain Management, without having to re-create the quotations and orders.

![Dual-write dataflow in quote-to-cash.](../../dev-itpro/data-entities/dual-write/media/dual-write-prospect-to-cash[1].png)

For information about customer and contact integration, see [Integrated customer master](../../dev-itpro/data-entities/dual-write/customer-mapping.md). For information about product integration, see [Unified product experience](../../dev-itpro/data-entities/dual-write/product-mapping.md).

> [!NOTE]
> In Supply Chain Management version 10.0.39 and later, accounts of the *Customer* and *Prospect* types are supported. This support enables an account qualification process where the account record is created and qualified first as a prospect and then as a customer. This process includes a process for automatically converting a prospect to a customer account in an integrated quotation scenario. For details about how to set up and enable this capability, see [Enable and configure prospect integration in prospect-to-cash with Dynamics 365 Sales](prospects-in-prospect-to-cash-enable.md).

## Prerequisites and mapping setup

Before you can sync sales quotations, you must update the following settings.

### Setup in Sales

In Sales, go to **Settings \> Administration \> System settings \> Sales**, and make sure that the following settings are used:

- The **Use system pricing calculation** system option is set to **Yes**.
- The **Discount calculation method** column is set to **Line item**.

> [!NOTE]
> An improved approach to pricing for sales quotations and sales orders is also available. In this approach, Supply Chain Management becomes the price master, and no price-related calculations are done in Sales. Additionally, when a sales quotation or sales order and a line are created and updated in Sales, line details, monetary line values, and totals can immediately be updated and synced between systems. For details about how to set up and enable these capabilities, see [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md) and [Enable and configure seamless sync with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-seamless-sync.md).

### Sites and warehouses

In Supply Chain Management, the **Site** and **warehouse** columns are required for quotation lines and order lines. If you set the site and warehouse in the default order settings, those columns will automatically be set when you add a product to a quotation line or an order line.

### Number sequences for quotations and orders

The number sequences for Supply Chain Management and Sales aren't connected when quotations and orders are created and synced in Sales and Supply Chain Management. If a sales order that is created in Sales is synced to Supply Chain Management, it has the same sales order number in Supply Chain Management. To help ensure that the sales order number isn't duplicated, you must use different number sequence systems in the two apps.

For example, the number sequence in Supply Chain Management is **1, 2, 3, 4, 5, ...**, and the number sequence in Sales is **100, 99, 98, ...**. If you create 100 sales orders in Sales, an order number will eventually be generated that already exists in Supply Chain Management. In other words, the two number sequences will eventually overlap as sales orders are created in Supply Chain Management and Sales. Instead, you might use a number sequence such as **F1, F2, F3, ...** in Supply Chain Management and a number sequence such as **C1, C2, C3, ...** in Sales. These number sequences will never produce duplicate sales order numbers.

## Sales quotations

Sales quotations can be created in either Sales or Supply Chain Management.

> [!NOTE]
> In Supply Chain Management version 10.0.39 and later, accounts of the *Customer* and *Prospect* types are supported. This support enables an account qualification process where the account record is created and qualified first as a prospect and then as a customer. This process includes a process for automatically converting a prospect to a customer account in an integrated quotation scenario. For details about how to set up and enable this capability, see [Enable and configure prospect integration in prospect-to-cash with Dynamics 365 Sales](prospects-in-prospect-to-cash-enable.md).

If you create a quotation in Sales, it's synced to Supply Chain Management in real time. Likewise, if you create a quotation in Supply Chain Management, it's synced to Sales in real time. Note the following points:

- You can add a discount to the product on the quotation. In this case, the discount will be synced to Supply Chain Management. The **Discount**, **Charges**, and **Tax** columns on the header are controlled by a setup in Supply Chain Management. This setup doesn't support integration mapping. Instead, the **Price**, **Discount**, **Charge**, and **Tax** columns are maintained and handled in Supply Chain Management.
- The **Discount %**, **Discount**, and **Freight Amount** columns on the sales quotation header are read-only columns.
- The **Freight terms**, **Delivery terms**, **Shipping method**, and **Delivery mode** columns aren't part of the default mappings. To map these columns, you must set up a value mapping that is specific to the data in the organizations that the table is synced between.

> [!NOTE]
> In Supply Chain Management, the sales quotation lifecycle can be integrated between Sales and Supply Chain Management. For details about how to set up and enable this integration, see [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md). When this functionality is enabled, state and status transitions throughout the lifecycle of a sales quotation are mapped between the two apps, and a policy of ownership is applied to control the actions that are available for a sales quotation when you work in Sales or Supply Chain Management. There's also related **Make Supply Chain Management price master** functionality that changes how calculations for sales quotations and sales orders are done in Sales. For more information about both functionalities, see [Add efficiency in Quote to Cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-concept.md).

If you are also using the Field Service solution, make sure to re-enable the **Quote Line Quick Create** parameter. Re-enabling the parameter lets you continue creating quote lines using the quick create function.

1. Navigate to your Dynamics 365 Sales application.
2. Select the settings icon in the top navigation bar.
3. Select **Advanced Settings**.
4. Choose the **Customize the System** option.
5. Select the **Quote Line** menu item.
6. Go to the **Data Services** section and select the **Allow quick create** checkbox.

## Sales orders

Sales orders can be created in either Sales or Supply Chain Management. If you create a sales order in Sales, it's synced to Supply Chain Management in real time. Likewise, if you create a sales order in Supply Chain Management, it's synced to Sales in real time. Note the following points:

- Write-in products on Dynamics 365 Sales will appear as product categories in Dynamics 365 Supply Chain Management.
- Discount calculation and rounding:

    - The discount calculation model in Sales differs from the discount calculation model in Supply Chain Management. In Supply Chain Management, the final discount amount on a sales line can be the result of a combination of discount amounts and discount percentages. If this final discount amount is divided by the quantity on the line, rounding can occur. However, this rounding isn't considered if a rounded per-unit discount amount is synced to Sales. To help ensure that the full discount amount from a sales line in Supply Chain Management is correctly synced to Sales, the full amount must be synced without being divided by the line quantity. Therefore, you must define the discount calculation method as **Line item** in Sales.
    - When a sales order line is synced from Sales to Supply Chain Management, the full line discount amount is used. Because Supply Chain Management has no column that can store the full discount amount for a line, the amount is divided by the quantity and stored in the **Line discount** column. Any rounding that occurs during this division is stored in the **Sales charges** column on the sales line.

### Example: Synchronization from Sales to Supply Chain Management

You have the following sales order:

- **Sales:** Quantity = 3, per-line discount = $10.00
- **Supply Chain Management:** Quantity = 3, line discount amount = $3.33, sales charge = –$0.01

If you sync from Supply Chain Management to Sales, you get the following result:

- **Supply Chain Management:** Quantity = 3, line discount amount = $3.33, sales charge = –$0.01
- **Sales:** Quantity = 3, per-line discount = (3 × $3.33) + $0.01 = $10.00

> [!NOTE]
> An improved approach to pricing for sales quotations and sales orders is also available. In this approach, Supply Chain Management becomes the price master, and no price-related calculations are done in Sales. Additionally, when a sales quotation or sales order and a line are created and updated in Sales, line details, monetary line values, and totals can immediately be updated and synced between systems. For details about how to set up and enable these capabilities, see [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md) and [Enable and configure seamless sync with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-seamless-sync.md).

## Dual-write solution for Sales

New columns have been added to the **Order** table and appear on the page. Most of these columns appear on the **Integration** tab in Sales. To learn more about how the status columns are mapped, see [Set up the mapping for sales order status columns](../../dev-itpro/data-entities/dual-write/sales-status-map.md).

- The **Create Invoice** and **Cancel Order** buttons on the **Sales order** page are hidden in Sales.
- The **Sales order status** value will remain **Active** to help ensure that changes from Supply Chain Management can flow to the sales order in Sales. To control this behavior, set the default **Statecode \[Status\]** value to **Active**.

> [!NOTE]
> The status integration of sales orders differs, depending on whether you use the *CDS Sales order headers* (*salesorders*) entity or the *Dynamics 365 Sales order headers* (*salesorders*) entity. For more information about the differences, see [Set up the mapping for sales order status columns](../../dev-itpro/data-entities/dual-write/sales-status-map.md).

## Invoices

Sales invoices are created in Supply Chain Management and synced to Sales. Note the following points:

- An **Invoice number** column has been added to the **Invoice** table and appears on the page.
- The **Create invoice** button on the **Sales order** page is hidden, because invoices will be created in Supply Chain Management and synced to Sales. The **Invoice** page can't be edited, because invoices will be synced from Supply Chain Management.
- The **Sales order status** value is automatically changed to **Invoiced** when the related invoice from Supply Chain Management has been synced to Sales. Additionally, the owner of the sales order that the invoice was created from is assigned as the owner of the invoice. Therefore, the owner of the sales order can view the invoice.
- The **Freight terms**, **Delivery terms**, and **Delivery mode** columns aren't included in the default mappings. To map these columns, you must set up a value mapping that is specific to the data in the organizations that the table is synced between.

## Templates

Prospect-to-cash includes a collection of core table maps that work together during data interaction, as shown in the following table.

| Finance and operations apps | Customer engagement apps | Description |
|---|---|---|
| [All products](../../dev-itpro/data-entities/dual-write/mapping-reference.md#138) | msdyn\_globalproducts | |
| [Customers V3](../../dev-itpro/data-entities/dual-write/mapping-reference.md#101) | accounts | |
| [Customers V3](../../dev-itpro/data-entities/dual-write/mapping-reference.md#116) | contacts | |
| [Contacts V2](../../dev-itpro/data-entities/dual-write/mapping-reference.md#221) | msdyn\_contactforparties | |
| [CDS sales order headers](../../dev-itpro/data-entities/dual-write/mapping-reference.md#217) | salesorders | |
| [CDS sales order lines](../../dev-itpro/data-entities/dual-write/mapping-reference.md#216) | salesorderdetails | |
| [CDS sales quotation header](../../dev-itpro/data-entities/dual-write/mapping-reference.md#215) | quotes | |
| [CDS sales quotation lines](../../dev-itpro/data-entities/dual-write/mapping-reference.md#214) | quotedetails | |
| [Released products V2](../../dev-itpro/data-entities/dual-write/mapping-reference.md#189) | msdyn\_sharedproductdetails | |
| [Sales invoice headers V2](../../dev-itpro/data-entities/dual-write/mapping-reference.md#118) | invoices | The Sales invoice headers V2 table in the finance and operations app contains invoices for sales orders and free text invoices. A filter that's applied in Dataverse for dual-write will filter out any free text invoice documents. |
| [Sales invoice lines V2](../../dev-itpro/data-entities/dual-write/mapping-reference.md#117) | invoicedetails | |
| [Sales order origin codes](../../dev-itpro/data-entities/dual-write/mapping-reference.md#186) | msdyn\_salesorderorigins | |
| [Dynamics 365 Sales order headers](../../dev-itpro/data-entities/dual-write/mapping-reference.md#238) | salesorders | This entity is introduced through the *Add efficiency in Quote to Cash with Dynamics 365 Sales* feature. |
| [Dynamics 365 Sales order lines](../../dev-itpro/data-entities/dual-write/mapping-reference.md#239) | salesorderdetails | This entity is introduced through the *Add efficiency in Quote to Cash with Dynamics 365 Sales* feature. |
| [Dynamics 365 Sales quotation header](../../dev-itpro/data-entities/dual-write/mapping-reference.md#240) | quotes | This entity is introduced through the *Add efficiency in Quote to Cash with Dynamics 365 Sales* feature. |
| [Dynamics 365 Sales quotation lines](../../dev-itpro/data-entities/dual-write/mapping-reference.md#241) | quotedetails | This entity is introduced through the *Add efficiency in Quote to Cash with Dynamics 365 Sales* feature. |
| [Dynamics 365 Sales feature management states](../../dev-itpro/data-entities/dual-write/mapping-reference.md#237) | msdyn\_supplychainfeaturestate | This entity is introduced through the *Add efficiency in Quote to Cash with Dynamics 365 Sales* feature. |
| Dynamics 365 Sales Prospect (accounts) | | This entity is introduced through the *Enable prospect in prospect-to-cash with Dynamics 365 Sales* feature (available in Supply Chain Management 10.0.39 and later). |
| Dynamics 365 Sales Prospect (contacts) | | This entity is introduced through the *Enable prospect in prospect-to-cash with Dynamics 365 Sales* feature (available in Supply Chain Management 10.0.39 and later). |
| Dynamics 365 Sales feature parameters | | This entity is introduced through the *Enable prospect in prospect-to-cash with Dynamics 365 Sales* feature (available in Supply Chain Management 10.0.39 and later). |

<!--KFM: Add links for the last three rows when the mapping reference page is updated by HenrikJ. Also add the column details for Customer engagement apps from the mapping reference. -->

For information about price lists, see [Unified product experience](../../dev-itpro/data-entities/dual-write/product-mapping.md).

> [!NOTE]
> For more information about the entities that are introduced in Supply Chain Management version 10.0.39 (*Dynamics 365 Sales Prospect* (*accounts*), *Dynamics 365 Sales Prospect* (*contacts*), and *Dynamics 365 Sales feature parameters*), see [Enable and configure prospect integration in prospect-to-cash with Dynamics 365 Sales](prospects-in-prospect-to-cash-enable.md).

## Limitations

The following limitations apply:

- Return orders aren't supported. A return order is a sales order that has a sales order type of **Returned order**.
- Financial dimensions must be set for the master data, for example, customer and vendor. When a customer is added to a quotation or sales order, the financial dimensions associated with the customer record flow to the order automatically. Currently dual-write does not include financial dimensions data for master data.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
