---
title: Inventory profile overview
description: Learn about the inventory profile which is intended for the implementation of and accounting for movements and on-hand inventory as they relate to activities.
author: evgenypopov
ms.author: evgenypopov
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 06/27/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1
---

# Inventory profile overview
[!include [banner](../../includes/banner.md)]


The inventory profile is intended for the implementation of and accounting for movements and on-hand inventory as they are related to a kind of activity. The kind of activity defines the way that the item was received by the organization and the restrictions that are imposed on the handling of the item. Here are some examples of kinds of activity:

- The purchase of the item on the agreement for further sales or processing
- The receipt of items under a commission agreement
- The receipt of raw material for processing

In all these cases, the movements and on-hand inventory of the same item that is received by the organization as a result of different kinds of activity should differ in the following aspects:

- **Inventory management** – Quantitative on-hand inventory of the item for different kinds of activity should not be mixed.
- **Accounting** – Movements and on-hand inventory of the item for different kinds of activity should be reflected in different ledger accounts.

The inventory profiles functionality lets you perform these tasks:

- Set up inventory dimensions in accordance with the organization's kinds of activity. For more information, see the [Kinds of activity](#kinds-of-activity) section.
- Use the inventory profile as an inventory dimension. For more information, see the [Inventory profile as an inventory dimension](#inventory-profile-as-an-inventory-dimension) section.
- Set up compatible inventory profiles. For more information, see the [Compatible inventory profiles](#compatible-inventory-profiles) section.
- Set up and use inventory posting ledger accounts in the context of inventory profiles. For more information, see the [Inventory transaction combinations for inventory profiles](#inventory-transaction-combinations-for-inventory-profiles) section.
- Specify an inventory profile when you set up the inventory posting. For more information, see the [Inventory posting setup](#inventory-posting-setup) section.
- Set up a default inventory profile and a default kind of activity for purchase orders, sales orders, and transfer orders. For more information, see the [Set up a kind of activity and an inventory profile in purchase, sales, and transfer orders](#set-up-a-kind-of-activity-and-an-inventory-profile-in-purchase-sales-and-transfer-orders) section.
- Split sales order lines by inventory profile. For more information, see the [Split sales order lines by inventory profile](#split-sales-order-lines-by-inventory-profile) section.
- Specify the inventory profile on bill of materials (BOM) lines. For more information, see the [Inventory profile in BOMs](#inventory-profile-in-boms) section.
- Specify the inventory profile in the cash flow forecast on purchase orders and sales orders. For more information, see the [Cash flow forecasts on purchase and sales orders](#cash-flow-forecasts-on-purchase-and-sales-orders) section.
- Specify the inventory profile in cash flow forecasts that are based on planned purchases and sales. For more information, see the [Cash flow forecasts based on planned purchases and sales](#cash-flow-forecasts-based-on-planned-purchases-and-sales) section.

## Kinds of activity

There are four kinds of activity:

- **Basic** – This kind of activity is intended for the accounting of items that aren't counted for other activities (for example, items that are purchased under an agreement for resale, raw materials, and materials for production).
- **Commission agent** – This kind of activity is intended for the accounting of goods that the organization receives from the principal for further realization to the final buyer on behalf of the commission agent.
- **Principal's agent** – This kind of activity is intended for the accounting of goods that the organization receives from the principal for further realization to the final buyer on behalf of the principal.
- **Bailee** – This kind of activity is intended for the accounting of goods that the bailee receives in the process of bailment.

## Inventory profile as an inventory dimension

The inventory profile is used for the separate accounting of item movements and balances in the context of activities. You can define a set of possible values for the inventory profile. For each inventory profile, the kind of activity that the profile belongs to is specified. The type of activity in the inventory profile can't be changed.

When an inventory profile is active in a group of inventory dimensions, the following check boxes on the **Tracking dimension groups** page are selected: **Primary stocking**, **Physical inventory**, **Financial inventory**, and **Transfer**. Additionally, when an inventory profile is active for a product, it must be specified on the document lines and can't differ in the corresponding inventory transactions.

For more information, see [Set up an inventory profile](rus-set-up-inventory-profile.md).

## Compatible inventory profiles

The inventory profile compatibility setting is used for these purposes:

- Automatic selection of inventory profiles from on-hand inventory when you create sales order lines by selecting **Create lines**.
- Control of the validity of inventory profiles on sales order lines if a specific inventory profile is specified in the order header.

For more information, see [Set up compatible inventory profiles](rus-set-up-inventory-profile.md#set-up-compatible-inventory-profiles).

## Inventory transaction combinations for inventory profiles

To set up and use inventory posting ledger accounts in the context of inventory profiles, you must activate the inventory transaction combinations for inventory profiles.

For more information, see [Activate transaction combinations for inventory profiles](rus-set-up-inventory-profile.md#activate-transaction-combinations-for-inventory-profiles).

## Inventory posting setup

You can specify the inventory profile when you set up inventory posting. The ledger account that an item movement is posted to is determined by the value of the inventory profile that is specified for the movement.

Inventory posting can be set up for the following inventory profile values:

- A specific inventory profile value
- A group of inventory profile values that have the same kind of activity
- All inventory profile values (By default, the inventory posting value is also used for products that aren't accounted in the context of an inventory profile.)

The ability to set posting for a specific kind of activity and inventory profile is controlled by the settings for activating combinations of inventory transactions.

For more information, see [Set up inventory posting in the context of an inventory profile](rus-set-up-inventory-profile.md#set-up-inventory-posting-in-the-context-of-an-inventory-profile).

## Set up a kind of activity and an inventory profile in purchase, sales, and transfer orders

The kind of activity and inventory dimension can be specified in the purchase order, sales order, and transfer order header. If a kind of activity is specified in an order, only inventory profile values that correspond to that kind of activity can be specified in the order header, on the order lines, and in the inventory transactions for the order. If you specify an inventory profile in the sales order header and on the sales order lines, only that inventory profile and compatible inventory profiles can be specified on the order lines and in the inventory transactions. For more information, see [Set up a default inventory profile for purchase orders](rus-set-up-inventory-profile.md#set-up-a-default-inventory-profile-for-purchase-orders).

The kind of activity and inventory profile can be specified in a vendor, customer, or agreement master record. If a kind of activity and inventory profile are specified, they are considered the default dimension values for purchase order and sales order headers. If a kind of activity is already specified for the vendor, customer, or agreement master record, you can specify only the inventory profile value that corresponds to the kind of activity in that master record. For more information, see [Set up a default kind of activity and inventory profile for vendors, customers, agreements, and warehouses](rus-set-up-inventory-profile.md#set-up-a-default-kind-of-activity-and-inventory-profile-for-vendors-customers-agreements-and-warehouses).

In other types of documents, such as inventory journals and production orders, the inventory profile, like other inventory dimensions, is specified on the document lines. For more information, see [Set up a default inventory profile for BOMs](rus-set-up-inventory-profile.md#set-up-a-default-inventory-profile-for-boms).

You can't change the inventory profile value during inventory picking or registration. The inventory profile value that is specified on the document line remains the same on inventory transactions until financial posting occurs.

## Split sales order lines by inventory profile

When you create sales order lines, if you specify the quantity but don't specify an inventory profile, the system can automatically pick up physically available on-hand inventory in the context of inventory profiles.

Some inventory profile values might also indicate that they can't be used for automatic line splitting. To post an outgoing inventory transaction that has this type of inventory profile, you must specify the inventory profile value on the sales order line or inventory journal line.

If a kind of activity is specified in the sales order, the sales order line can be split only by the inventory profile values that are related to that kind of activity.

For more information, see [Create sales order lines](rus-use-inventory-profile-documents-queries.md#create-sales-order-lines).

## Split documents by inventory profile

Posted packing slips, product receipts, invoices, and invoice-factures for purchase orders and sales orders are divided into separate documents, based on the kinds of activity that correspond to the inventory profiles from the order lines, and on the corresponding customer and vendor posting profiles.

The value of the kind of activity is stored in the invoices and invoice-factures.

Posted documents are divided based on the number of unique combinations of a kind of activity and a customer or vendor posting profile. Items that aren't accounted for in the context of inventory profiles are included in invoices, and the **Basic** kind of activity and the customer or vendor posting profile are specified in the order header. Splitting by kinds of activity and customer or vendor posting profiles is done regardless of the summary update settings.

For more information, see [Set up a default inventory profile for purchase orders](rus-set-up-inventory-profile.md#set-up-a-default-inventory-profile-for-purchase-orders), [Set up a default inventory profile for sales orders](rus-set-up-inventory-profile.md#set-up-a-default-inventory-profile-for-sales-orders), [Purchase orders](rus-use-inventory-profile-documents-queries.md#purchase-orders), and [Sales orders](rus-use-inventory-profile-documents-queries.md#sales-orders).

## Inventory profile in BOMs

You can specify an inventory profile on the BOM line. The inventory profile will be further specified in the following places:

- On the BOM journal line when the BOM is accepted
- On the sales order or purchase order line when the BOM is exploded
- On the production order BOM line when the production order is created

The **Inventory profile** field on the BOM journal lines is filled in from one of two places:

- The BOM lines
-  The **Inventory profile** field on the **Bills of materials** tab of the **Inventory and warehouse management parameters** page (if the inventory profile is active for the item and isn't specified on the BOM line)

The **Inventory profile** field on the BOM order lines is filled in from one of two places:

- The BOM lines
- The **Inventory profile** field on the **Inventory and warehouse management parameters** page

For more information, see the [Set up a default inventory profile for BOMs](rus-set-up-inventory-profile.md#set-up-a-default-inventory-profile-for-boms) section.

## Cash flow forecasts on purchase and sales orders

When you generate a cash flow forecast for purchase orders or sales orders, the inventory profiles that is specified on the order lines are considered when the posting accounts of inventory movements and customer and vendor transactions are determined. Ledger accounts for customer and vendor transactions are defined from the posting profiles that correspond to the inventory profiles that are specified on the order lines. For order lines where an inventory profile isn't specified, the **Basic** kind of activity and the posting profile that is specified in the order header are used.

For more information, see the [Cash flow forecasts on purchase and sales orders](rus-use-inventory-profile-documents-queries.md#cash-flow-forecasts-on-purchase-and-sales-orders) section later in this article.

## Cash flow forecasts based on planned purchases and sales

When you generate a cash flow forecast for planned sales and purchases, the inventory profiles that are specified on the supply forecast lines and in planned orders are considered.

Find more details in the following topics:

- [Set up an inventory profile](rus-set-up-inventory-profile.md)
- [Use an inventory profile in documents and queries](rus-use-inventory-profile-documents-queries.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
