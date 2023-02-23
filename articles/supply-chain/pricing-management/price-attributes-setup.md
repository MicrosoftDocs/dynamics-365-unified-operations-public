---
title: Set up price attributes for products, customers, and orders
description: This article explains how to set up the configurable price attributes and link them to the products, customers, and orders.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 03/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up price attributes for products, customers, and orders

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.33 GA -->

Pricing management provides a set of pre-populated price attributes from fields in the related table that are associated to **Product**, **Customer**, **Order table** and **Order line**. <!-- KFM: This sentence isn't clear; please clarify. Also, what are these bolded terms? Tables? Fields? How do we find and use these "pre-populated" (predefined?) attributes? -->

Pricing management also offers the option to create custom price attributes and connect them to orders, customers, and items. You can use those price attributes when creating pricing rules and conditions, and the pricing engine will use those associations to identify the appropriate sales order <!-- KFM: Do you mean sales price?--> when an order is placed.

This article explains how to set up the configurable price attributes and link them to the products, customers, and orders.

## Set up attribute types

When you create an attribute for any purpose, you must assign an *attribute type*. The attribute type defines the data type and the range of values that can be entered for the attributes of that type.

To maintain your attribute types, go to **Product information management \> Setup \> Categories and attributes \> Attribute types**.

## Set up and assign product price attributes

You can create Pricing management pricing rules that consider attribute values assigned to each item in an order. *Attributes* describe products and their characteristics. Examples of attributes include: brand, flavor, memory size, and commodity group. They provide a way to describe products and their characteristics through user-defined fields.

When you create new attributes and assign them to a category, products in that category inherit those attributes and their default values. Attributes can be associated both to a released product and to a product master. Default attribute values can be overridden at the individual product level. Only one value for each attribute can be assigned to each products. Attributes apply to each product rather than each item of inventory. Attributes serve as a broad classification of a product, rather than being connected to inventory dimension.

### <a name="price-attributes"></a>Set up product price attributes

To use attributes when designing price rules for Pricing management, you must mark them as *price attributes*, as described in the following procedure.

1. Go to **Product information management \> Setup \> Categories and attributes \> Attributes**.
1. Either select an attribute in the list pane or create a new one.
1. Set **Attribute type** to the type you identified or selected in the previous section.
1. Set the **Can be used as price attribute** to *Yes*.
1. Assign a **Default value** if needed.
1. Make other settings as needed.

### Assign product price attributes to products

For attributes to have an effect, you must assign them to the relevant products using one of the following methods:

- Assign product attributes to products using the [Set up a procurement category hierarchy](../procurement/tasks/set-up-procurement-category-hierarchy.md) <!-- KFM: Is it right that we want to assign these to *procurement* categories? -->
- Group attributes into price attribute groups and [assign attribute groups to Commerce categories](../../commerce/attribute-attributegroups-lifecycle.md). Products assigned to categories that are associated to attribute groups inherit the attributes that are included in those attribute groups.

For more information about attribute management and association, see [Manage attributes and attribute groups](../../commerce/attribute-attributegroups-lifecycle.md).

<!-- KFM: I think we need the following section, which I added based on assumptions. Please review and confirm.

### Assign product price attribute values to products 

Product price attributes will initially be assigned the **Default value** set up for the attribute. If you need to assign a specific value for a product, follow these steps.

1. Depending on whether you want to set up a released product or product master, go to one of the following pages:
    - **Product information management \> Products \> Released products**.
    - **Product information management \> Products \> Product masters**.
1. Select a released product or product master in the grid.
1. On the Action Pane, open the **Product** tab and select **Product attributes**.
1. Select a product attribute from the list pane. Then expand the **Value** FastTab and edit the value as needed for this attribute for this product.
1. Repeat the previous step until you have assigned all the attribute values needed for this product.

-->

## Set up and assign customer price attributes

You can create Pricing management pricing rules that consider attribute values assigned to the customer placing an order. You set up customer price attributes by creating an attribute group with the attributes you need and then setting that attribute group up as the customer attribute group. You can only have one customer attribute group, which applies to all customers. But each customer can have different values for each attribute.

### Set up customer price attributes

Follow these steps to set up your customer price attributes:

1. Go to **Product information management \> Setup \> Categories and attributes \> Attributes**. Set up all the customer price attributes you will need. Make sure that each of these attributes has **Can be used as price attribute** set to *Yes* (see also [Mark attributes as price attributes](#price-attributes)). Assign a **Default value** if needed.
1. Go to **Product information management \> Setup \> Categories and attributes \> Attribute groups**. Create your customer price attributes group. Give it an appropriate name (such as *Customer price attributes*) and add each relevant attribute to the **Attributes** FastTab.
1. Go to **Pricing management \> Setup \> Pricing management parameters** and open the **Price attribute** tab. Set **Customer attribute group** to the attribute group that you created to hold your customer price attributes.

### Assign customer price attribute values to customers

Customer price attributes will initially be assigned the **Default value** set up for the attribute. If you need to assign a specific value for a customer, follow these steps.

1. Go to **Sales and marketing \> Customers \> All customers**.
1. Select a customer in the grid.
1. On the Action Pane, open the **Price** tab and select **Customer attributes**.
1. Select a customer attribute from the list pane, expand the **Value** FastTab, and edit the value as needed for this attribute for this customer.
1. Repeat the previous step until you have assigned all the attribute values needed for this customers.

## Set up and assign sales order price attributes

You can create Pricing management pricing rules that consider attribute values assigned to each sales order. For example, you might set up sales order price attributes for *Campaign event*, *Order type*, and *Order channel*. You set up sales order price attributes by creating an attribute group with the attributes you need and then setting that attribute group up as the sales order attribute group. You can only have one sales order attribute group, which applies to all sales orders, but each sales order can have different values for each attribute.

### Set up sales order price attributes

Follow these steps to set up your sales order price attributes:

1. Go to **Product information management \> Setup \> Categories and attributes \> Attributes**. Set up all the sales order price attributes you will need. Make sure that each of these attributes has **Can be used as price attribute** set to *Yes* (see also [Mark attributes as price attributes](#price-attributes)). Assign a **Default value** if needed.
1. Go to **Product information management \> Setup \> Categories and attributes \> Attribute groups**. Create your sales order price attributes group. Give it an appropriate name (such as *Order price attributes*) and add each relevant attribute to the **Attributes** FastTab.
1. Go to **Pricing management \> Setup \> Pricing management parameters** and open the **Price attribute** tab. Set **Sales order attribute group** to the attribute group that you created to hold your sales order price attributes.

### Assign order attribute values to sales orders

Sales order price attributes will initially be assigned the **Default value** set up for the attribute. If you need to assign a specific value for an order, follow these steps.

1. Go to **Sales and marketing \> Orders \> All sales orders**.
1. Select an order in the grid or create a new one.
1. On the Action Pane, open the **Price** tab and select **Sales order attributes**.
1. Select a sales order price attribute from the list pane, expand the **Value** FastTab, and edit the value as needed for this attribute for this customer.
1. Repeat the previous step until you have assigned all the attribute values needed for this order.
