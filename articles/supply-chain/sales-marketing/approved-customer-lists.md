---
title: Approved customer lists (preview)
description: Control which products specific customers can buy and when they can buy them, which is especially important with a product line that involves controlled substances or branded products.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSApprovedCustomerList, QMSApprovedCustomerGroup, QMSApprovedItemGroup
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Approved customer lists (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

You might often sell products and services on a recurring basis to certain customers or groups of customers who have been approved for these purchases based on their prior and ongoing business relationship. By pre-approving customers, you not only expedite the sales order process and shipment of the product, but you also validate that the product is sold only to those customers who are allowed to purchase it. This also prevents a product from being sold to customers who aren't authorized to buy it.

For example, one of your long-time customers, Super Club, can purchase only their own private labeled products. They sell this product at both their Super Club warehouse location and their retail location, Super Mart. As a manufacturer of apple juice, you produce private label juices. You sell Super Club's private label apple juice cases only to Super Club Warehouse and Super Mart. This product can't be sold to any other customer.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
    - *(Preview) Advanced quality management*
    - *(Preview) Approved customer list*

## Setting up approved customers

To authorize an approved customer or an approved customer group for recurring sales, or to restrict who you can sell a given product to, you use the **Approved customer list setup** page.

When you set up new approved customer/item relationships, you also establish the approved customer list (ACL) check method, which provided the level of warning that is needed for a particular item or customer. Likewise, you also specify the type of relationship between the customer and item, which can be any of the following:

- A specific customer approved to purchase a specified item
- A specific customer approved to purchase any item in a specified item group
- A customer group approved to purchase a specified item
- A customer group approved to purchase any item in a specified item group (*group to group*)

## Establishing ACL check methods

When you approve a product for a customer, you also set up an ACL check method at both the customer level and the item level to confirm that this customer is approved to purchase this item. This process of verifying the customer/item combination is referred to as the ACL check method. To set the ACL check method for products and customers go to:

- **Product information management** \> **Products** \> **Released products**. Open the **Sell** FastTab and select the method in the field **Approved customer list check method**.

- **Sales and marketing** \> **Customers** \> **All customers** - Open the **Sales order defaults** FastTab and select the method in the field **Approved customer list check method**.

This method determines the action taken if you select a customer and/or item that isn't listed in the item's approved customer list. It also confirms that the transaction date is within the effective approval period specified for the customer and the item. You can set up the check method to issue a warning or to prevent the transaction from being processed.

The check methods include the following:

- *No check* – No validation is performed. Therefore, any customer or item that you select is allowed.
- *Warning only* – A warning message is displayed, but you can continue with the transaction.
- *Not allowed* – An error message is displayed, and this transaction isn't allowed.

The ACL check method is applicable for the following document types

- Sales agreements
- Sales quotations
- Sales orders

Based on the ACL check method, only items authorized for the selected customer account are permitted for the document.

## Set up approved customer lists

To set up and maintain customers who are approved to purchase one or more products, use the **Approved customer list setup** page, which you can open by following either of the following navigation paths:

- **Product information management** \> **Setup** \> **Approved customer list** \> **Approved customer list setup**
- **Sales and marketing** \> **Setup** \> **Approved customer list** \> **Approved customer list setup**

Then use the buttons and settings described in the following subsections.

### Buttons on the Approved customer list setup page

- **New** – Add a customer or approved customer group relationship to an item or approved item group.
- **Delete** – Remove a customer or approved customer group relationship to an item or approved item group.
- **Edit** – Edit the effective and expiration dates for a customer's approval period.
- **View** – Select a view option to locate item or approved item groups within the customer's effective date range. The two options also include approved items that never expire.
    - *Current* – Select this option to display records with an effective date before the current date.
    - *All* – Select this option to display all records.

### Fields on the Approved customer list setup page

- **Item code** – Select or view the item relationship code for which this item is approved. The values are:
    - *Table* – Designates a specific item.
    - *Group* – Designates an approved item group.
    - *All* – All items are designated.
- **Item relation** – Select or view the identification for the item or approved item group.
- **Customer code** – Select or view the customer relationship code for which this item is approved. The values are:
    - *Table* – Designates a specific customer.
    - *Group* – Designates an approved customer group.
    - *All* – All customers are designated.
- **Customer relation** – Select or view the identification for the customer or approved customer group.
- **Effective** – Select or view the effective date on which the ACL approval to purchase the item or items starts. The default is the current date.
- **Expiration** – Select or view the date on which the ACL's approval to purchase the item or items expires. The default is *Never*.

## Set up approved customer groups and approved item groups

Customer and item groups allow you to set up groups of customers and groups of items to expedite the approval process when the same set of items are approved for a specific customer, a group of customers, or all customers. If the approved item group is associated to an approved customer group, every customer in the group is authorized to purchase every item in the approved item group. To set up the groups, go to

- **Sales and marketing** \> **Setup** \> **Approved customer list** \> **Approved customer groups**
- **Product information management** \> **Setup** \> **Approved customer list** \> **Approved item groups**

## View and maintain approved items from the customer account

From the customer record, you have different options to view and maintain approved items for that customer account. 

1. Go to **Sales and marketing** \> **Customers** \> **All customers**.
1. Select the customer you want to set up.
1. On the Action Pane, open the **Sell** tab and select one of the following buttons from the **Approved customer** group.

    - **Setup** - Open the **Approved customer list** page filtered by the customer account. In this context, when you create a new line item, you only need to specify specific items or **Approved item groups**, the customer account is fixed to the account from where you opened the list.
    - **Approved items** -  Open the **Approved customer list by customer** page showing items approved for the customer account. This list is similar to the **Setup** page, except that all items defined in **Approved items groups** are unfolded to their item numbers. Use the fields **Effective** and **Expiration** to filter the list based on a specified **Effective date** or **Expiration date**.
    - **Effective period** - Open the **Approved customer list expiration** page showing items approved for the customer. By default this list shows approved items that have an expiration date. The date in the **As of** field is defaulted to *todays date*, so it shows by default approved items where the approval isn't expired as of *todays date*. You can change the date to a different date in the future. Select **Include never expired** to show also approved items that are set up with no expiration date.

## View and maintain approved customers from the released product master

From the product master, you have different options to view and maintain approved customers.

1. Go to  **Product information management** \> **Products** \> **Released products**.
1. Select the product you want to set up.
1. On the Action Pane, open the **Sell** tab and select one of the following buttons from the **Approved customer** group.

    - **Setup** - Open the **Approved customer list** page filtered by the customer account. In this context, when you create a new line item, you only need to specify specific items or **Approved item groups**, the customer account is fixed to the account from where you opened the list.
    - **Approved customers** -  Open the **Approved customer list by item** page showing customers approved for the item. This list is similar to the **Setup** page, except that all customers defined in **Approved customer groups** are unfolded to their item customer accounts. Use the fields **Effective** and **Expiration** to filter the list based on a specified **Effective date** or **Expiration date**.
    - **Effective period** - Open the **Approved customer list expiration** page showing customers approved for the item. By default this list shows approved customers that are set up with an expiration date. The date in the **As of** field is defaulted to *todays date*, so it shows by default approved customers where the approval isn't expired as of *todays date*. You can change the date to a different date in the future. Select **Include never expired** to show also approved customers that are set up with no expiration date.

## Configure the date validation for the approved customer list

When entering effective and expiration dates for an approved customer list record, validation is performed when the check method isn't set to *No check*. The dates are validated for the various documents based on the configuration selection you make in the **Sales and marketing parameters** page.

**Date type** – The date on the document that is selected for validation against the ACL record. The values are:

- *Today* – Today's date or system date.
- *Requested ship date* – The requested ship date on the sales order.
- *Requested receipt date* – The requested receipt date on the sales order.
- *Order date* – The date for which the order was placed.

This allows you to validate the sales order against the ACL when the order is expected to ship, when it's expected to be received, or when the order is placed. The values of Today and Order date will usually provide the same result.
