---
title: 
description: 
ms.date: 04/25/2025
ms.topic: how-to
ms.service: 
author: johanhoffmann
ms.author: johanho
manager: 
---

# Approved customer lists (ACL)

You may often sell products and services on a recurring basis to certain customers or groups of customers who have been approved for these purchases based on their prior and on-going business relationship. By pre-approving customers, you not only expedite the sales order process and shipment of the product, but you also validate that the product is sold only to those customers who are allowed to purchase it. This also prevents a product from being sold to customers who are not authorized to buy it.

For example, one of your long-time customers, Super Club, can purchase only their own private labeled products. They sell this product at both their Super Club warehouse location and their retail location, Super Mart. As a manufacturer of apple juice, you produce private label juices. You sell Super Club's private label apple juice cases only to Super Club Warehouse and Super Mart. This product cannot be sold to any other customer.

## Setting up approved customers

To authorize an approved customer or an approved customer group for recurring sales, or to restrict who you can sell a given product to, you use the **Approved customer list setup** form.

When you set up new approved customer/item relationships, you also establish the ACL check method, which provided the level of warning that is needed for a particular item or customer. Likewise, you also specify the type of relationship between the customer and item, which can be any of the following:

- A specific customer approved to purchase a specified item

- A specific customer approved to purchase any item in a specified item group

- A customer group approved to purchase a specified item

- A customer group approved to purchase any item in a specified item group ( "Group to Group")

## Establishing ACL check methods

When you approve a product for a customer, you also set up an ACL check method at both the customer level and the item level to confirm that this customer is approved to purchase this item. This process of verifying the customer/item combination is referred to as the ACL check method.

This method determines the action taken if you select a customer and/or item that is not listed in the item's approved customer list. It also confirms that the transaction date is within the effective approval period specified for the customer and the item. You can set up the check method to issue a warning or to prevent the transaction from being processed.

The check methods include the following:

- **No check** – No validation is performed. Therefore, any customer or item that you select is allowed.

- **Warning only** – A warning message is displayed, but you can continue with the transaction.

- **Not allowed** – An error message is displayed, and this transaction is not allowed.

## Approved customer list setup

To set up and maintain customers who are approved to purchase one or more products, you use the **Approved customer list setup** form.

| **Path: Product information management (or Sales and marketing)** \> **Setup** \> **Approved customer list** \> **Approved customer list setup** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** |  |  |
| New | Add a customer or approved customer group relationship to an item or approved item group. |  |
| Delete | Remove a customer or approved customer group relationship to an item or approved item group. |  |
| Edit | Edit the effective and expiration dates for a customer's approval period. |  |
| View | Select a view option to locate item or approved item groups within the customer's effective date range. The two options also include approved items that never expire.</br><ul></br><li><blockquote></br>**Current** - Select this option to display records with an effective date prior to the current date.</br></blockquote></li></br><li><blockquote></br>**All** - Select this option to display all records.</br></blockquote></li></br></ul> |  |

| **Path: Product information management (or Sales and marketing)** \> **Setup** \> **Approved customer list** \> **Approved customer list setup** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Fields** |  |  |
| Item code | Select or view the item relationship code for which this item is approved. The values are:</br><ul></br><li><blockquote></br>**Table** – Designates a specific item.</br></blockquote></li></br><li><blockquote></br>**Group** – Designates an approved item group.</br></blockquote></li></br><li><blockquote></br>**All** – All items are designated.</br></blockquote></li></br></ul> |  |
| Item relation | Select or view the identification for the item or approved item group. |  |
| Customer code | Select or view the customer relationship code for which this item is approved. The values are:</br><ul></br><li><blockquote></br>**Table** – Designates a specific customer.</br></blockquote></li></br><li><blockquote></br>**Group** – Designates an approved customer group.</br></blockquote></li></br><li><blockquote></br>**All** – All customers are designated.</br></blockquote></li></br></ul> |  |
| Customer relation | Select or view the identification for the customer or approved customer group. |  |
| Effective | Select or view the effective date on which the ACL approval to purchase the item or items starts. The default is the current date. |  |
| Expiration | Select or view the date on which the ACL's approval to purchase the item or items expires. The default is **Never**. |  |

## Viewing customers and approved customer groups

To view lists of approved customers, you can access from any of the following forms, depending on the information you wish to obtain:

- Approved customer list

- Approved customer list by item

- Approved customer list expiration

### Approved customer list

To set up and maintain customers who are approved to a specific item, you can also use the **Approved customer list** form. This form provides access to the Approved Customer List while filtering the data based on the Released product selected.

| **Path: Product information management** \> **Common** \> **Released products** \> **Sell tab** \> **Approved customer** \> **Setup** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** |  |  |
| New | Add a customer or approved customer group relationship to the item. |  |
| Delete | Remove a customer or approved customer group relationship. |  |
| Edit record | Edit the effective and expiration dates for a customer's approval period. |  |
| View | Select a view option to ACL records for the item within the customer's effective date range. The two options also include approved items that never expire.</br><ul></br><li><blockquote></br>**Current** - Select this option to display records with an effective date prior to the current date.</br></blockquote></li></br><li><blockquote></br>**All** - Select this option to display all records.</br></blockquote></li></br></ul> |  |
| **Fields** |  |  |
| Item number | The identification for the product. | This defaults to the item selected. |
| Product name | The name of the product. |  |
| Customer code | Select or view the customer relationship code for which this item is approved. The values are:</br><ul></br><li><blockquote></br>**Table** - The item is approved for this specific customer.</br></blockquote></li></br><li><blockquote></br>**Group** - The item is approved for this approved customer group.</br></blockquote></li></br><li><blockquote></br>**All** - The product is approved for all customers.</br></blockquote></li></br></ul> |  |
| Customer relation | Select or view the identification for the customer or approved customer group. |  |
| Effective | Select or view the effective date on which the customer's approval to purchase the item starts. The default is the current date. |  |
| Expiration | Select or view the date on which the customer's approval to purchase the item expires. The default is **Never**. |  |

### Approved customer list by item

To view a list of customers who are approved to purchase a specific product, you use the **Approved customer list by item** form.

| **Path: Product information management** \> **Common** \> **Products** \> **Released products &gt;**</br>**Sell tab** \> **Approved customer group** \> **Approved customers** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** |  |  |
| View | Select a view option to locate customers within the item's effective date range. These two options also include approved items that never expire.</br><ul></br><li><blockquote></br>**Current** - Select this option to display records that have an effective date prior to the current date.</br></blockquote></li></br><li><blockquote></br>**All** - Select this option to display all records.</br></blockquote></li></br></ul> |  |
| **Fields** |  |  |
| Item number | The identification for the product. |  |
| Product name | The name of the product. |  |
| Effective | Select or view the effective date on which a customer's approval to purchase the product begins. You can use this field in conjunction with the **Expiration** field to view items within the customer's effective date range. |  |
| Expiration | Select or view the expiration date through which a customer's approval to purchase the product ends. |  |
| Customer account | The account identification for the customer. |  |
| Name | The name of the customer |  |
| Effective | The effective date for this customer. |  |
| Expiration | The expiration date for this customer. |  |

### Approved customer list expiration

To view a list of customers who are approved to purchase a specific product prior to a certain expiration date, use the **Approved customer list expiration** form.

| **Path: Product information management** \> **Common** \> **Products** \> **Released products &gt;**</br>**Sell tab** \> **Approved customer group** \> **Effective period** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** |  |  |
| View | Select a view option to locate items within the customer's effective date range. These two options also include approved items that never expire.</br><ul></br><li><blockquote></br>**Current** - Select this option to display records that have an effective date prior to the current date.</br></blockquote></li></br><li><blockquote></br>**All** - Select this option to display all records.</br></blockquote></li></br></ul> |  |
| **Fields** |  |  |
| Item number | The identification for the product. | This defaults to the item number selected. |
| Product name | The name of the product. |  |
| As of | Select a date as of which you want to view items that are approved for purchase by this customer when you use the **View** FastTab search feature. | This defaults to the current date. |
| Include never expired | Select this check box if you wish to include in the **View** FastTab search any approved items that do not expire. |  |
| Name | The name of the customer approved to purchase this item. |  |
| Customer account | The account identification for the customer. |  |
| Effective | The effective date for this particular item. |  |
| Expiration | The expiration date for this particular item. |  |

## Viewing items and approved item groups

To view lists of approved items for a specific customer, you can access from any of the following forms, depending on the information you wish to obtain:

- Approved customer list

- Approved customer list by customer

- Approved customer list expiration

### Approved customer list

To set up and maintain items that are approved for a specific customer, you can also use the **Approved customer list** form. This form provides access to the Approved Customer List while filtering the data based on the Customer selected.

| **Path: Sales and marketing** \> **Common** \> **Customers** \> **All customers** \> **Sell tab** \> **Approved customer** \> **Setup** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** |  |  |
| New | Add an item or approved item group relationship to the Customer. |  |
| Delete | Remove an item or approved item group relationship. |  |
| Edit record | Edit the effective and expiration dates for an item's approval period. |  |
| View | Select a view option to ACL records for the customer within the item's effective date range. The two options also include approved items that never expire.</br><ul></br><li><blockquote></br>**Current** - Select this option to display records with an effective date prior to the current date.</br></blockquote></li></br><li><blockquote></br>**All** - Select this option to display all records.</br></blockquote></li></br></ul> |  |
| **Fields** |  |  |
| Customer account | The identification for the customer. | This defaults to the customer selected. |
| Name | The name of the customer. |  |
| Item code | Select or view the item relationship code for which this customer is approved. The values are:</br><ul></br><li><blockquote></br>**Table** - The item is approved for this specific customer.</br></blockquote></li></br><li><blockquote></br>**Group** - The item is approved for this approved customer group.</br></blockquote></li></br><li><blockquote></br>**All** - The product is approved for all customers.</br></blockquote></li></br></ul> |  |
| Item relation | Select or view the identification for the item or approved item group. |  |
| Effective | Select or view the effective date on which the customer's approval to purchase the item starts. The default is the current date. |  |
| Expiration | Select or view the date on which the customer's approval to purchase the item expires. The default is **Never**. |  |

### Approved customer list by customer

To view a list of items that are approved to be purchased by a specific customer, you use the **Approved customer list by customer** form.

| **Path: Sales and marketing** \> **Common** \> **Customers** \> **All customers** \> **Sell tab** \> **Approved customer** \> **Approved items** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** |  |  |
| View | Select a view option to locate items within the customer's effective date range. These two options also include approved items that never expire.</br><ul></br><li><blockquote></br>**Current** - Select this option to display records that have an effective date prior to the current date.</br></blockquote></li></br><li><blockquote></br>**All** - Select this option to display all records.</br></blockquote></li></br></ul> |  |
| **Fields** |  |  |
| Customer account | The identification for the customer. |  |
| Name | The name of the customer. |  |
| Effective | Select or view the effective date on which a customer's approval to purchase the product begins. You can use this field in conjunction with the **Expiration** field to view items within the customer's effective date range. |  |
| Expiration | Select or view the expiration date through which a customer's approval to purchase the product ends. |  |
| Item number | The account identification for the item. |  |
| Product name | The name of the item. |  |
| Effective | The effective date for this item. |  |
| Expiration | The expiration date for this item. |  |

### Approved customer list expiration

To view a list of items that are approved to be purchased by a specific customer prior to a certain expiration date, use the **Approved customer list expiration** form.

| **Path: Sales and marketing** \> **Common** \> **Customers** \> **All customers** \> **Sell tab** \> **Approved customer** \> **Effective period** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** |  |  |
| View | Select a view option to locate items within the customer's effective date range. These two options also include approved items that never expire.</br><ul></br><li><blockquote></br>**Current** - Select this option to display records that have an effective date prior to the current date.</br></blockquote></li></br><li><blockquote></br>**All** - Select this option to display all records.</br></blockquote></li></br></ul> |  |
| **Fields** |  |  |
| Customer account | The identification for the customer. | This defaults to the customer number selected. |
| Customer name | The name of the customer. |  |
| As of | Select a date as of which you want to view items that are approved for purchase by this customer when you use the **View** FastTab search feature. | This defaults to the current date. |
| Include never expired | Select this check box if you wish to include in the **View** FastTab search any approved items that do not expire. |  |
| Item number | The name of the item approved to be purchased by this customer. |  |
| Product name | The account identification for the item. |  |
| Effective | The effective date for this customer. |  |
| Expiration | The expiration date for this customer. |  |

### Approved customer list by customer

To view a list of products that have been approved for a specific customer to purchase on a recurring basis, use the **Approved customer list by customer** form. An approved customer is authorized to order certain products, which expedites the sales order process and allows the product to ship more quickly.

| **Path: Sales and marketing** \> **Common** \> **Sales orders** \> **All sales orders &gt;**</br>**General tab** \> **Related information group** \> **Approved items** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** |  |  |
| View | Select a view option to locate items within the customer's effective date range. These two options also include approved items that never expire.</br><ul></br><li><blockquote></br>**Current** - Select this option to display records that have an effective date prior to the current date.</br></blockquote></li></br><li><blockquote></br>**All** - Select this option to display all records.</br></blockquote></li></br></ul> |  |
| **Fields** |  |  |
| Customer account | The account identification for the customer. | This defaults to the customer on the sales order. |
| Customer name | The name of the customer. |  |
| Effective | Select or view the effective date on which a customer's approval to purchase the product begins. You can use this field in conjunction with the **Expiration** field to view items within the customer's effective date range. |  |
| Expiration | Select or view the expiration date through which a customer's approval to purchase the product ends. |  |
| Item number | The item approved for this customer. |  |
| Product name | The name of the item. |  |
| Effective | The effective date for this particular item. |  |
| Expiration | The expiration date for this particular item. |  |

Setting up approved customer groups and approved item groups

Customer and item groups allow you to set up groups of customers and groups of items to expedite the approval process when the same set of items are approved for a specific customer, a group of customers, or all customers. If the approved item group is associated to an approved customer group, every customer in the group is authorized to purchase every item in the approved item group.

### Setting up approved customer groups

To set up, maintain, and view a group of customers who are approved to purchase a certain item or approved item groups during the specified effective period, you use the **Approved customer groups** form. You can associate the approved customer group to one or more items, approved item groups, or all items.

| **Path: Sales and marketing** \> **Setup** \> **Approved customer list** \> **Approved customer groups** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** |  |  |
| New | Add an approved customer group. |  |
| Delete | Delete the selected approved customer group.</br>**Note:** You cannot delete an approved customer group if it is currently assigned to a customer or has a record relationship in the ACL. |  |
| Add (Customer list tab) | Add a customer to this Approved Customer Group. |  |
| Remove (Customer list tab) | Remove the selected customer from the Approved Customer Group. |  |
| Remove (Assign customers using query tab) | Remove the selected customer from the query list. |  |
| Select query (Assign customers using query tab) | Opens the search query form allowing the user to enter criteria for specific customers. |  |
| Add all to group (Assign customers using query tab) | Add the selected Customers to the selected Approved customer group. |  |
| New (Approved items fast tab) | Add an item or an approved item group for the selected Approved Customer Group. |  |
| Delete (Approved items fast tab) | Remove the selected item or approved item group. |  |
| Edit (Approved items fast tab) | Edit the current ACL record. |  |
| View (Approved items fast tab) | View all or current records based on Effective and Expiration date. |  |
| **Fast tabs** |  |  |
| Customers | Set up, maintain, and view customers who are associated with the selected Approved Customer Group. | Use the <em>Assign customers using query</em> tab to search for and select a subset of Customers based on any combination of customer fields and values. This subset of customers, once finalized, can be added to the selected Approved customer group at the same time using the <em>Add all to group</em> button |
| Approved items | Set up, maintain, and view items or approved item groups that are approved to be purchased by customers who are associated with the selected approved customer group. |  |
| **Fields** |  |  |
| Approved customer group | Enter or view the unique identification for the approved customer group. |  |
| Description | Enter or view the description of the approved customer group. |  |
| Customer account (Customer list tab) | The account identification for the customer. |  |
| Search name (Customer list tab) | Search name of the Customer. |  |
| Customer group (Customer list tab) | Customer group of the Customer. |  |
| Invoice account (Customer list tab) | Invoice account of the Customer. |  |
| Customer account (Assign customers using query tab) | The account identification for the customer. |  |
| Name (Assign customers using query tab) | The name of the customer. |  |
| Approved customer group (Assign customers using query tab) | Approved customer group the customer is associated with. |  |
| Item code | Enter or view the unique identification for the item or Approved Item Group. | The options are **Table**, **Group**, or **All**. |
| Item relation | Enter or view the name of the Approved Item Group if the Item code is set to Group. Enter or view the name of the item if the Item code is set to Table. |  |
| Effective | The effective date for this item or Approved Item Group. |  |
| Expiration | The expiration date for this item or Approved Item Group. |  |

You can also assign a customer to an Approved Customer Group using the **Customer** form.

| **Path: Sales and marketing** \> **Common** \> **Customers** \> **All customers** \> **Sales order defaults FastTab** |                                                                                                                          |                    |
|---------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|--------------------|
| **Label Name**                                                                                                | **Description**                                                                                                          | **Examples/Hints** |
| **Fields**                                                                                                    |                                                                                                                          |                    |
| Approved customer group                                                                                       | The group to which this customer is assigned for purposes of ACL                                                         |                    |
| Approved customer list check method                                                                           | The method of validation that is used when creating a sales order, sales agreement or sales quotation for this customer. |                    |

### Setting up approved item groups

To set up, maintain, and view a group of products that are approved for purchase by a certain customer or customers during the specified effective period, you use the **Approved item groups** form. You can associate the item group to one or more customers, customer groups, or all customers.

| **Path: Product information management** \> **Setup** \> **Approved customer list** \> **Approved item groups** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Buttons** |  |  |
| New | Add an approved item group. |  |
| Delete | Delete the selected approved item group.</br>**Note:** You cannot delete an approved item group if it is currently associated with an item or used on an ACL record. |  |
| Add (Items tab) | Add an item to this Approved Item Group. |  |
| Remove (Items tab) | Remove the selected item from the Approved Item Group. |  |
| Remove (Assign items using query tab) | Remove the selected item from the query list. |  |
| Select query (Assign items using query tab) | Opens the search query form allowing the user to enter criteria for specific items. |  |
| Add all to group (Assign items using query tab) | Add the selected Items to the selected Approved item group. |  |
| New (Approved customers fast tab) | Add a customer or an approved customer group for this Approved item group. |  |
| Delete (Approved customers fast tab) | Remove the selected customer or approved customer group. |  |
| Edit (Approved customers fast tab) | Edit the current ACL record. |  |
| View (Approved customers fast tab) | View all or current records based on Effective and Expiration date. |  |
| **Fast Tabs** |  |  |
| Items | Set up, maintain, and view items that are associated with the selected Approved Item Group. | Use the <em>Assign items using query</em> tab to search for and select a subset of Items based on any combination of item fields and values. This subset of items, once finalized, can be added to the selected Approved item group at the same time using the <em>Add all to group</em> button |
| Approved customers | Set up, maintain, and view customers or approved customer groups that are approved to purchase item in the select approved item group. |  |
| **Fields** |  |  |
| Approved item group | Enter or view the unique identification for the approved item group. |  |
| Description | Enter or view the description for the approved item group. |  |
| Item number (Item list tab) | The identification for the product. |  |
| Search name (Item list tab) | The search name of the item. |  |
| Product name (Item list tab) | The product name. |  |
| Item model group (Item list tab) | The Item model group of the item. |  |
| Item number (Assign items using query tab) | The identification for the product. |  |
| Search name (Assign items using query tab) | The search name of the item. |  |
| Approved item group (Assign items using query tab) | Approved item group the item is associated with. |  |
| Customer code | Enter or view the unique identification for the customer or Approved Customer Group. | The options are **Table**, **Group**, or **All**. |
| Customer relation | Enter or view the name of the Approved Customer Group if the Customer code is set to Group. Enter or view the name of the Customer if the Customer code is set to Table. |  |
| Effective | The effective date for this particular customer or Approved Customer Group. |  |
| Expiration | The expiration date for this particular customer or Approved Customer Group. |  |

You can also assign an item to an Approved Item Group using the **Released products** form.

| **Path: Product information management** \> **Common** \> **Released products** \> **Sell FastTab** |                                                                                                                      |                    |
|-----------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|--------------------|
| **Label Name**                                                                                | **Description**                                                                                                      | **Examples/Hints** |
| **Fields**                                                                                    |                                                                                                                      |                    |
| Approved customer list check method                                                           | The method of validation that is used when creating a sales order, sales agreement or sales quotation for this item. |                    |
| Approved item group                                                                           | The group to which this item is assigned for purposes of ACL                                                         |                    |

### Viewing current approved items for a customer

When entering a sales order for a specific customer you can use the Item number drop-down to provide a list of items for selection to add to the sales order line. If the customer associated with the sales order has a record in the Approved customer list, then an **Approved items** tab will be visible to make a selection. The Other tab contains all items.

| **Path: Sales and marketing** \> **Common** \> **Sales orders** \> **All sales orders** |                                                                                                                                                                                                                                                                                                                        |                    |
|-----------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------|
| **Label Name**                                                                    | **Description**                                                                                                                                                                                                                                                                                                        | **Examples/Hints** |
| **Fields**                                                                        |                                                                                                                                                                                                                                                                                                                        |                    |
| Item number                                                                       | The identification for the product.                                                                                                                                                                                                                                                                                    |                    |
| Product name                                                                      | The name of the product.                                                                                                                                                                                                                                                                                               |                    |
| Valid for                                                                         | The ACL source that provides this ACL relationship. If the item has a direct relationship with the customer then the field will be "Table". If the item has a group relationship, either through an Approved Item Group or an Approved Customer Group to which this customer is associated, the field will be "Group". |                    |
| Group                                                                             | When there is a group relation between the Item and Customer and the 'Valid for' field is "Group" then this field indicates the group from which the relationship was resolved or derived.                                                                                                                             |                    |
| Effective                                                                         | The effective date for this item or Approved Item Group.                                                                                                                                                                                                                                                               |                    |
| Expiration                                                                        | The expiration date for this item or Approved Item Group.                                                                                                                                                                                                                                                              |                    |

You may also select the **Add lines** option on the sales order line. Click the checkbox on the added Approved items button (defaults to being checked) to display all the resolved items that this customer is authorized to purchase.

Both options will only show the approved items for which the customer is currently approved to purchase. If you feel that they should be other items available to this customer, you can use the Approved items from the Customer form which will show all ACL record for the selected customer regardless of Effective or Expiration date.

### Viewing all approved items for a customer

From the sales order form you can select to display all Approved items for the customer associated with the sales order by clicking the General tab and selecting Approved items. This provides access to the Approved Customer List by Customer form from the sales order.

### Configuring the date validation for the Approved Customer List

When entering Effective and Expiration dates for an Approved Customer List record there is validation performed when the check method is not set to 'No check'. The dates are validation for the various documents based on the configuration selection you make in the Sales and marketing parameters form.

| **Path: Sales and marketing** \> **Common** \> **Sales orders** \> **All sales orders** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Fields** |  |  |
| Date type | The date on the document that is selected for validation against the ACL record. The values are:</br><ul></br><li><blockquote></br>Today - Today's date or system date</br></blockquote></li></br><li><blockquote></br>Requested ship date – The requested ship date on the sales order</br></blockquote></li></br><li><blockquote></br>Requested receipt date – The requested receipt date on the sales order</br></blockquote></li></br><li><blockquote></br>Order date – The date for which the order was placed</br></blockquote></li></br></ul> | This allows you to validate the sales order against the ACL when the order is expected to ship, when it is expect to be received, or when the order is placed. The values of Today and Order date will usually provide the same result. |
