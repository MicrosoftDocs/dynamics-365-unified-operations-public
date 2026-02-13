---
title: Approved customer lists
description: Learn how to use approved customer lists (ACLs) to control which products specific customers can buy and when they can buy them.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSApprovedCustomerList, QMSApprovedCustomerGroup, QMSApprovedItemGroup
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Approved customer lists

[!include [banner](../../includes/banner.md)]

You might sell products and services on a recurring basis to specific customers or groups of customers who are preapproved for these purchases based on their previous and ongoing business relationship. By preapproving customers, you expedite the sales order process and shipment of the product. In addition, you ensure that the product is sold only to customers who are authorized to buy it and prevent it from being sold to other customers.

For example, you're a manufacturer of apple juice. One of your long-time customers, Super Club, can buy only its own privately labeled products. Super Club sells these products at both its Super Club warehouse location and its retail location, Super Mart. Therefore, you sell Super Club's privately labeled apple juice cases only to Super Club Warehouse and Super Mart. This product can't be sold to any other customer.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The following features must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.47, both of these features are turned on by default.
    - *Advanced quality management*
    - *Approved customer list*

## Set up approved customers

To authorize an approved customer or customer group for recurring sales, or to limit who you can sell a given product to, use the **Approved customer list setup** page to set up a relationship between the customer or customer group and an item or item group.

As part of the process of setting up a customer/item relationship, you specify the type of relationship. The following types are available:

- A specific customer is authorized to buy a specific item.
- A specific customer is authorized to buy any item in a specific item group.
- A customer group is authorized to buy a specific item.
- A customer group is authorized to buy any item in a specific item group. (A relationship of this type is known as a *group-to-group* relationship.)

In addition, you set up the approved customer list (ACL) check method to define what occurs if a customer tries to buy an item that it isn't authorized to buy.

## Set up the ACL check method

When you approve a product for a customer by setting up a customer/item relationship, you also set up the ACL check method at both the customer level and the item level. The ACL check method is used to validate the combination of the customer and the item. In other words, it confirms that the customer is authorized to buy the item.

To set up the ACL check method for products and customers, follow these steps:

- Go to **Product information management** \> **Products** \> **Released products**. On the **Sell** FastTab, in the **Approved customer list check method** field, select the method.
- Go to **Sales and marketing** \> **Customers** \> **All customers**. On the **Sales order defaults** FastTab, in the **Approved customer list check method** field, select the method.

The ACL check method defines the action that is taken if you select a customer and/or an item that isn't listed in the item's approved customer list. It also confirms that the transaction date is within the effective approval period that is specified for the customer and the item. You can set up the ACL check method either to issue a warning or to prevent the transaction from being processed.

The following ACI check methods are available:

- *No check* – No validation is done. Therefore, any customer or item that you select is allowed.
- *Warning only* – A warning message is shown, but you can continue with the transaction.
- *Not allowed* – An error message is shown, and you're prevented from continuing with the transaction.

The ACL check method is applicable to the following document types:

- Sales agreements
- Sales quotations
- Sales orders

Based on the ACL check method, only items that are authorized for the selected customer account are permitted for the document.

## Set up approved customer lists

To set up and maintain customers who are authorized to buy one or more products, use the **Approved customer list setup** page. To open this page, go to one of the following locations:

- **Product information management** \> **Setup** \> **Approved customer list** \> **Approved customer list setup**
- **Sales and marketing** \> **Setup** \> **Approved customer list** \> **Approved customer list setup**

Then use the buttons and fields that are described in the following subsections.

### Buttons on the Approved customer list setup page

- **New** – Add a relationship between an approved customer or customer group and an approved item or item group.
- **Delete** – Remove a relationship between an approved customer or customer group and an approved item or item group.
- **Edit** – Edit the effective and expiration dates for a customer's approval period.
- **View** – Select a view option to find approved items or item groups within the customer's effective date range. The two view options also include approved items that never expire.

    - *Current* – Show records that have an effective date before the current date.
    - *All* – Show all records.

### Fields on the Approved customer list setup page

- **Item code** – Select or review the item relationship code that the item is approved for. The following values are available:

    - *Table* – A specific item.
    - *Group* – An approved item group.
    - *All* – All items.

- **Item relation** – Select or review the identifier of the approved item or item group.
- **Customer code** – Select or review the customer relationship code that which the item is approved for. The following values are available:

    - *Table* – A specific customer.
    - *Group* – An approved customer group.
    - *All* – All customers.

- **Customer relation** – Select or review the identifier of the approved customer or customer group.
- **Effective** – Select or review the effective date when the approved customer list's approval to buy the item or items begins. The default value is the current date.
- **Expiration** – Select or review the date when the approved customer list's approval to buy the item or items expires. The default value is *Never*.

## Set up approved customer groups and approved item groups

You can set up groups of customers and groups of items to expedite the approval process when the same set of items is approved for a specific customer, a group of customers, or all customers. If the approved item group is associated with an approved customer group, every customer in that customer group is authorized to buy every item in that item group. To set up the groups, go to the following locations:

- **Sales and marketing** \> **Setup** \> **Approved customer list** \> **Approved customer groups**
- **Product information management** \> **Setup** \> **Approved customer list** \> **Approved item groups**

## View and maintain approved items from the customer account

From the customer record, you have different options for viewing and maintaining approved items for the customer account.

1. Go to **Sales and marketing** \> **Customers** \> **All customers**.
1. Select the customer that you want to set up.
1. On the Action Pane, on the **Sell** tab, in the **Approved customer** group, select one of the following buttons:

    - **Setup** – Open a view of the **Approved customer list** page that is filtered by the customer account. When you create a line item in this context, you just have to specify approved items or item groups. The customer account is fixed to the account that you opened the list from.
    - **Approved items** – Open the **Approved customer list by customer** page, which shows the items that are approved for the customer account. The list one this page resembles the list on the **Approved customer list** page, but it shows the item numbers of all items that are defined in approved item groups. Use the **Effective** and **Expiration** fields to filter the list based on a specific effective date or expiration date.
    - **Effective period** – Open the **Approved customer list expiration** page, which shows items that are approved for the customer. By default, the list shows approved items that have an expiration date, and the date in the **As of** field is set to the current date. Therefore, the list shows approved items where the approval is still effective as of the current date. You can change the date to a different date in the future. If you want the list also to show approved items that have no expiration date, select **Include never expired**.

## View and maintain approved customers from the released product master

From the product master, you have different options for viewing and maintaining approved customers.

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Select the product that you want to set up.
1. On the Action Pane, on the **Sell** tab, in the **Approved customer** group, select one of the following buttons:

    - **Setup** – Open a view of the **Approved customer list** page that is filtered by the customer account. When you create a line item in this context, you just have to specify approved items or item groups. The customer account is fixed to the account that you opened the list from.
    - **Approved customers** – Open the **Approved customer list by item** page, which shows the customers that are approved for the item. This list on this page resembles the list on the **Approved customer list** page, but it shows the customer account numbers of all customers that are defined in approved customer groups. Use the **Effective** and **Expiration** fields to filter the list based on a specific effective date or expiration date.
    - **Effective period** – Open the **Approved customer list expiration** page, which shows customers that are approved for the item. By default, the list shows approved customers that have an expiration date, and the date in the **As of** field is set to the current date. Therefore, the list shows approved customers where the approval is still effective as of the current date. You can change the date to a different date in the future. If you want the list also to show approved customers that have no expiration date, select **Include never expired**.

## Configure date validation for the approved customer list

When you enter effective and expiration dates for an approved customer list record, validation is done only if the ACL check method is set to *Warning only* or *Not allowed*. (It isn't done if the method is set to *No check*.) The dates are validated for the different documents, based on the setting of the **Date type** field on the **Sales and marketing parameters** page. This field specifies which date on the document is validated against the approved customer list record. The following values are available:

- *Today* – The current date or the system date.
- *Requested ship date* – The requested ship date on the sales order.
- *Requested receipt date* – The requested receipt date on the sales order.
- *Order date* – The date when the order was placed.

Therefore, you can validate the sales order against the approved customer list when the order is expected to be shipped, when it's expected to be received, or when it's placed. The *Today* and *Order date* values usually produce the same result.
