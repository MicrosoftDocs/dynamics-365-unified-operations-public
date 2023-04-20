---
title: Price attributes for products, customers, and orders
description: This article explains how to set up the configurable price attributes and link them to the products, customers, and orders.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPParameters, EcoResAttribute, EcoResAttributeGroup, SalesTable
ms.topic: how-to
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Price attributes for products, customers, and orders

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Pricing management provides a set of prefilled price attributes from fields in related tables that are associated with products, customers, orders, and order lines. It also lets you create custom price attributes and associate them with orders, customers, and items. You can use those price attributes when you create pricing rules and conditions. Then, when an order is placed, the pricing engine will then use the associations to determine the appropriate price.

This article explains how to set up the configurable price attributes and associate them with products, customers, and orders.

## Set up attribute types

When you create an attribute for any purpose, you must assign an *attribute type*. The attribute type defines the data type and the range of values that can be entered for attributes of that type.

To maintain your attribute types, go to **Product information management \> Setup \> Categories and attributes \> Attribute types**.

## Set up and assign product price attributes

You can create pricing rules that consider the attribute values that are assigned to each item in an order. *Attributes* provide a way to describe products and their characteristics through user-defined fields. Examples of attributes include brand, flavor, memory size, and commodity group.

When you create new attributes and assign them to a category, products in that category inherit the attributes and their default values. Attributes can be associated both with a released product and with a product master. Default attribute values can be overridden at the level of the individual product. Only one value per attribute can be assigned to each product.

> [!NOTE]
> Attributes apply to each *product*, not to each *item of inventory*. They serve as a broad classification of a product and aren't connected to inventory dimensions.

### <a name="price-attributes"></a>Set up product price attributes

To use attributes when you design Pricing management pricing rules, you must mark them as *price attributes*, as described in the following procedure.

1. Go to **Product information management \> Setup \> Categories and attributes \> Attributes**.
1. Either select an attribute in the list pane, or create a new one.
1. Set the **Attribute type** field to the type that you identified or selected earlier.
1. Set the **Can be used as price attribute** option to *Yes*.
1. In the **Default value** field, assign a default attribute value as required.
1. On the Action Pane, select **Save**.

### Assign product price attributes to products

Before attributes can have an effect, you must assign them to the relevant products by using one of the following methods:

- Assign product attributes to products by using the [procurement category hierarchy](../procurement/tasks/set-up-procurement-category-hierarchy.md).
- Group attributes into price attribute groups, and [assign attribute groups to Commerce categories](../../commerce/attribute-attributegroups-lifecycle.md). If products are assigned to categories that are associated with attribute groups, they inherit the attributes that are included in those attribute groups.

For more information about attribute management and association, see [Manage attributes and attribute groups](../../commerce/attribute-attributegroups-lifecycle.md).

## Set up and assign customer price attributes

You can create Pricing management pricing rules that consider the attribute values that are assigned to the customer who places an order. To set up customer price attributes, you first create an attribute group that includes the attributes that you need. You then set up that attribute group as the customer attribute group. You can have only one customer attribute group, and it applies to all customers. However, each customer can have different values for each attribute.

### Set up customer price attributes

Follow these steps to set up your customer price attributes.

1. Go to **Product information management \> Setup \> Categories and attributes \> Attributes**, and set up all the customer price attributes that you'll need. For each attribute, make sure that the **Can be used as price attribute** option is set to *Yes*. (For more information, see the [Set up product price attributes](#price-attributes) section of this article.) In the **Default value** field, assign a default attribute value as required.
1. Go to **Product information management \> Setup \> Categories and attributes \> Attribute groups**, and create a customer price attribute group. Give it an appropriate name (such as *Customer price attributes*), and add each relevant attribute on the **Attributes** FastTab.
1. Go to **Pricing management \> Setup \> Pricing management parameters**. On the **Price attribute** tab, set the **Customer attribute group** field to the attribute group that you created to hold your customer price attributes.

### Assign customer price attribute values to customers

Customer price attributes are initially assigned the default value that's set up for the attribute. If you must assign a specific value for a customer, follow these steps.

1. Go to **Sales and marketing \> Customers \> All customers**.
1. Select a customer in the grid.
1. On the Action Pane, on the **Price** tab, select **Customer attributes**.
1. Select a customer attribute in the list pane, and then, on the **Value** FastTab, edit the attribute value for the customer as required.
1. Repeat the previous step until you've assigned all the attribute values that are required for the customer.

## Set up and assign sales order price attributes

You can create Pricing management pricing rules that consider attribute values that are assigned to each sales order. For example, you might set up sales order price attributes for *Campaign event*, *Order type*, and *Order channel*. To set up sales order price attributes, you first create an attribute group that includes the attributes that you need. You then set up that attribute group as the sales order attribute group. You can have only one sales order attribute group, and it applies to all sales orders. However, each sales order can have different values for each attribute.

### Set up sales order price attributes

Follow these steps to set up your sales order price attributes.

1. Go to **Product information management \> Setup \> Categories and attributes \> Attributes**, and set up all the sales order price attributes that you'll need. For each attribute, make sure that the **Can be used as price attribute** option is set to *Yes*. (For more information, see the [Set up product price attributes](#price-attributes) section of this article.) In the **Default value** field, assign a default value as required.
1. Go to **Product information management \> Setup \> Categories and attributes \> Attribute groups**, and create a sales order price attributes group. Give it an appropriate name (such as *Order price attributes*), and add each relevant attribute on the **Attributes** FastTab.
1. Go to **Pricing management \> Setup \> Pricing management parameters**. On the **Price attribute** tab, set the **Sales order attribute group** field to the attribute group that you created to hold your sales order price attributes.

### Assign sales order price attribute values to sales orders

Sales order price attributes are initially assigned the default value that's set up for the attribute. If you must assign a specific value for an order, follow these steps.

1. Go to **Sales and marketing \> Orders \> All sales orders**.
1. Select an order in the grid, or create a new one.
1. On the Action Pane, on the **Price** tab, select **Sales order attributes**.
1. Select a sales order price attribute in the list pane, and then, on the **Value** FastTab, edit the attribute value for the customer as required.
1. Repeat the previous step until you've assigned all the attribute values that are required for the order.
