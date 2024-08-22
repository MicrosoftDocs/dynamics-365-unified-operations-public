---
title: Intercompany parameters
description: Learn about intercompany parameters, including examples involving two-level intercompany chains and three-level intercompany chains.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 09/01/2021
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchLineOpenOrder, InterCompanyTradingRelationSetupCustomer
---

# Intercompany parameters

[!include [banner](../../includes/banner.md)]

In an intercompany organization, you can set up parameters that determine how you trade between different legal entities. These parameters are determined by the fields that you select. You can select different combinations to reflect different trading scenarios.

The following two examples describe scenarios for intercompany organizations, one with two levels and one with three levels.

## Example 1: Two-level intercompany chain

The intercompany organization includes the following legal entities:

- Legal entity A – Sells to external customers, but has no stock. This legal entity buys from Legal entity B.
- Legal entity B – Sells only to Legal entity A.

Both legal entities can sell to and buy from each other.

In this example, the pricing on the original sales order, which is directed to the external customer, is always based on the sales price. The pricing on the intercompany sales order and the intercompany purchase order is controlled by the internal sales or transfer pricing on the intercompany sales order in Legal entity B.

The order header information is controlled from the original sales order to the external customer. Any change on the intercompany sales order is not synchronized to the original sales order.

In Legal entity A, on the **Intercompany** page for vendors, select **Purchase order policies**. Select the following fields in the **Original sales order (direct delivery)** field group:

- **Print packing slip automatically**
- **Post invoice automatically**
- **Print invoice automatically**

In the **Intercompany purchase order (direct delivery)** field group, select the following field:

- **Post invoice automatically**

In the **Original sales order <-> Intercompany purchase order** group, select the following fields:

- **Customer information**
- **RMA number**

In the **Intercompany purchase order <-> Intercompany sales order** field group, select the following fields:

- **Customer information**
- **RMA number**
- **Batch number**
- **Serial number**

In Legal entity B, on the **Intercompany** page for customers, select **Sales order policies**. Select the following fields in the **Intercompany sales order creation** field group:

- **Sales order numbering** : **Company + original number**
- **Allow summary update of documents for original customer**

In the **Intercompany sales order prices** field group, select the following fields:

- **Price and discount search**
- **Allow price edit**
- **Allow discount edit**

In the **Intercompany sales order \> Intercompany purchase order** field group, select the following fields:

- **Batch number**
- **Serial number**

## Example 2: Three-level intercompany chain

The intercompany organization includes the following legal entities:

- Legal entity A – A sales legal entity that sells to external customers and buys from Legal entity B.
- Legal entity B – A production or distribution legal entity that cannot deliver products, and buys from Legal entity C.
- Legal entity C – A production or distribution legal entity that delivers products to Legal entity B.

Internal transfer pricing between Legal entities B and C is at cost from the selling legal entity at the start of the chain. It is also at cost to Legal entity A, which sells to external customers. However, pricing on the original sales order to the external customer is always based on the sales price.

Pricing on all intercompany sales orders and intercompany purchase orders is controlled on the intercompany sales order. It is controlled at the start of the chain. Therefore, Legal entity C, which sells to Legal entity B, controls the price. Intercompany sales order pricing is based on the internal sales or transfer pricing that is set up in Legal entity C.

The order header information is controlled from the original sales order to the external customer. Any change on the intercompany orders is not synchronized to the original sales order.

The following parameters should be selected:

In Legal entity A, on the **Intercompany** page for vendors, select **Purchase order policies**. Select the following fields in the **Original sales order (direct delivery)** field group:

- **Print packing slip automatically**
- **Post invoice automatically**
- **Print invoice automatically**

In the **Intercompany purchase order (direct delivery)** field group, select the following field:

- **Post invoice automatically**

In the **Original sales order <-> Intercompany purchase order** field group, select the following fields:

- **Customer information**
- **RMA number**

In the **Intercompany purchase order <-> Intercompany sales order** field group, select the following fields:

- **Customer information**
- **RMA number**
- **Batch number**
- **Serial number**

In Legal entity B, on the **Intercompany** page for customers, select **Sales order policies**. Select the following fields in the **Intercompany sales order creation** field group:

- **Sales order numbering** : **Company + original number**
- **Allow summary update of documents for original customer**

In the **Intercompany sales order \> Intercompany purchase order** field group, select the following fields:

- **Batch number**
- **Serial number**

In the **Intercompany customer invoice posting** field group, select the following fields:

- **Unit price equal to cost price**
- **Initiate original customer invoice posting**

In Legal entity B, on the **Intercompany** page for vendors, select **Purchase order policies**. Select the following fields in the **Original sales order (direct delivery)** field group:

- **Print packing slip automatically**
- **Post invoice automatically**
- **Print invoice automatically**

In the **Intercompany purchase order (direct delivery)** field group, select the following field:

- **Post invoice automatically**

In the **Original sales order<-> Intercompany purchase order** field group, select the following fields:

- **Customer information**
- **RMA number**
- **Price and discount**

In the **Intercompany purchase order <-> Intercompany sales order** field group, select the following fields:

- **Customer information**
- **RMA number**
- **Batch number**
- **Serial number**

In Legal entity C, on the **Intercompany** page for customers, select **Sales order policies**. Select the following fields in the **Intercompany sales order creation** field group:

- **Sales order numbering** : **Number sequence code**
- **Allow summary update of documents for original customer**

In the **Intercompany sales order prices** field group, select the following field:

- **Price and discount search**

In the **Intercompany customer invoice posting** field group, select the following fields:

- **Unit price equal to cost price**
- **Initiate original customer invoice posting**

In the **Intercompany sales order <-> Intercompany purchase order** field group, select the following fields:

- **Batch number**
- **Serial number**

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
