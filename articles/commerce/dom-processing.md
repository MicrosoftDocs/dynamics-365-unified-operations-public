---
title: DOM processing
description: Learn how distributed order management (DOM) processes sales orders in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 09/02/2026
ms.topic: how-to
ms.custom: 
  - bap-template
ms.author: wenxyang
ms.reviewer: mirao
ms.search.region: Global
ms.search.validFrom: 2023-11-07
---

# DOM processing

[!INCLUDE [banner](includes/banner.md)]

This article describes how distributed order management (DOM) processes sales orders in Microsoft Dynamics 365 Commerce.

## Configure DOM processor batch job

DOM runs only in a batch job.

To configure the DOM processor batch job for DOM runs, follow these steps:

1. Go to **Retail and Commerce** > **Distributed order management** > **Batch processing** > **DOM processor job setup**.
1. On the **Parameters** FastTab, for **Fulfillment profile**, select a profile for which DOM must run.
1. On the **Run in the background** FastTab, for **Batch group**, select a configured batch group.
1. For **Task description**, enter a name for the batch job.
1. Select **Recurrence**, and then specify the recurrence of the batch job.
1. Select **OK**.

## Search sales orders and lines

When processing, DOM considers the following order and order lines:

- Order lines that meet the criteria for sales order origins, modes of delivery, and legal entity as defined in the DOM profile, and that also meet any of the following criteria:
  - The order lines are created from Commerce channels. Sales orders are identified as being from Commerce channels when the **Commerce sale** option is set to **Yes**.
  - The order lines aren't brokered by DOM.
  - The order lines are brokered by DOM, but are marked as exceptions and are below the maximum attempt threshold.
  - The mode of delivery isn't pickup or electronic delivery.
  - The order lines aren't marked for delivery.
  - The order lines aren't manually excluded.
  - If **Do not process accepted store orders during order optimization** is enabled, the order lines aren't assigned to retail store warehouses with the fulfillment status as **Accepted** .
- Orders that aren't on hold.

To manually exclude a sales line, in Commerce headquarters, go to **Retail and Commerce** > **Customers** > **All sales orders** and select a sales line. On the **General** FastTab of the sales line, set the **Exclude from DOM processing** option to **Yes**.

## Partition sales lines

During each DOM processor job, DOM breaks orders into batches, depending on the **Maximum number of order lines per optimization** parameter value defined in the fulfillment profile. DOM ensures that all sales lines of a sales order are in the same batch.

For example, if 10,000 order lines are being optimized in a run, and the **Maximum number of order lines per optimization** parameter is set to **2000**, DOM creates five batches that are processed simultaneously.

If the **Maximum number of order lines per optimization** value is **0**:

- For the **Simplified Solver** type, DOM creates a batch for every 100 sales lines.
- For the **Production Solver** type, DOM creates a batch for every 1,500 sales lines.

> [!NOTE]
> If you set a large value for **Maximum number of order lines per optimization**, the DOM processor job takes a longer time to complete because it runs on a batch server. To improve performance, set an appropriate value to ensure that DOM can use more batch servers.

## Inventory lookup

DOM determines available physical inventory for each item by using the applicable dimensions from the product variant and sales order line together with the candidate site and warehouse. The lookup uses the product configuration, size, color, style, and product version dimensions, the site and warehouse storage dimensions, and the batch and serial number tracking dimensions.

Starting with Commerce version 10.0.46, DOM provides default support for inventory status, an advanced warehouse management storage dimension. DOM includes the inventory status from the sales order line when it determines which warehouses have inventory available for fulfillment. This step ensures that only inventory with a matching status is considered, producing a more accurate available-inventory calculation for advanced warehouse scenarios. This support is enabled by default.

The inventory status on a sales order line isn't set by DOM. It's a standard [inventory status](../supply-chain/inventory/inventory-statuses.md), which is one of the storage dimensions in the storage dimension group. The inventory status on an order line inherits from the default inventory status that's configured for the site, warehouse, item, or sales order. It can also be changed directly on the sales order line. The default inventory status for sales orders can't be a blocking status. You can also set up a default sales order inventory status as part of your advanced warehouse management parameters.

Other advanced warehouse management dimensions, including warehouse location and license plate, aren't supported by default. Custom inventory dimensions also aren't supported. To support these dimensions, use DOM extensibility. For more information, see [DOM extensibility](./dom-extensibility.md).

DOM adds physical quantities reserved for sales lines in the current DOM run back to the available inventory for the same item and inventory dimensions. This adjustment prevents those reservations from reducing the inventory available to fulfill the sales lines they belong to.

### Inventory lookup before Commerce version 10.0.46

In Commerce version 10.0.45 and earlier, DOM retrieves available inventory from warehouse V2 entities such as `InventWarehouseOnHandAggregatedView`. This inventory lookup supports product dimensions such as color, size, style, and configuration, and the site and warehouse storage dimensions. It doesn't support other storage dimensions, such as inventory status, location, or license plate.

To view the inventory returned by this legacy lookup, enter the following URL in your browser's address bar. Replace `<DomainName>` with the domain name of your environment and `<CompanyName>` with the name of your legal entity:

`https://<DomainName>/?cmp=<CompanyName>&mi=SysTableBrowser&TableName=InventWarehouseOnHandAggregatedView`

## Calculate distance

DOM converts addresses of the **Delivery** type to latitude and longitude values. DOM then converts the delivery address on the sales order to latitude and longitude values, and updates the latitude and longitude values of the address for future use. DOM depends on Azure Maps or Bing Maps to determine accurate latitude and longitude values based on address, city, and postal code information. To let DOM use the Azure Maps functionality, enable the **Confirm Azure Maps usage for DOM** setting. To let DOM use the Bing Maps functionality, enable the **Confirm Bing Maps usage for DOM** setting. For more information, see [Set up DOM](dom-set-up.md).

DOM uses either the Azure Maps or Bing Maps application programming interface (API) to calculate aerial or road distance, depending on the value of the **Disable road distance calculation** setting. DOM then uses this information to determine the cost of shipping. The optimization model prioritizes fulfillment of a complete order from one location. Even if part of an order is available in the same city or postal code, the model is optimized to reduce the number of shipments. For more information, see [Set up DOM](dom-set-up.md).

## Generate fulfillment plans

After DOM applies the rules, inventory constraints, and optimization, it picks the location that's closest to the customer's delivery address. Then, it gets fulfillment plans from the optimizer. Whether the system applies fulfillment plans on the sales lines depends on the value of the **Auto apply result** setting. For more information, see [Results of DOM runs](dom-runs-results.md).

:::image type="content" source="./media/ordercriteria.png" alt-text="Screenshot of sales order criteria in DOM processing." lightbox="media/ordercriteria.png":::

## More resources

- [DOM overview](dom.md)
- [Set up DOM](dom-set-up.md)
- [DOM rules](dom-rules.md)
- [DOM cost configuration](dom-costs.md)
- [Results of DOM runs](dom-runs-results.md)
- [Clean up DOM fulfillment plans and logs](dom-clean-up.md)
- [DOM extensibility](dom-extensibility.md)
- [DOM limitations](dom-limitations.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
